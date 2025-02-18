================================================
File: omni_pro_oms/apps.py
================================================
from django.apps import AppConfig


class OmsConfig(AppConfig):
    default_auto_field = "django.db.models.BigAutoField"
    name = "omni_pro_oms"

    def ready(self):
        import omni_pro_oms.models.signals

        return super().ready()


================================================
File: omni_pro_oms/er.dbml
================================================
// La tabla User representa a los usuarios del sistema.
Table User {
  id Int [primary key, note: 'Identificador único para cada usuario']
  password Varchar [note: 'Contraseña del usuario']
  last_login Timestamp [null, note: 'Fecha y hora del último inicio de sesión']
  is_superuser Bool [note: 'Indica si el usuario es un superusuario']
  username Varchar [unique, note: 'Nombre de usuario, único en el sistema']
  first_name Varchar [note: 'Nombre del usuario']
  last_name Varchar [note: 'Apellido del usuario']
  email Varchar [note: 'Correo electrónico del usuario']
  is_staff Bool [note: 'Indica si el usuario puede acceder al sitio de administración']
  is_active Bool [note: 'Indica si el usuario está activo']
  date_joined Timestamp [note: 'Fecha y hora en que el usuario se unió al sistema']
}

// La tabla Config almacena configuraciones para las plataformas OMS y Magento, incluyendo los detalles de autenticación.
Table Config {
  id Int [primary key, note: 'Identificador único de la configuración']
  base_url Varchar [note: 'Url base del core ']
  auth JSON
  token JSON
}


// La tabla Tenant representa a un inquilino o cliente del sistema.
Table Tenant {
  id Int [primary key, note: 'Identificador único del inquilino']
  name Varchar [note: 'Nombre del inquilino']
  description Varchar [note: 'Descripción del inquilino']
  code Varchar [note: 'Codigo del inquilino']
  cliend_id Varchar [note: '']
  cliend_secret Varchar [note: '']
}

// La tabla Operation almacena tareas asociadas a operaciones.
Table Operation {
  id Int [primary key, note: 'Identificador único de la operación']
  name Varchar [note: 'Nombre de la operación']
  dst Varchar [note: 'Indicador de quien es el destino la peticion ASAP o OMS']
  score Enum [note: 'low, higt, medium, Indica la urgencia de las task relacionadas a la operacion']
  endpoint_url Varchar [note: 'URL del endpoint de destino']
  http_method Varchar [note: 'Método HTTP a utilizar, como GET, POST, PUT, DELETE']
  timeout Int [note: 'Tiempo máximo en segundos para esperar la respuesta']
  auth_type Varchar [note: 'Tipo de autenticación, por ejemplo, None, Basic, Bearer, etc.']
  headers Text [note: 'Encabezados HTTP personalizados en formato JSON']
}

Table OperationType {
  id Int
  code Varchar
  name Varchar
}

Table TenantOperation {
  id Int [primary key, note: 'Identificador único de la relación']
  tenant_id Int [ref: > Tenant.id, note: 'ID del inquilino']
  operation_id Int [ref: > Operation.id, note: 'ID de la operación']
  operation_type_id Int [ref: > OperationType.id]
  config_id Int [ref: > Config.id]

  //unique tenant_id y operation_type_id
}


// La tabla OperationTask almacena tareas asociadas a operaciones.
Table Task {
  id Int [primary key, note: 'Identificador único de la tarea']
  tenant_id Int [ref: > Tenant.id, note: 'ID del Tenant asociada']
  operation_id Int [ref: > Operation.id, note: 'ID del Tenant asociada']
  status Enum [note: 'Estado actual de la tarea, waiting, error, success']
  body_src Varchar [note: 'Body de entrada para la tarea']
  headers_src Varchar [note: 'Cabeceras de entrada para la tarea']
  params_src Varchar [note: 'Parametros de entrada para la tarea']
  response_src Varchar [note: 'Respuesta recibida de la entrada']
  url_src Varchar [note: 'URL de entrada para la tarea, url endpoint igreso']
  body_dst Varchar [note: 'Body de salida de la tarea hacia el destino']
  headers_dst Varchar [note: 'Cabeceras de entrada para la tarea']
  params_dst Varchar [note: 'Parametros de entrada para la tarea']
  response_dst Varchar [note: 'Respuesta enviada a la salida']
  url_dst Varchar [note: 'URL de salida para la tarea']
  time Varchar [note: 'Tiempo asociado a lo que costo procesar tarea']
}


================================================
File: omni_pro_oms/permissions.py
================================================
import requests
from django.conf import settings
from rest_framework import permissions


class TokenValidScope(permissions.BasePermission):
    message = "Invalid or expired token."

    def has_permission(self, request, view):
        auth = request.headers.get("Authorization", None)
        if auth:
            token = auth.split(" ")[-1]
            url = settings.AUTH_BASE_URL + f"/auth/token/validate/?token={token}"
            headers = {"Authorization": f"Bearer {token}"}
            response = requests.get(url, headers=headers)
            return response.status_code == 200

        token = request.headers.get("token", None)
        if token:
            url = settings.AUTH_BASE_URL + "/auth/user/validate/"
            headers = {"Authorization": f"Token {token}"}
            response = requests.get(url, headers=headers)
            return response.status_code == 200

        return False


================================================
File: omni_pro_oms/tests.py
================================================
from django.test import TestCase

# Create your tests here.


================================================
File: omni_pro_oms/urls.py
================================================
from django.urls import include, path
from rest_framework import routers

from omni_pro_oms.views import config, operation, operation_type, task, tenant, tenant_operation

router = routers.DefaultRouter()

router.register(r"tenants", tenant.TenantViewSet)
router.register(r"operations", operation.OperationViewSet)
router.register(r"tasks", task.TaskViewSet)
router.register(r"configs", config.ConfigViewSet)
router.register(r"operation_types", operation_type.OperationTypeViewSet)
router.register(r"tenant_operations", tenant_operation.TenantOperationViewSet)

# Wire up our API using automatic URL routing.
# Additionally, we include login URLs for the browsable API.
urlpatterns = [
    path("", include(router.urls)),
]


================================================
File: omni_pro_oms/utils.py
================================================
from requests_oauthlib import OAuth1
import requests
from omni_pro_oms.models.tenant_operation import TenantOperation
from omni_pro_oms.models.task import Task
from omni_pro_oms.models.tenant import Tenant

import json


def call_request(tenant_operation: TenantOperation, **kwargs):
    headers = tenant_operation.operation_id.headers or {}
    config = tenant_operation.config_id
    operation = tenant_operation.operation_id
    method = kwargs.get("method") if kwargs.get("method", None) else operation.http_method
    endpoint_url = (
        kwargs.pop("endpoint_url")
        if kwargs.get("endpoint_url")
        else operation.endpoint_url
    )

    url = config.base_url + endpoint_url

    kwargs.update(
        {
            "method": method,
            "url": url,
            "headers": headers,
        }
    )
    auth_type = operation.auth_type
    if auth_type == "auth1":
        config.auth.get(auth_type, {}).get("consumer_key")
        oauth = OAuth1(
            config.auth.get(auth_type, {}).get("consumer_key"),
            config.auth.get(auth_type, {}).get("consumer_secret"),
            config.auth.get(auth_type, {}).get("access_token"),
            config.auth.get(auth_type, {}).get("token_secret"),
        )
        kwargs["auth"] = oauth

    elif auth_type == "bearer_token":
        headers["Authorization"] = config.auth.get(auth_type)

    elif auth_type == "token":
        headers["Token"] = config.auth.get(auth_type)

    return requests.request(**kwargs)


================================================
File: omni_pro_oms/admin/__init__.py
================================================
from . import config, operation, operation_type, task, task_result, tenant, tenant_operation


================================================
File: omni_pro_oms/admin/config.py
================================================
from django.contrib import admin
from django.utils.translation import gettext_lazy as _
from omni_pro_base.admin import BaseAdmin

from omni_pro_oms.forms import ConfigAdminForm
from omni_pro_oms.models import Config


class ConfigAdmin(BaseAdmin):
    list_display = ("base_url", "auth", "token")
    list_filter = ("base_url",)
    search_fields = ("base_url",)
    form = ConfigAdminForm

    def __init__(self, *args, **kwargs):
        super(ConfigAdmin, self).__init__(*args, **kwargs)
        self.fieldsets = (
            (_("Config"), {"fields": ("name", "base_url")}),
            (_("Auth"), {"fields": ("auth",)}),
            (_("Token"), {"fields": ("token",)}),
        ) + self.fieldsets


admin.site.register(Config, ConfigAdmin)


================================================
File: omni_pro_oms/admin/operation.py
================================================
from django.contrib import admin
from django.utils.translation import gettext_lazy as _
from omni_pro_base.admin import BaseAdmin
from omni_pro_oms.forms import OperationAdminForm
from omni_pro_oms.models import Operation


class OperationAdmin(BaseAdmin):
    list_display = ("name", "destination", "score", "endpoint_url", "timeout")
    list_filter = ("destination", "http_method")
    search_fields = ("name", "endpoint_url")
    form = OperationAdminForm

    def __init__(self, *args, **kwargs):
        super(OperationAdmin, self).__init__(*args, **kwargs)
        self.fieldsets = (
            (
                _("Required Information"),
                {
                    "fields": (
                        "name",
                        "destination",
                        "score",
                        "endpoint_url",
                        "http_method",
                        "timeout",
                        "auth_type",
                        "picking_state",
                    )
                },
            ),
            (
                _("Optional Information"),
                {"fields": ("headers",)},
            ),
            (
                _("Clean Task"),
                {"fields": ("success_clean_task_days", "other_clean_task_days", "packages_to_clean_count")},
            ),
            (
                _("Notifications"),
                {
                    "fields": (
                        "active_notifications",
                        "emails",
                        "status_notifications",
                    )
                },
            ),
        ) + self.fieldsets


admin.site.register(Operation, OperationAdmin)


================================================
File: omni_pro_oms/admin/operation_type.py
================================================
from django.contrib import admin
from django.utils.translation import gettext_lazy as _
from omni_pro_base.admin import BaseAdmin

from omni_pro_oms.forms import OperationTypeAdminForm
from omni_pro_oms.models import OperationType


class OperationTypeAdmin(BaseAdmin):
    list_display = ("name", "operation_code")
    search_fields = ("name", "operation_code")
    form = OperationTypeAdminForm

    def __init__(self, *args, **kwargs):
        super(OperationTypeAdmin, self).__init__(*args, **kwargs)
        self.fieldsets = ((_("Required Information"), {"fields": ("name", "operation_code")}),) + self.fieldsets


admin.site.register(OperationType, OperationTypeAdmin)


================================================
File: omni_pro_oms/admin/task.py
================================================
import django
from django.contrib import admin
from django.urls import resolve
from django.utils.translation import gettext_lazy as _
from import_export import resources
from import_export.admin import ImportExportModelAdmin
from omni_pro_base.admin import BaseAdmin
from omni_pro_oms.forms import TaskAdminForm
from omni_pro_oms.models import Task
from rangefilter.filters import DateRangeFilter
from rest_framework.request import Request
from rest_framework.test import APIRequestFactory


class TaskResource(resources.ModelResource):
    class Meta:
        model = Task
        fields = (
            "id",
            "item",
            "created_at",
            "tenant_id",
            "operation_id",
            "tenant_operation_id",
            "status",
            "url_src",
            "url_dst",
            "time",
            "updated_at",
            "celery_task_id",
        )
        export_order = fields


class BuilderDateRangeFilter(DateRangeFilter):
    def get_form(self, _request):
        form_class = self._get_form_class()
        if django.VERSION[:2] >= (5, 0):
            for name, value in self.used_parameters.items():
                if isinstance(value, list):
                    self.used_parameters[name] = value[-1]
        return form_class(self.used_parameters or None)


class TaskAdmin(ImportExportModelAdmin, BaseAdmin):
    resource_class = TaskResource

    list_display = (
        "id",
        "celery_task_id",
        "item",
        "created_at",
        "tenant_id",
        "operation_id",
        "tenant_operation_id",
        "status",
        "url_src",
        "url_dst",
        "time",
        "updated_at",
    )
    list_filter = (
        "tenant_id",
        "operation_id",
        "status",
        ("created_at", BuilderDateRangeFilter),
        "updated_at",
    )
    search_fields = ("item", "url_src", "url_dst", "body_src", "body_dst", "time")
    form = TaskAdminForm

    def __init__(self, *args, **kwargs):
        super(TaskAdmin, self).__init__(*args, **kwargs)
        self.fieldsets = (
            (
                _("Required Information"),
                {"fields": ("name", "tenant_id", "operation_id", "status", "time", "item", "celery_task_id")},
            ),
            (
                _("Source Info"),
                {
                    "fields": (
                        "body_src",
                        "headers_src",
                        "params_src",
                        "response_src",
                        "url_src",
                    )
                },
            ),
            (
                _("Destination Info"),
                {
                    "fields": (
                        "body_dst",
                        "headers_dst",
                        "params_dst",
                        "response_dst",
                        "url_dst",
                    )
                },
            ),
        ) + self.fieldsets

    def retry_task(self, request, queryset):
        try:
            for task in queryset:
                if task.status != "error":
                    continue
                task_view = resolve(task.url_src)
                view = task_view.func.view_class()
                factory = APIRequestFactory()

                # Crea la solicitud con el diccionario JSON y el método HTTP especificado
                method = task.operation_id.http_method.lower()
                request_rest = getattr(factory, method)(task.url_src, task.body_src, content_type="application/json")

                # Convertimos HttpRequest a una instancia de Request
                request_rest = Request(request_rest, parsers=[view.parser_classes[0]])
                request_rest._full_data = task.body_src

                # Llamamos al método dinámico de la vista
                view_method = getattr(view, method)
                view_method(request=request_rest, **task_view.kwargs)
                return self.message_user(request, "Task retried successfully.")
        except Exception as e:
            print(str(e))
            self.message_user(request, f"Error: {str(e)}", 40)

    actions = [retry_task]

    def save_model(self, request, obj, form, change):
        """
        Overrides the save_model method to set a custom attribute before saving the model.
        Args:
            request (HttpRequest): The current request object.
            obj (Model): The model instance being saved.
            form (ModelForm): The form instance used to create or update the model.
            change (bool): A flag indicating whether the model is being changed (True) or added (False).
        """

        if change:
            obj._admin_panel = True
        super().save_model(request, obj, form, change)


admin.site.register(Task, TaskAdmin)


================================================
File: omni_pro_oms/admin/task_result.py
================================================
import json

from django.contrib import admin
from django.db import models
from django.urls import reverse
from django.utils.html import format_html
from django_celery_results.admin import TaskResultAdmin
from django_celery_results.models import TaskResult
from omni_pro_base.admin import BaseAdmin

admin.site.unregister(TaskResult)


class CustomTaskResultAdmin(TaskResultAdmin):
    list_display = [
        "task_id",
        "periodic_task_name",
        "task_name",
        "date_done",
        "status",
        "worker",
        "oms_task",
    ]

    def oms_task(self, obj):
        try:
            if obj.task_args:
                task_args = obj.task_args.strip('"').strip()
                task_args = task_args.strip("()").split(",")

                task_id = task_args[0].strip() if len(task_args) > 0 else None
                if task_id and task_id.isdigit():
                    url = reverse("admin:omni_pro_oms_task_change", args=[int(task_id)])
                    return format_html('<a href="{}" target="_blank">Ver Task</a>', url)

            return "No disponible"
        except Exception as e:
            return format_html(f"<span style='color: red;'>Error: {e}</span>")

    oms_task.short_description = "OMS Task"


admin.site.register(TaskResult, CustomTaskResultAdmin)


================================================
File: omni_pro_oms/admin/tenant.py
================================================
from django.contrib import admin
from django.utils.translation import gettext_lazy as _
from omni_pro_base.admin import BaseAdmin
from omni_pro_oms.forms import TenantAdminForm
from omni_pro_oms.models import Tenant


class TenantAdmin(BaseAdmin):
    list_display = (
        "name",
        "description",
        "code",
        "client_id",
        "client_secret",
        "minutes_remaining",
        "token_expires_at",
    )
    search_fields = ("name", "code")
    form = TenantAdminForm

    def __init__(self, *args, **kwargs):
        super(TenantAdmin, self).__init__(*args, **kwargs)
        self.fieldsets = (
            (
                _("Required Information"),
                {
                    "fields": (
                        "name",
                        "description",
                        "code",
                        "client_id",
                        "client_secret",
                        "base_url",
                        "token",
                        "token_expires_at",
                        "minutes_remaining",
                    )
                },
            ),
        ) + self.fieldsets


admin.site.register(Tenant, TenantAdmin)


================================================
File: omni_pro_oms/admin/tenant_operation.py
================================================
from django.contrib import admin
from django.utils.translation import gettext_lazy as _
from omni_pro_base.admin import BaseAdmin

from omni_pro_oms.forms import TenantOperationAdminForm
from omni_pro_oms.models import TenantOperation


class TenantOperationAdmin(BaseAdmin):
    list_display = ("tenant_id", "operation_id", "operation_type_id", "config_id")
    list_filter = ("tenant_id", "operation_id", "operation_type_id", "config_id")
    search_fields = ("tenant_id", "operation_id", "operation_type_id", "config_id")
    form = TenantOperationAdminForm

    def __init__(self, *args, **kwargs):
        super(TenantOperationAdmin, self).__init__(*args, **kwargs)
        self.fieldsets = (
            (
                _("Tenant Operation"),
                {"fields": ("name", "tenant_id", "operation_id", "operation_type_id", "config_id")},
            ),
        ) + self.fieldsets


admin.site.register(TenantOperation, TenantOperationAdmin)


================================================
File: omni_pro_oms/core/__init__.py
================================================
from omni_pro_oms.core.api_client import ApiClient


================================================
File: omni_pro_oms/core/api_client.py
================================================
import json
from datetime import datetime, timedelta, timezone

import requests
from omni_pro_oms import utils
from omni_pro_oms.models import Operation, OperationType, Task, Tenant, TenantOperation

base_url = "https://integration-core-oms-v3.omni.pro"


class ApiClient:
    def __init__(self, tenant: Tenant, timeout=30) -> None:
        self.tenant: Tenant = tenant
        self.timeout = timeout
        self.token = self.get_auth_token()
        self._set_api_models()

    def _set_api_models(self):
        from omni_pro_oms.core.catalog.family import FamilyApi
        from omni_pro_oms.core.catalog.product import ProductApi
        from omni_pro_oms.core.catalog.product_integration import ProductIntegrationApi
        from omni_pro_oms.core.client.client import ClientApi
        from omni_pro_oms.core.rules.appointment import AppointmentApi
        from omni_pro_oms.core.rules.compute_method import ComputeMethodApi
        from omni_pro_oms.core.sale.order import OrderApi
        from omni_pro_oms.core.sale.order_line import OrderLineApi
        from omni_pro_oms.core.sale.sale import SaleApi
        from omni_pro_oms.core.sale.state import StateApi
        from omni_pro_oms.core.sale.tax import TaxApi
        from omni_pro_oms.core.stock.carrier_utils import CarrierSaveGuideApi
        from omni_pro_oms.core.stock.integration_operation import IntegrationOperationApi
        from omni_pro_oms.core.stock.integration_stock import StockIntegrationApi
        from omni_pro_oms.core.stock.picking import PickingApi
        from omni_pro_oms.core.stock.warehouse import WarehouseApi
        from omni_pro_oms.core.utilities.file_record import FileRecordApi

        self.order = OrderApi(self)
        self.picking = PickingApi(self)
        self.compute_method = ComputeMethodApi(self)
        self.sale = SaleApi(self)
        self.stock_integration = StockIntegrationApi(self)
        self.client = ClientApi(self)
        self.warehouse = WarehouseApi(self)
        self.appointment = AppointmentApi(self)
        self.carrier_utils = CarrierSaveGuideApi(self)
        self.state = StateApi(self)
        self.file_record = FileRecordApi(self)
        self.product = ProductApi(self)
        self.order_line = OrderLineApi(self)
        self.tax = TaxApi(self)
        self.family = FamilyApi(self)
        self.product_integration = ProductIntegrationApi(self)
        self.integration_operation = IntegrationOperationApi(self)

    def call_api(
        self, method: str, endpoint: str, raise_status: bool = True, response_is_json: bool = True, **kwargs
    ) -> dict:
        if not kwargs.get("timeout", None):
            kwargs.update({"timeout": self.timeout})
        headers = {"Accept": "application/json", "Authorization": self.token}
        url = f"{self.tenant.base_url}{endpoint}"
        response = requests.request(method, url, headers=headers, **kwargs)
        if raise_status:
            response.raise_for_status()
        if response_is_json:
            return response.json()
        return response

    def get_auth_token(self):
        if (
            self.tenant.token_expires_at
            and (self.tenant.token_expires_at - datetime.now(timezone.utc)).total_seconds() > 600
        ):
            return self.tenant.token

        url = f"{self.tenant.base_url}/api/v1/auth/token"

        payload = json.dumps(
            {
                "client_secret": self.tenant.client_secret,
                "client_id": self.tenant.client_id,
                "tenant": self.tenant.code,
            }
        )
        headers = {"Content-Type": "application/json"}
        response = requests.request("POST", url, headers=headers, data=payload)
        response.raise_for_status()
        token = response.json().get("authentication_result", {}).get("token")
        expires_in = response.json().get("authentication_result", {}).get("expires_in")

        if expires_in:
            self.tenant.token_expires_at = datetime.now(timezone.utc) + timedelta(seconds=expires_in)
            self.tenant.token = token
            self.tenant.save()

        return response.json().get("authentication_result", {}).get("token")


================================================
File: omni_pro_oms/core/decorators.py
================================================
from omni_pro_oms.models import Task


def task_flow_register(func):
    """
    Decorador diseñado para registrar el flujo de una tarea, manejar su éxito o fracaso,
    y en caso de fallo, lanzar una excepción. La función decorada debe retornar una tupla
    que contiene un objeto de respuesta (puede ser un diccionario vacío) y una tupla `_t`.
    La tupla `_t` debe contener un mensaje, un valor booleano indicando el éxito, y datos de la
    solicitud (`rq`) en ese orden.

    La ejecución exitosa o fallida de la función decorada determina si se lanza una excepción
    y cómo se registra el paso en el objeto de tarea asociado.

    Parameters:
        func (Callable): La función a decorar. Debe retornar una tupla con la forma (response, _t),
                         donde '_t' es otra tupla de la forma (message, success, rq).

    Returns:
        Callable: Una función wrapper que envuelve a `func`, gestionando la captura y registro de
                  su ejecución dentro del flujo de una tarea específica.

    Raises:
        Exception: Si `success` en la tupla `_t` retornada por `func` es False, se levanta una excepción
                   con el `message` contenido en `_t`.

    Example:
        @task_flow_register
        def mi_funcion_de_tarea(task, rq_data):
            # Lógica de la función...
            return {}, ("Operación exitosa", True, rq_data)

    Note:
        - Es crucial que la función decorada cumpla con la estructura de retorno esperada.
        - El primer argumento de la función decorada debe tener un atributo `task` desde el cual
          se puedan registrar los detalles de la ejecución del paso.
    """

    def wrapper(*args, **kwargs):
        response, _t = func(*args, **kwargs)
        response = response or {}
        task: Task = args[0].task
        message, success, rq = _t
        step = {
            "success": success,
            "step_name": func.__name__.replace("_", " ").strip().upper(),
            "func_name": func.__name__,
            "message": message,
            "request": rq,
            "response": response,
        }
        task.response_dst.get("steps").append(step)
        task.save()
        if not success:
            raise Exception(message)
        return response, _t

    return wrapper


================================================
File: omni_pro_oms/core/catalog/family.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_family = "/api/v1/catalog/family-attribute"


class FamilyApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def get_api(self, **kwargs):
        data = self.api_client.call_api(
            method="GET", endpoint=endpoint_family, **kwargs, raise_status=False, response_is_json=False
        )
        return data


================================================
File: omni_pro_oms/core/catalog/product.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_product = "/api/v1/catalog/product"


class ProductApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def get_api(self, **kwargs):
        data = self.api_client.call_api(method="GET", endpoint=endpoint_product, **kwargs)
        return data.get("products")


================================================
File: omni_pro_oms/core/catalog/product_integration.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_product_integration = "/api/v1/catalog/product/integration"


class ProductIntegrationApi:

    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def product_integration(self, **kwargs):
        data = self.api_client.call_api(method="POST", endpoint=endpoint_product_integration, **kwargs)
        success = False
        if data.get("response_standard", {}).get("status_code") == 200:
            success = True

        return success, data


================================================
File: omni_pro_oms/core/client/__init__.py
================================================
from omni_pro_oms.core.client.client import ClientApi


================================================
File: omni_pro_oms/core/client/client.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_client = "/api/v1/client"


class ClientApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def get_api(self, **kwargs):
        data = self.api_client.call_api(method="GET", endpoint=endpoint_client, **kwargs)
        return data.get("clients")


================================================
File: omni_pro_oms/core/rules/__init__.py
================================================
from omni_pro_oms.core.rules.compute_method import ComputeMethodApi
from omni_pro_oms.core.rules.appointment import AppointmentApi

================================================
File: omni_pro_oms/core/rules/appointment.py
================================================
from omni_pro_oms.core.api_client import ApiClient


class AppointmentApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def post_api(self, endpoint, **kwargs):
        response = self.api_client.call_api(
            method="POST",
            endpoint=endpoint,
            raise_status=False,
            response_is_json=False,
            **kwargs,
        )
        return response


================================================
File: omni_pro_oms/core/rules/compute_method.py
================================================
endpoint_compute = "/api/v1/rules/compute-method"
from omni_pro_oms.core.api_client import ApiClient


class ComputeMethodApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def post_api(self, **kwargs):
        data = self.api_client.call_api(
            method="POST", endpoint=endpoint_compute, **kwargs
        )
        return data.get("result")


================================================
File: omni_pro_oms/core/sale/__init__.py
================================================
from omni_pro_oms.core.sale.order import OrderApi
from omni_pro_oms.core.sale.sale import SaleApi
from omni_pro_oms.core.sale.state import StateApi
from omni_pro_oms.core.sale.order_line import OrderLineApi
from omni_pro_oms.core.sale.tax import TaxApi


================================================
File: omni_pro_oms/core/sale/order.py
================================================
endpoint_order = "/api/v1/sales/order"
from omni_pro_oms.core.api_client import ApiClient


class OrderApi:
    def __init__(self, api_client: ApiClient, raw_response=False):
        self.api_client = api_client
        self.raw_response = raw_response

    def get_api(self, **kwargs):
        try:
            data = self.api_client.call_api(method="GET", endpoint=endpoint_order, **kwargs)
            if self.raw_response:
                return data
            return data.get("orders")
        except Exception as e:
            raise Exception(f"Error getting orders: {e}")

    def put_api(self, **kwargs):
        try:
            data = self.api_client.call_api(method="PUT", endpoint=endpoint_order, **kwargs)
            if self.raw_response:
                return data
            return data.get("order")
        except Exception as e:
            raise Exception(f"Error putting orders: {e}")


================================================
File: omni_pro_oms/core/sale/order_line.py
================================================

from omni_pro_oms.core.api_client import ApiClient

endpoint_order_line = "/api/v1/sales/order_line"


class OrderLineApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def put_api(self, **kwargs):
        data = self.api_client.call_api(method="PUT", endpoint=endpoint_order_line, **kwargs)
        return data.get("order_line")


================================================
File: omni_pro_oms/core/sale/sale.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_sale = "/api/v1/sales/sale"


class SaleApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def get_api(self, endpoint, **kwargs):
        data = self.api_client.call_api(method="GET", endpoint=endpoint, **kwargs)
        return data.get("sale")

    def post_api(self, endpoint, raise_status=True, response_is_json=True, **kwargs):
        response = self.api_client.call_api(
            method="POST", endpoint=endpoint, raise_status=raise_status, response_is_json=response_is_json, **kwargs
        )
        return response

    def put_api(self, **kwargs):
        data = self.api_client.call_api(method="PUT", endpoint=endpoint_sale, **kwargs)
        return data.get("sale")


================================================
File: omni_pro_oms/core/sale/state.py
================================================
from omni_pro_oms.core.api_client import ApiClient
endpoint_state = "/api/v1/sales/state"

class StateApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def get_api(self, **kwargs):
        data = self.api_client.call_api(method="GET", endpoint=endpoint_state, **kwargs)
        return data.get("states")


================================================
File: omni_pro_oms/core/sale/tax.py
================================================

from omni_pro_oms.core.api_client import ApiClient

endpoint_tax = "/api/v1/sales/tax"


class TaxApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def get_api(self, **kwargs):
        data = self.api_client.call_api(method="GET", endpoint=endpoint_tax, **kwargs)
        return data.get("tax")


================================================
File: omni_pro_oms/core/stock/__init__.py
================================================
from omni_pro_oms.core.stock.picking import PickingApi
from omni_pro_oms.core.stock.integration_stock import StockIntegrationApi
from omni_pro_oms.core.stock.carrier_utils import CarrierSaveGuideApi


================================================
File: omni_pro_oms/core/stock/attachment.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_attachment= "/api/v1/stock/attachment"


class AttachmentSaveGuideApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def post_api(self, **kwargs):
        response = self.api_client.call_api(
            method="POST", endpoint=endpoint_attachment, **kwargs
        )
        return response


================================================
File: omni_pro_oms/core/stock/carrier_utils.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_save_guide = "/api/v1/stock/carrier/save/guide"


class CarrierSaveGuideApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def save_guide(self, **kwargs):
        data = self.api_client.call_api(method="POST", endpoint=endpoint_save_guide, **kwargs)
        return data.get("response_standard")


================================================
File: omni_pro_oms/core/stock/integration_operation.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_Integration_operation = "/api/v1/stock/picking/integration-operation"


class IntegrationOperationApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def put_api(self, **kwargs):
        data = self.api_client.call_api(method="PUT", endpoint=endpoint_Integration_operation, **kwargs)
        return data.get("response_standard")


================================================
File: omni_pro_oms/core/stock/integration_stock.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_get_quants = "/api/v1/stock/search/quant/integration"
endpoint_set_quants = "/api/v1/stock/quant/integration"


class StockIntegrationApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def get_search_stock(self, **kwargs):
        response = self.api_client.call_api(
            method="POST", endpoint=endpoint_get_quants, **kwargs
        )
        data = {
            "message": response.get("response_standard", {}).get("message", "")
        }
        success = False

        if response.get("response_standard", {}).get("status_code") == 200:
            success = True
            data.update({
                "quants": response.get("quants", {}),
                "locations": response.get("locations", {}),
                "products": response.get("products", {})
            })

        return success, data

    def set_process_stock(self, **kwargs):
        data = self.api_client.call_api(
            method="POST", endpoint=endpoint_set_quants, **kwargs
        )
        success = False
        message = data.get("response_standard", {}).get("message", "")
        if data.get("response_standard", {}).get("status_code") == 200:
            success = True

        return success, message


================================================
File: omni_pro_oms/core/stock/picking.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_picking = "/api/v1/stock/picking"


class PickingApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def get_api(self, **kwargs):
        data = self.api_client.call_api(
            method="GET", endpoint=endpoint_picking, **kwargs
        )
        return data.get("pickings")


================================================
File: omni_pro_oms/core/stock/warehouse.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_warehouse = "/api/v1/stock/warehouse"


class WarehouseApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def get_api(self, **kwargs):
        data = self.api_client.call_api(
            method="GET", endpoint=endpoint_warehouse, **kwargs
        )
        return data.get("warehouses")


================================================
File: omni_pro_oms/core/utilities/file_record.py
================================================
from omni_pro_oms.core.api_client import ApiClient

endpoint_file_record = "/api/v1/utilities/file_record"

class FileRecordApi:
    def __init__(self, api_client: ApiClient):
        self.api_client = api_client

    def post_api(self, **kwargs):
        response = self.api_client.call_api(
            method="POST", endpoint=endpoint_file_record, **kwargs
        )
        return response


================================================
File: omni_pro_oms/forms/__init__.py
================================================
from .config import ConfigAdminForm
from .operation import OperationAdminForm
from .operation_type import OperationTypeAdminForm
from .task import TaskAdminForm
from .tenant import TenantAdminForm
from .tenant_operation import TenantOperationAdminForm


================================================
File: omni_pro_oms/forms/config.py
================================================
from django import forms
from django_json_widget.widgets import JSONEditorWidget

from omni_pro_oms.models import Config


class ConfigAdminForm(forms.ModelForm):
    class Meta:
        model = Config
        fields = "__all__"
        widgets = {
            "auth": JSONEditorWidget,
            "token": JSONEditorWidget,
        }


================================================
File: omni_pro_oms/forms/operation.py
================================================
from django import forms
from django.contrib.postgres.forms import SimpleArrayField
from django_json_widget.widgets import JSONEditorWidget
from omni_pro_oms.models import Operation


class OperationAdminForm(forms.ModelForm):
    emails = SimpleArrayField(forms.EmailField(), required=False, widget=forms.Textarea(attrs={"rows": 4, "cols": 20}))

    class Meta:
        model = Operation
        fields = "__all__"
        widgets = {
            "headers": JSONEditorWidget,
        }

    def clean_emails(self):
        emails = self.cleaned_data.get("emails", [])
        # Validate if emails are unique
        if len(emails) != len(set(emails)):
            raise forms.ValidationError("Duplicate emails are not allowed.")
        return emails


================================================
File: omni_pro_oms/forms/operation_type.py
================================================
from django import forms

from omni_pro_oms.models import OperationType


class OperationTypeAdminForm(forms.ModelForm):
    class Meta:
        model = OperationType
        fields = "__all__"


================================================
File: omni_pro_oms/forms/task.py
================================================
from django import forms
from django_json_widget.widgets import JSONEditorWidget

from omni_pro_oms.models import Task


class TaskAdminForm(forms.ModelForm):
    class Meta:
        model = Task
        fields = "__all__"
        widgets = {
            "body_src": JSONEditorWidget,
            "headers_src": JSONEditorWidget,
            "params_src": JSONEditorWidget,
            "response_src": JSONEditorWidget,
            "body_dst": JSONEditorWidget,
            "headers_dst": JSONEditorWidget,
            "params_dst": JSONEditorWidget,
            "response_dst": JSONEditorWidget,
        }


================================================
File: omni_pro_oms/forms/tenant.py
================================================
from django import forms
from omni_pro_oms.models import Tenant


class TenantAdminForm(forms.ModelForm):
    minutes_remaining = forms.CharField(
        label="Minutes Remaining", required=False, widget=forms.TextInput(attrs={"disabled": "disabled"})
    )
    token = forms.CharField(label="Token", required=False, widget=forms.Textarea(attrs={"disabled": "disabled"}))

    class Meta:
        model = Tenant
        fields = "__all__"

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        if self.instance:
            self.fields["minutes_remaining"].initial = self.instance.minutes_remaining


================================================
File: omni_pro_oms/forms/tenant_operation.py
================================================
from django import forms

from omni_pro_oms.models import TenantOperation


class TenantOperationAdminForm(forms.ModelForm):
    class Meta:
        model = TenantOperation
        fields = "__all__"


================================================
File: omni_pro_oms/migrations/0001_initial.py
================================================
# Generated by Django 5.0 on 2024-05-21 23:34

import django.db.models.deletion
import omni_pro_oms.models.config
from django.conf import settings
from django.db import migrations, models


class Migration(migrations.Migration):
    initial = True

    dependencies = [
        migrations.swappable_dependency(settings.AUTH_USER_MODEL),
    ]

    operations = [
        migrations.CreateModel(
            name="Config",
            fields=[
                (
                    "id",
                    models.BigAutoField(
                        auto_created=True,
                        primary_key=True,
                        serialize=False,
                        verbose_name="ID",
                    ),
                ),
                (
                    "created_at",
                    models.DateTimeField(
                        auto_now_add=True,
                        help_text="Date time on which the object was created",
                        verbose_name="created at",
                    ),
                ),
                (
                    "updated_at",
                    models.DateTimeField(
                        auto_now=True,
                        help_text="Date time on which the object was last modified",
                        verbose_name="updated by",
                    ),
                ),
                (
                    "is_active",
                    models.BooleanField(
                        default=True,
                        help_text="Designates whether this user should be treated as active. Unselect this instead of deleting accounts.",
                        verbose_name="is active",
                    ),
                ),
                ("name", models.CharField(max_length=255, verbose_name="Name")),
                ("base_url", models.CharField(max_length=255, verbose_name="Base URL")),
                (
                    "auth",
                    models.JSONField(
                        blank=True,
                        default=omni_pro_oms.models.config.get_default_auth,
                        null=True,
                        verbose_name="Auth",
                    ),
                ),
                (
                    "token",
                    models.JSONField(blank=True, null=True, verbose_name="Token"),
                ),
                (
                    "created_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_created_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="created by",
                    ),
                ),
                (
                    "updated_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_updated_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="updated by",
                    ),
                ),
            ],
            options={
                "verbose_name": "Configuration",
                "verbose_name_plural": "Configurations",
            },
        ),
        migrations.CreateModel(
            name="Operation",
            fields=[
                (
                    "id",
                    models.BigAutoField(
                        auto_created=True,
                        primary_key=True,
                        serialize=False,
                        verbose_name="ID",
                    ),
                ),
                (
                    "created_at",
                    models.DateTimeField(
                        auto_now_add=True,
                        help_text="Date time on which the object was created",
                        verbose_name="created at",
                    ),
                ),
                (
                    "updated_at",
                    models.DateTimeField(
                        auto_now=True,
                        help_text="Date time on which the object was last modified",
                        verbose_name="updated by",
                    ),
                ),
                (
                    "is_active",
                    models.BooleanField(
                        default=True,
                        help_text="Designates whether this user should be treated as active. Unselect this instead of deleting accounts.",
                        verbose_name="is active",
                    ),
                ),
                ("name", models.CharField(max_length=255, verbose_name="Name")),
                (
                    "destination",
                    models.CharField(max_length=255, verbose_name="Destination"),
                ),
                (
                    "score",
                    models.CharField(
                        choices=[
                            ("low", "Low"),
                            ("medium", "Medium"),
                            ("high", "High"),
                            ("critical", "Critical"),
                        ],
                        help_text="Level of priority",
                        max_length=255,
                        verbose_name="Score",
                    ),
                ),
                (
                    "endpoint_url",
                    models.CharField(max_length=255, verbose_name="Endpoint URL"),
                ),
                (
                    "http_method",
                    models.CharField(
                        choices=[
                            ("GET", "GET"),
                            ("POST", "POST"),
                            ("PUT", "PUT"),
                            ("DELETE", "DELETE"),
                            ("PATCH", "PATCH"),
                            ("OPTIONS", "OPTIONS"),
                            ("HEAD", "HEAD"),
                            ("CONNECT", "CONNECT"),
                            ("TRACE", "TRACE"),
                        ],
                        max_length=255,
                        null=True,
                        verbose_name="HTTP Method",
                    ),
                ),
                (
                    "timeout",
                    models.IntegerField(help_text="In seconds", verbose_name="Timeout"),
                ),
                (
                    "auth_type",
                    models.CharField(
                        choices=[
                            ("token", "Token"),
                            ("bearer_token", "Bearer Token"),
                            ("api_key", "Api Key"),
                            ("auth2", "Auth2"),
                            ("auth1", "Auth1"),
                            ("custom", "Custom"),
                        ],
                        max_length=255,
                        verbose_name="Auth Type",
                    ),
                ),
                (
                    "headers",
                    models.JSONField(blank=True, null=True, verbose_name="Headers"),
                ),
                (
                    "created_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_created_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="created by",
                    ),
                ),
                (
                    "updated_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_updated_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="updated by",
                    ),
                ),
            ],
            options={
                "verbose_name": "Operation",
                "verbose_name_plural": "Operations",
            },
        ),
        migrations.CreateModel(
            name="OperationType",
            fields=[
                (
                    "id",
                    models.BigAutoField(
                        auto_created=True,
                        primary_key=True,
                        serialize=False,
                        verbose_name="ID",
                    ),
                ),
                (
                    "created_at",
                    models.DateTimeField(
                        auto_now_add=True,
                        help_text="Date time on which the object was created",
                        verbose_name="created at",
                    ),
                ),
                (
                    "updated_at",
                    models.DateTimeField(
                        auto_now=True,
                        help_text="Date time on which the object was last modified",
                        verbose_name="updated by",
                    ),
                ),
                (
                    "is_active",
                    models.BooleanField(
                        default=True,
                        help_text="Designates whether this user should be treated as active. Unselect this instead of deleting accounts.",
                        verbose_name="is active",
                    ),
                ),
                ("name", models.CharField(max_length=255, verbose_name="Name")),
                (
                    "operation_code",
                    models.CharField(
                        default="default", max_length=255, verbose_name="Operation Code"
                    ),
                ),
                (
                    "created_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_created_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="created by",
                    ),
                ),
                (
                    "updated_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_updated_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="updated by",
                    ),
                ),
            ],
            options={
                "verbose_name": "Operation Type",
                "verbose_name_plural": "Operation Types",
            },
        ),
        migrations.CreateModel(
            name="Tenant",
            fields=[
                (
                    "id",
                    models.BigAutoField(
                        auto_created=True,
                        primary_key=True,
                        serialize=False,
                        verbose_name="ID",
                    ),
                ),
                (
                    "created_at",
                    models.DateTimeField(
                        auto_now_add=True,
                        help_text="Date time on which the object was created",
                        verbose_name="created at",
                    ),
                ),
                (
                    "updated_at",
                    models.DateTimeField(
                        auto_now=True,
                        help_text="Date time on which the object was last modified",
                        verbose_name="updated by",
                    ),
                ),
                (
                    "is_active",
                    models.BooleanField(
                        default=True,
                        help_text="Designates whether this user should be treated as active. Unselect this instead of deleting accounts.",
                        verbose_name="is active",
                    ),
                ),
                ("name", models.CharField(max_length=255, verbose_name="Name")),
                (
                    "description",
                    models.CharField(max_length=255, verbose_name="Description"),
                ),
                (
                    "code",
                    models.CharField(max_length=255, unique=True, verbose_name="Code"),
                ),
                (
                    "client_id",
                    models.CharField(max_length=255, verbose_name="Client ID"),
                ),
                (
                    "client_secret",
                    models.CharField(max_length=255, verbose_name="Client Secret"),
                ),
                ("base_url", models.CharField(max_length=255, verbose_name="Base URL")),
                (
                    "created_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_created_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="created by",
                    ),
                ),
                (
                    "updated_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_updated_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="updated by",
                    ),
                ),
            ],
            options={
                "verbose_name": "Tenant",
                "verbose_name_plural": "Tenants",
            },
        ),
        migrations.CreateModel(
            name="TenantOperation",
            fields=[
                (
                    "id",
                    models.BigAutoField(
                        auto_created=True,
                        primary_key=True,
                        serialize=False,
                        verbose_name="ID",
                    ),
                ),
                (
                    "created_at",
                    models.DateTimeField(
                        auto_now_add=True,
                        help_text="Date time on which the object was created",
                        verbose_name="created at",
                    ),
                ),
                (
                    "updated_at",
                    models.DateTimeField(
                        auto_now=True,
                        help_text="Date time on which the object was last modified",
                        verbose_name="updated by",
                    ),
                ),
                (
                    "is_active",
                    models.BooleanField(
                        default=True,
                        help_text="Designates whether this user should be treated as active. Unselect this instead of deleting accounts.",
                        verbose_name="is active",
                    ),
                ),
                (
                    "name",
                    models.CharField(
                        blank=True, max_length=255, null=True, verbose_name="Name"
                    ),
                ),
                (
                    "config_id",
                    models.ForeignKey(
                        on_delete=django.db.models.deletion.CASCADE,
                        related_name="config_tenant_operations",
                        to="omni_pro_oms.config",
                        verbose_name="Config ID",
                    ),
                ),
                (
                    "created_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_created_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="created by",
                    ),
                ),
                (
                    "operation_id",
                    models.ForeignKey(
                        on_delete=django.db.models.deletion.CASCADE,
                        related_name="operation_tenant_operations",
                        to="omni_pro_oms.operation",
                        verbose_name="Operation ID",
                    ),
                ),
                (
                    "operation_type_id",
                    models.ForeignKey(
                        on_delete=django.db.models.deletion.CASCADE,
                        related_name="operation_type_tenant_operations",
                        to="omni_pro_oms.operationtype",
                        verbose_name="Operation Type ID",
                    ),
                ),
                (
                    "tenant_id",
                    models.ForeignKey(
                        on_delete=django.db.models.deletion.CASCADE,
                        related_name="tenant_operations",
                        to="omni_pro_oms.tenant",
                        verbose_name="Tenant ID",
                    ),
                ),
                (
                    "updated_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_updated_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="updated by",
                    ),
                ),
            ],
            options={
                "verbose_name": "Tenant Operation",
                "verbose_name_plural": "Tenant Operations",
            },
        ),
        migrations.CreateModel(
            name="Task",
            fields=[
                (
                    "id",
                    models.BigAutoField(
                        auto_created=True,
                        primary_key=True,
                        serialize=False,
                        verbose_name="ID",
                    ),
                ),
                (
                    "created_at",
                    models.DateTimeField(
                        auto_now_add=True,
                        help_text="Date time on which the object was created",
                        verbose_name="created at",
                    ),
                ),
                (
                    "updated_at",
                    models.DateTimeField(
                        auto_now=True,
                        help_text="Date time on which the object was last modified",
                        verbose_name="updated by",
                    ),
                ),
                (
                    "is_active",
                    models.BooleanField(
                        default=True,
                        help_text="Designates whether this user should be treated as active. Unselect this instead of deleting accounts.",
                        verbose_name="is active",
                    ),
                ),
                ("name", models.CharField(max_length=256, verbose_name="Name")),
                (
                    "status",
                    models.CharField(
                        choices=[
                            ("waiting", "Waiting"),
                            ("error", "Error"),
                            ("success", "Success"),
                            ("partial_success", "Partial Success"),
                        ],
                        default="waiting",
                        max_length=256,
                        verbose_name="Status",
                    ),
                ),
                (
                    "body_src",
                    models.JSONField(blank=True, null=True, verbose_name="Body Source"),
                ),
                (
                    "headers_src",
                    models.JSONField(
                        blank=True, null=True, verbose_name="Headers Source"
                    ),
                ),
                (
                    "params_src",
                    models.JSONField(
                        blank=True, null=True, verbose_name="Params Source"
                    ),
                ),
                (
                    "response_src",
                    models.JSONField(
                        blank=True, null=True, verbose_name="Response Source"
                    ),
                ),
                (
                    "url_src",
                    models.CharField(
                        blank=True, max_length=256, null=True, verbose_name="URL Source"
                    ),
                ),
                (
                    "body_dst",
                    models.JSONField(
                        blank=True, null=True, verbose_name="Body Destination"
                    ),
                ),
                (
                    "headers_dst",
                    models.JSONField(
                        blank=True, null=True, verbose_name="Headers Destination"
                    ),
                ),
                (
                    "params_dst",
                    models.JSONField(
                        blank=True, null=True, verbose_name="Params Destination"
                    ),
                ),
                (
                    "response_dst",
                    models.JSONField(
                        blank=True, null=True, verbose_name="Response Destination"
                    ),
                ),
                (
                    "url_dst",
                    models.CharField(
                        blank=True,
                        max_length=256,
                        null=True,
                        verbose_name="URL Destination",
                    ),
                ),
                (
                    "time",
                    models.IntegerField(
                        blank=True,
                        help_text="In milliseconds",
                        null=True,
                        verbose_name="Time",
                    ),
                ),
                (
                    "created_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_created_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="created by",
                    ),
                ),
                (
                    "operation_id",
                    models.ForeignKey(
                        on_delete=django.db.models.deletion.CASCADE,
                        related_name="tasks",
                        to="omni_pro_oms.operation",
                        verbose_name="Operation",
                    ),
                ),
                (
                    "updated_by",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.SET_NULL,
                        related_name="%(app_label)s_%(class)s_updated_by",
                        to=settings.AUTH_USER_MODEL,
                        verbose_name="updated by",
                    ),
                ),
                (
                    "tenant_id",
                    models.ForeignKey(
                        on_delete=django.db.models.deletion.CASCADE,
                        related_name="tasks",
                        to="omni_pro_oms.tenant",
                        verbose_name="Tenant",
                    ),
                ),
                (
                    "tenant_operation_id",
                    models.ForeignKey(
                        null=True,
                        on_delete=django.db.models.deletion.CASCADE,
                        related_name="tasks",
                        to="omni_pro_oms.tenantoperation",
                        verbose_name="TenantOperation",
                    ),
                ),
            ],
            options={
                "verbose_name": "Task",
                "verbose_name_plural": "Tasks",
            },
        ),
        migrations.AddConstraint(
            model_name="tenantoperation",
            constraint=models.UniqueConstraint(
                fields=("tenant_id", "operation_type_id"),
                name="unique_tenant_operation_type",
            ),
        ),
    ]


================================================
File: omni_pro_oms/migrations/0002_task_item_tenant_token_tenant_token_expires_at.py
================================================
# Generated by Django 5.0 on 2024-06-04 16:22

from django.db import migrations, models


class Migration(migrations.Migration):

    dependencies = [
        ('omni_pro_oms', '0001_initial'),
    ]

    operations = [
        migrations.AddField(
            model_name='task',
            name='item',
            field=models.CharField(blank=True, max_length=256, null=True, verbose_name='Item'),
        ),
        migrations.AddField(
            model_name='tenant',
            name='token',
            field=models.CharField(blank=True, max_length=255, null=True, verbose_name='Token'),
        ),
        migrations.AddField(
            model_name='tenant',
            name='token_expires_at',
            field=models.DateTimeField(blank=True, null=True, verbose_name='Token Expires At'),
        ),
    ]


================================================
File: omni_pro_oms/migrations/0003_alter_tenant_token.py
================================================
# Generated by Django 5.0 on 2024-06-05 19:22

from django.db import migrations, models


class Migration(migrations.Migration):

    dependencies = [
        ('omni_pro_oms', '0002_task_item_tenant_token_tenant_token_expires_at'),
    ]

    operations = [
        migrations.AlterField(
            model_name='tenant',
            name='token',
            field=models.TextField(blank=True, null=True, verbose_name='Token'),
        ),
    ]


================================================
File: omni_pro_oms/migrations/0004_operation_other_clean_task_days_and_more.py
================================================
# Generated by Django 5.0 on 2024-06-18 15:36

from django.db import migrations, models


class Migration(migrations.Migration):
    dependencies = [
        ("omni_pro_oms", "0003_alter_tenant_token"),
    ]

    operations = [
        migrations.AddField(
            model_name="operation",
            name="other_clean_task_days",
            field=models.IntegerField(
                blank=True,
                help_text="In days",
                null=True,
                verbose_name="Other Clean Task Days",
            ),
        ),
        migrations.AddField(
            model_name="operation",
            name="packages_to_clean_count",
            field=models.IntegerField(
                blank=True,
                help_text="Number of packages to clean",
                null=True,
                verbose_name="Packages To Clean Count",
            ),
        ),
        migrations.AddField(
            model_name="operation",
            name="success_clean_task_days",
            field=models.IntegerField(
                blank=True,
                help_text="In days",
                null=True,
                verbose_name="Success Clean Task Days",
            ),
        ),
    ]


================================================
File: omni_pro_oms/migrations/0005_operation_picking_state.py
================================================
# Generated by Django 5.0 on 2024-12-03 21:39

from django.db import migrations, models


class Migration(migrations.Migration):
    dependencies = [
        ("omni_pro_oms", "0004_operation_other_clean_task_days_and_more"),
    ]

    operations = [
        migrations.AddField(
            model_name="operation",
            name="picking_state",
            field=models.BooleanField(
                default=False,
                help_text="If the operation is in picking state",
                verbose_name="Picking State",
            ),
        ),
    ]


================================================
File: omni_pro_oms/migrations/0005_task_celery_task_id.py
================================================
# Generated by Django 5.0 on 2024-12-19 15:24

from django.db import migrations, models


class Migration(migrations.Migration):
    dependencies = [
        ("omni_pro_oms", "0004_operation_other_clean_task_days_and_more"),
    ]

    operations = [
        migrations.AddField(
            model_name="task",
            name="celery_task_id",
            field=models.CharField(
                blank=True, max_length=256, null=True, verbose_name="Celery Task ID"
            ),
        ),
    ]


================================================
File: omni_pro_oms/models/__init__.py
================================================
from .tenant import Tenant
from .operation import Operation
from .operation_type import OperationType
from .config import Config
from .task import Task
from .tenant_operation import TenantOperation


================================================
File: omni_pro_oms/models/config.py
================================================
from auditlog.models import AuditlogHistoryField
from auditlog.registry import auditlog
from django.db import models
from django.utils.translation import gettext_lazy as _
from omni_pro_base.models import OmniModel


def get_default_auth():
    """
    Generate value for default authentication field
    """
    return {
        "token": "123",
        "bearer_token": "Bearer your_token",
        "api_key": "qwerr",
        "auth2": {
            "client_id": "qweqr",
            "client_secret": "poiklo",
            "token_url": "https://auth-url.com",
            "grant_type": "client_credentials",
            "scope": "",
        },
        "auth1": {
            "consumer_key": "8w8rt9agjaf2iyc63jpeysoj9p5zd6li",
            "consumer_secret": "mh5riskd5pdf1uod95hrfx1807fejako",
            "access_token": "gjaf2iyc63jpeysoj9p5zd6li",
            "token_secret": "8w8rt9agjaf2iyc63jpeysoj9p5zd6li",
        },
        "custom": {
            "key": "value",
        },
    }


class Config(OmniModel):
    name = models.CharField(max_length=255, verbose_name=_("Name"))
    base_url = models.CharField(max_length=255, verbose_name=_("Base URL"))
    auth = models.JSONField(
        verbose_name=_("Auth"), blank=True, null=True, default=get_default_auth
    )
    token = models.JSONField(verbose_name=_("Token"), blank=True, null=True)

    history = AuditlogHistoryField()

    def __str__(self):
        return self.name

    class Meta:
        verbose_name = _("Configuration")
        verbose_name_plural = _("Configurations")


auditlog.register(Config)


================================================
File: omni_pro_oms/models/operation.py
================================================
from auditlog.models import AuditlogHistoryField
from auditlog.registry import auditlog
from django.contrib.postgres.fields import ArrayField
from django.db import models
from django.utils.translation import gettext_lazy as _
from omni_pro_base.models import OmniModel

STATUS_CHOICES = (
    ("waiting", "Waiting"),
    ("error", "Error"),
    ("success", "Success"),
    ("partial_success", "Partial Success"),
)


class Operation(OmniModel):

    class HttpMethod(models.TextChoices):
        GET = "GET", _("GET")
        POST = "POST", _("POST")
        PUT = "PUT", _("PUT")
        DELETE = "DELETE", _("DELETE")
        PATCH = "PATCH", _("PATCH")
        OPTIONS = "OPTIONS", _("OPTIONS")
        HEAD = "HEAD", _("HEAD")
        CONNECT = "CONNECT", _("CONNECT")
        TRACE = "TRACE", _("TRACE")

    class Score(models.TextChoices):
        LOW = "low", _("Low")
        MEDIUM = "medium", _("Medium")
        HIGH = "high", _("High")
        CRITICAL = "critical", _("Critical")

    class AuthType(models.TextChoices):
        TOKEN = ("token",)
        BEARER_TOKEN = ("bearer_token",)
        API_KEY = ("api_key",)
        AUTH2 = ("auth2",)
        AUTH1 = "auth1"
        CUSTOM = "custom"

    name = models.CharField(max_length=255, verbose_name=_("Name"))
    destination = models.CharField(max_length=255, verbose_name=_("Destination"))
    score = models.CharField(
        choices=Score.choices, max_length=255, verbose_name=_("Score"), help_text=_("Level of priority")
    )
    endpoint_url = models.CharField(max_length=255, verbose_name=_("Endpoint URL"))
    http_method = models.CharField(choices=HttpMethod.choices, max_length=255, verbose_name=_("HTTP Method"), null=True)
    timeout = models.IntegerField(verbose_name=_("Timeout"), help_text=_("In seconds"))
    auth_type = models.CharField(choices=AuthType.choices, max_length=255, verbose_name=_("Auth Type"))
    headers = models.JSONField(verbose_name=_("Headers"), blank=True, null=True)
    success_clean_task_days = models.IntegerField(
        verbose_name=_("Success Clean Task Days"), help_text=_("In days"), null=True, blank=True
    )
    other_clean_task_days = models.IntegerField(
        verbose_name=_("Other Clean Task Days"), help_text=_("In days"), null=True, blank=True
    )
    packages_to_clean_count = models.IntegerField(
        verbose_name=_("Packages To Clean Count"), help_text=_("Number of packages to clean"), null=True, blank=True
    )
    active_notifications = models.BooleanField(verbose_name=_("Active Notifications"), default=False)
    emails = ArrayField(models.EmailField(), blank=True, default=list, verbose_name=_("Emails"))
    status_notifications = models.CharField(
        choices=STATUS_CHOICES,
        max_length=256,
        default="error",
        verbose_name=_("Status Notifications"),
    )
    picking_state = models.BooleanField(
        verbose_name=_("Picking State"), help_text=_("If the operation is in picking state"), default=False
    )

    history = AuditlogHistoryField()

    def __str__(self):
        return self.name

    class Meta:
        verbose_name = _("Operation")
        verbose_name_plural = _("Operations")


auditlog.register(Operation)


================================================
File: omni_pro_oms/models/operation_type.py
================================================
from auditlog.models import AuditlogHistoryField
from auditlog.registry import auditlog
from django.db import models
from django.utils.translation import gettext_lazy as _
from omni_pro_base.models import OmniModel


class OperationType(OmniModel):
    name = models.CharField(max_length=255, verbose_name=_("Name"))
    operation_code = models.CharField(max_length=255, verbose_name=_("Operation Code"),
                                      default='default')

    history = AuditlogHistoryField()

    def __str__(self):
        return self.name

    class Meta:
        verbose_name = _("Operation Type")
        verbose_name_plural = _("Operation Types")


auditlog.register(OperationType)


================================================
File: omni_pro_oms/models/signals.py
================================================
from django.conf import settings
from django.core.mail import send_mail
from django.db.models.signals import post_save, pre_save
from django.dispatch import receiver
from omni_pro_oms.models import Task


@receiver(pre_save, sender=Task)
def set_old_status(sender, instance, **kwargs):
    """
    Signal handler to set the old status of a Task instance before it is saved.
    This function is intended to be connected to the pre-save signal of the Task model.
    It checks if the instance being saved already exists in the database (i.e., it has a primary key).
    If it does, it retrieves the current status of the instance from the database and stores it in the
    instance's _old_status attribute. If the instance is new (i.e., it does not have a primary key yet),
    it sets the _old_status attribute to None.
    Args:
        sender (Model): The model class that sent the signal.
        instance (Model instance): The instance of the model that is being saved.
        **kwargs: Additional keyword arguments.
    """

    if instance.pk:
        old = Task.objects.filter(pk=instance.pk).values("status").first()
        if old:
            instance._old_status = old["status"]  # Save the previous status
        else:
            instance._old_status = None
    else:
        instance._old_status = None


@receiver(post_save, sender=Task)
def send_email_on_error_status(sender, instance, created, **kwargs):
    """
    Sends an email notification when the status of an instance changes to a specific value.
    This function is intended to be used as a Django signal handler for the post_save signal.
    It sends an email notification only when the instance is updated (not created) and the status
    changes to a specific value defined in the related operation_id.
    Args:
        sender (Model): The model class that sent the signal.
        instance (Model instance): The actual instance being saved.
        created (bool): A boolean indicating whether a new record was created.
        **kwargs: Additional keyword arguments.
    Conditions for sending an email:
        - The instance is not newly created.
        - The old status is different from the new status.
        - The new status matches the status_notifications of the related operation_id.
        - The related operation_id has active notifications.
        - The related operation_id has specified email addresses.
        - The update is not performed from the admin panel.
    Email content:
        - Subject: Status change notification with the task name and ID.
        - Message: Details about the task and its new status.
        - Recipients: Email addresses specified in the related operation_id.
    """

    # We avoid emails during creation, only for updates
    if not created:
        old_status = getattr(instance, "_old_status", None)
        new_status = instance.status
        admin_panel = getattr(instance, "_admin_panel", False)

        if (
            old_status != instance.operation_id.status_notifications
            and new_status == instance.operation_id.status_notifications
            and instance.operation_id.active_notifications
            and instance.operation_id.emails
            and not admin_panel
        ):
            status: str = instance.operation_id.status_notifications
            asunto = f"{status.capitalize()} en tarea {instance.name} con ID {instance.pk}"
            mensaje = f"La tarea {instance.name} con ID {instance.pk} ha pasado a estado de {status}."
            destinatarios = instance.operation_id.emails

            send_mail(asunto, mensaje, settings.DEFAULT_FROM_EMAIL, destinatarios, fail_silently=False)


================================================
File: omni_pro_oms/models/task.py
================================================
from auditlog.models import AuditlogHistoryField
from auditlog.registry import auditlog
from django.db import models
from django.utils.translation import gettext_lazy as _
from omni_pro_base.models import OmniModel

from .operation import Operation
from .tenant import Tenant
from .tenant_operation import TenantOperation

STATUS_CHOICES = (
    ("waiting", "Waiting"),
    ("error", "Error"),
    ("success", "Success"),
    ("partial_success", "Partial Success"),
)


class Task(OmniModel):
    name = models.CharField(max_length=256, verbose_name=_("Name"))
    tenant_id = models.ForeignKey(Tenant, on_delete=models.CASCADE, verbose_name=_("Tenant"), related_name="tasks")
    operation_id = models.ForeignKey(
        Operation,
        on_delete=models.CASCADE,
        verbose_name=_("Operation"),
        related_name="tasks",
    )
    tenant_operation_id = models.ForeignKey(
        TenantOperation,
        on_delete=models.CASCADE,
        verbose_name=_("TenantOperation"),
        related_name="tasks",
        null=True,
    )
    status = models.CharField(
        choices=STATUS_CHOICES,
        max_length=256,
        default="waiting",
        verbose_name=_("Status"),
    )
    body_src = models.JSONField(verbose_name=_("Body Source"), blank=True, null=True)
    headers_src = models.JSONField(verbose_name=_("Headers Source"), blank=True, null=True)
    params_src = models.JSONField(verbose_name=_("Params Source"), blank=True, null=True)
    response_src = models.JSONField(verbose_name=_("Response Source"), blank=True, null=True)
    url_src = models.CharField(max_length=256, verbose_name=_("URL Source"), blank=True, null=True)
    body_dst = models.JSONField(verbose_name=_("Body Destination"), blank=True, null=True)
    headers_dst = models.JSONField(verbose_name=_("Headers Destination"), blank=True, null=True)
    params_dst = models.JSONField(verbose_name=_("Params Destination"), blank=True, null=True)
    response_dst = models.JSONField(verbose_name=_("Response Destination"), blank=True, null=True)
    url_dst = models.CharField(max_length=256, verbose_name=_("URL Destination"), blank=True, null=True)
    time = models.IntegerField(verbose_name=_("Time"), help_text=_("In milliseconds"), blank=True, null=True)
    item = models.CharField(_("Item"), max_length=256, blank=True, null=True)
    celery_task_id = models.CharField(max_length=256, verbose_name=_("Celery Task ID"), blank=True, null=True)

    history = AuditlogHistoryField()

    def __str__(self):
        return self.name

    class Meta:
        verbose_name = _("Task")
        verbose_name_plural = _("Tasks")


auditlog.register(Task)


================================================
File: omni_pro_oms/models/tenant.py
================================================
from datetime import datetime, timezone

from auditlog.models import AuditlogHistoryField
from auditlog.registry import auditlog
from django.db import models
from django.utils.translation import gettext_lazy as _
from omni_pro_base.models import OmniModel


class Tenant(OmniModel):
    name = models.CharField(max_length=255, verbose_name=_("Name"))
    description = models.CharField(max_length=255, verbose_name=_("Description"))
    code = models.CharField(max_length=255, verbose_name=_("Code"), unique=True)
    client_id = models.CharField(max_length=255, verbose_name=_("Client ID"))
    client_secret = models.CharField(max_length=255, verbose_name=_("Client Secret"))
    base_url = models.CharField(max_length=255, verbose_name=_("Base URL"))
    token = models.TextField(verbose_name=_("Token"), blank=True, null=True)
    token_expires_at = models.DateTimeField(verbose_name=_("Token Expires At"), blank=True, null=True)

    history = AuditlogHistoryField()

    @property
    def minutes_remaining(self):
        if self.token_expires_at:
            remaining_time = self.token_expires_at - datetime.now(timezone.utc)
            return remaining_time.total_seconds() // 60

    def __str__(self):
        return self.name

    class Meta:
        verbose_name = _("Tenant")
        verbose_name_plural = _("Tenants")


auditlog.register(Tenant)


================================================
File: omni_pro_oms/models/tenant_operation.py
================================================
import requests
from auditlog.models import AuditlogHistoryField
from auditlog.registry import auditlog
from django.db import models
from django.utils import timezone
from django.utils.translation import gettext_lazy as _
from omni_pro_base.models import OmniModel

from .config import Config
from .operation import Operation
from .operation_type import OperationType
from .tenant import Tenant


class TenantOperation(OmniModel):
    name = models.CharField(max_length=255, verbose_name=_("Name"), null=True, blank=True)
    tenant_id = models.ForeignKey(
        Tenant, on_delete=models.CASCADE, verbose_name=_("Tenant ID"), related_name="tenant_operations"
    )
    operation_id = models.ForeignKey(
        Operation, on_delete=models.CASCADE, verbose_name=_("Operation ID"), related_name="operation_tenant_operations"
    )
    operation_type_id = models.ForeignKey(
        OperationType,
        on_delete=models.CASCADE,
        verbose_name=_("Operation Type ID"),
        related_name="operation_type_tenant_operations",
    )
    config_id = models.ForeignKey(
        Config, on_delete=models.CASCADE, verbose_name=_("Config ID"), related_name="config_tenant_operations"
    )

    history = AuditlogHistoryField()

    def __str__(self):
        return f"{self.tenant_id.name} - {self.operation_type_id.name}"

    def get_oms_token(self):
        try:
            config = self.config_id

            if not config.token.get("token") or config.token.get("expired") <= timezone.now():
                token_response = requests.post(
                    config.base_url + config.auth.get("token_url"),
                    json={
                        "client_id": self.tenant_id.client_id,
                        "client_secret": self.tenant_id.client_secret,
                        "tenant": self.tenant_id.code,
                    },
                )
                if token_response.status_code != 200:
                    raise Exception(f"Token request failed with status code {token_response.status_code}")
                token_response_data = token_response.json()

                config.token["token"] = token_response_data["authentication_result"]["token"]
                config.token["expired"] == timezone.now() + timezone.timedelta(
                    seconds=token_response_data["authentication_result"]["expires_in"]
                )
                config.save()

            return config.token

        except Tenant.DoesNotExist:
            print(f"Tenant with code {self.code} does not exist.")
            raise Exception(f"Tenant with code {self.code} does not exist.")

    class Meta:
        constraints = [
            models.UniqueConstraint(fields=["tenant_id", "operation_type_id"], name="unique_tenant_operation_type")
        ]
        verbose_name = _("Tenant Operation")
        verbose_name_plural = _("Tenant Operations")
        # ordering = ['created_at']


auditlog.register(TenantOperation)


================================================
File: omni_pro_oms/operations/__init__.py
================================================
from .tenant_operation import TenantOperationOperation


================================================
File: omni_pro_oms/operations/task.py
================================================
from omni_pro_oms.models import Operation, OperationType, Task, Tenant, TenantOperation
from rest_framework.request import Request


class TaskOperation:

    @classmethod
    def create_task_from_request(cls, request: Request, tenant_operation: TenantOperation):
        tasks = []

        if isinstance(request, Request):
            if isinstance(request.data, list):
                data_list = request.data
            else:
                return cls._create_single_task(request, tenant_operation, request.data)

        elif request is None:
            return cls._create_single_task(request, tenant_operation, None)

        elif isinstance(request, dict) and isinstance(request.get("data"), list):
            data_list = request.get("data")

        for data_item in data_list:
            task = cls._create_single_task(request, tenant_operation, data_item)
            tasks.append(task)

        return tasks

    @staticmethod
    def _create_single_task(request: Request, tenant_operation: TenantOperation, data_item) -> Task:
        name = f"{tenant_operation.operation_type_id.name} {tenant_operation.tenant_id.name}"

        task = Task.objects.create(
            name=name,
            tenant_id=tenant_operation.tenant_id,
            operation_id=tenant_operation.operation_id,
            tenant_operation_id=tenant_operation,
            status="waiting",
            body_src=data_item,
            headers_src=dict(request.headers) if request else {},
            params_src=request.query_params if request else {},
            response_src={"success": True, "message": None},
            url_src=request.path if request and request.path else "",
            body_dst="",
            headers_dst="",
            params_dst="",
            response_dst="",
            url_dst="",
            time=0,
        )
        return task


================================================
File: omni_pro_oms/operations/tenant_operation.py
================================================
from omni_pro_oms.models import Operation, OperationType, Tenant, TenantOperation, task


class TenantOperationOperation:
    @classmethod
    def get_tenant_operation(
        cls, tenant_code: str, operation_type_code: str
    ) -> TenantOperation:
        tenant_operation = TenantOperation.objects.get(
            tenant_id__code=tenant_code, operation_type_id__operation_code=operation_type_code
        )
        return tenant_operation


================================================
File: omni_pro_oms/serializers/__init__.py
================================================
from .config import ConfigSerializer
from .operation import OperationSerializer
from .operation_type import OperationTypeSerializer
from .task import TaskSerializer
from .tenant import TenantSerializer
from .tenant_operation import TenantOperationSerializer


================================================
File: omni_pro_oms/serializers/config.py
================================================
from rest_framework import serializers

from omni_pro_oms.models import Config


class ConfigSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = Config
        fields = "__all__"


================================================
File: omni_pro_oms/serializers/operation.py
================================================
from rest_framework import serializers

from omni_pro_oms.models import Operation


class OperationSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = Operation
        fields = "__all__"


================================================
File: omni_pro_oms/serializers/operation_type.py
================================================
from rest_framework import serializers

from omni_pro_oms.models import OperationType


class OperationTypeSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = OperationType
        fields = "__all__"


================================================
File: omni_pro_oms/serializers/task.py
================================================
from rest_framework import serializers

from omni_pro_oms.models import Task


class TaskSerializer(serializers.ModelSerializer):
    class Meta:
        model = Task
        fields = "__all__"


================================================
File: omni_pro_oms/serializers/tenant.py
================================================
from rest_framework import serializers

from omni_pro_oms.models import Tenant


class TenantSerializer(serializers.ModelSerializer):
    class Meta:
        model = Tenant
        fields = "__all__"


================================================
File: omni_pro_oms/serializers/tenant_operation.py
================================================
from rest_framework import serializers

from omni_pro_oms.models import TenantOperation


class TenantOperationSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = TenantOperation
        fields = "__all__"


================================================
File: omni_pro_oms/task/__init__.py
================================================
from omni_pro_oms.task.delete_tasks import DeleteTasks
from omni_pro_oms.task.task_api import TaskApi


================================================
File: omni_pro_oms/task/delete_tasks.py
================================================
from enum import Enum

from celery import current_task, shared_task
from django.conf import settings
from django.db import connection, connections, transaction
from django.utils import timezone
from omni_pro_oms.models import Operation, Task


class DeleteTasks:
    @staticmethod
    @shared_task(
        max_retries=settings.CELERY_MAX_RETRIES,
        default_retry_delay=settings.CELERY_SECONDS_TIME_TO_RETRY,
        queue=settings.CELERY_NAME_QUEUE,
    )
    def task_delete_tasks():
        try:
            return DeleteTasks().task_info()
        except Exception as exc:
            print(f"Tarea fallida: {exc}")
            raise current_task.retry(exc=exc, countdown=settings.CELERY_SECONDS_TIME_TO_RETRY)

    @transaction.atomic
    def task_info(self):
        operations = Operation.objects.filter(
            success_clean_task_days__isnull=False,
            other_clean_task_days__isnull=False,
            packages_to_clean_count__isnull=False,
        )
        for operation in operations:
            success_tasks_oms = self._fetch_tasks("omni_pro_oms_task", "success", operation.success_clean_task_days)
            success_tasks_celery = self._fetch_tasks(
                "django_celery_results_taskresult",
                "SUCCESS",
                operation.success_clean_task_days,
                date_field="date_created",
            )
            other_tasks_oms = self._fetch_tasks(
                "omni_pro_oms_task", ["error", "waiting", "partial_success"], operation.other_clean_task_days
            )
            other_tasks_celery = self._fetch_tasks(
                "django_celery_results_taskresult",
                ["FAILURE", "PENDING", "RETRY"],
                operation.other_clean_task_days,
                date_field="date_created",
            )
            limit = operation.packages_to_clean_count
            (
                limited_success_tasks_oms,
                limited_other_tasks_oms,
                limited_success_tasks_celery,
                limited_other_tasks_celery,
            ) = self._package_task(
                operation, success_tasks_oms, success_tasks_celery, other_tasks_oms, other_tasks_celery, limit
            )
        return self.delete_task(
            limited_success_tasks_oms,
            limited_other_tasks_oms,
            limited_success_tasks_celery,
            limited_other_tasks_celery,
        )

    def _fetch_tasks(self, table_name, status, days_to_keep, date_field="created_at"):
        cutoff_date = timezone.now() - timezone.timedelta(days=days_to_keep)
        status_condition = f"status = '{status}'" if isinstance(status, str) else f"status IN {tuple(status)}"

        query = f"""
            SELECT *
            FROM {table_name}
            WHERE {status_condition}
            AND {date_field} <= %s
        """

        try:
            with connection.cursor() as cursor:
                cursor.execute(query, [cutoff_date])
                return cursor.fetchall()
        except Exception as e:
            print(f"Error fetching tasks from {table_name}: {e}")
            return []

    def _package_task(
        self, operation, success_tasks_oms, success_tasks_celery, other_tasks_oms, other_tasks_celery, limit_delete
    ):
        try:
            with connection.cursor() as cursor:
                limited_success_tasks_oms = self._apply_limit(
                    cursor, "omni_pro_oms_task", success_tasks_oms, limit_delete
                )
                limited_other_tasks_oms = self._apply_limit(cursor, "omni_pro_oms_task", other_tasks_oms, limit_delete)
                limited_success_tasks_celery = self._apply_limit(
                    cursor, "django_celery_results_taskresult", success_tasks_celery, limit_delete
                )
                limited_other_tasks_celery = self._apply_limit(
                    cursor, "django_celery_results_taskresult", other_tasks_celery, limit_delete
                )

            return (
                limited_success_tasks_oms,
                limited_other_tasks_oms,
                limited_success_tasks_celery,
                limited_other_tasks_celery,
            )
        except Exception as e:
            print(f"Error packaging tasks: {e}")
            return [], [], [], []

    def _apply_limit(self, cursor, table_name, tasks, limit):
        task_ids = tuple(task[0] for task in tasks)
        if not task_ids:
            return []

        if table_name == "omni_pro_oms_task":
            query = f"""
                SELECT *
                FROM {table_name}
                WHERE id IN %s
                ORDER BY created_at ASC
                LIMIT %s
            """

        else:
            query = f"""
                SELECT *
                FROM {table_name}
                WHERE id IN %s
                ORDER BY date_created ASC
                LIMIT %s
            """

        cursor.execute(query, [task_ids, limit])
        return cursor.fetchall()

    def delete_task(
        self,
        limited_success_tasks_oms,
        limited_other_tasks_oms,
        limited_success_tasks_celery,
        limited_other_tasks_celery,
    ):
        try:
            with transaction.atomic():
                with connection.cursor() as cursor:
                    self._delete_tasks(cursor, "omni_pro_oms_task", limited_success_tasks_oms)
                    self._delete_tasks(cursor, "omni_pro_oms_task", limited_other_tasks_oms)
                    self._delete_tasks(cursor, "django_celery_results_taskresult", limited_success_tasks_celery)
                    self._delete_tasks(cursor, "django_celery_results_taskresult", limited_other_tasks_celery)
                transaction.set_rollback(False)
                print("Transaction committed successfully.")
        except Exception as e:
            print(f"Error deleting tasks: {e}")

    def _delete_tasks(self, cursor, table_name, tasks):
        task_ids = tuple(task[0] for task in tasks)
        if not task_ids:
            print(f"No tasks to delete in {table_name}")
            return

        query = f"""
            DELETE FROM {table_name}
            WHERE id IN %s
        """

        try:
            print(f"Executing delete query: {query} with task_ids: {task_ids}")
            cursor.execute(query, [task_ids])
            print(f"Deleted tasks with IDs {task_ids} from {table_name}")
        except Exception as e:
            print(f"Error executing delete query for {table_name}: {e}")


================================================
File: omni_pro_oms/task/task_api.py
================================================
import json
import time

from django.core.exceptions import ObjectDoesNotExist
from omni_pro_oms import utils
from omni_pro_oms.core.api_client import ApiClient
from omni_pro_oms.models import Task
from requests import Response


class TaskApi(ApiClient):

    def __init__(self, task_id: int, celery_task_id: str = None, timeout=30) -> None:
        # self.task: Task = self._get_task(task_id)
        self.task: Task = TaskApi.get_task_with_retry(task_id)
        if celery_task_id:
            self._update_celery_task_id(celery_task_id)
            
        super().__init__(tenant=self.task.tenant_id, timeout=timeout)

    def _get_task(self, task_id: int):
        return Task.objects.get(id=task_id)

    @classmethod
    def get_task_with_retry(cls, task_id, max_retries=5, initial_delay=2):
        """Intenta obtener la tarea con reintentos y retraso progresivo."""
        for attempt in range(1, max_retries + 1):
            try:
                task = Task.objects.get(id=task_id)
                return task
            except Task.DoesNotExist:
                # calculo del retraso
                retry_delay = initial_delay + attempt
                if attempt < max_retries:
                    print(
                        f"Tarea {task_id} no encontrada. Reintentando en {retry_delay} segundos (intento {attempt}/{max_retries})..."
                    )
                    time.sleep(retry_delay)
                else:
                    print(f"Tarea {task_id} no encontrada después de {max_retries} intentos.")
                    raise ObjectDoesNotExist(f"Tarea {task_id} no encontrada después de {max_retries} intentos.")

    def call_request(self, update_task: bool = False, **kwargs) -> Response:
        if not kwargs.get("timeout"):
            kwargs["timeout"] = self.task.operation_id.timeout
        response: Response = utils.call_request(self.task.tenant_operation_id, **kwargs)
        if update_task:
            self.task_update_from_response(response)
        return response

    def task_update_from_response(self, response: Response, item: str = None):
        body_dest = json.loads(response.request.body.decode("utf-8"))
        response_dst = json.loads(response.content.decode("utf-8"))
        headers_dst = response.request.headers._store
        url_dst = response.request.url
        time_request = response.elapsed.total_seconds() * 1000

        self.task.url_dst = url_dst
        self.task.headers_dst = headers_dst
        self.task.body_dst = body_dest
        self.task.response_dst = response_dst
        self.task.time = time_request
        self.task.status = self.get_task_status_from_request_status_code([response.status_code])
        self.task.item = item
        self.task.save()

    def _update_celery_task_id(self, celery_task_id: str) -> None:
        """Actualiza el ID de la tarea de Celery en el modelo Task."""
        self.task.celery_task_id = celery_task_id
        self.task.save()

    def get_task_status_from_request_status_code(self, status_codes):
        successful = all(status >= 200 and status < 300 for status in status_codes)
        unsuccessful = all(status >= 400 for status in status_codes)

        if self.task.operation_id.picking_state:
            self.update_status_picking_operation(status_codes)

        if successful and not unsuccessful:
            return "success"
        elif unsuccessful and not successful:
            return "error"
        else:
            return "partial_success"

    def update_status_picking_operation(self, status_code):
        picking = self.task.body_src
        if picking.get("picking_integration_operations", []):
            payload = {
                "picking_id": int(picking.get("id")),
                "code": self.task.operation_id.name,
                "status": "SUCCESS" if status_code == 200 else "ERROR",
                "message": (
                    f"{self.task.operation_id.name} enviado correctamente" if status_code == 200 else "Error al enviar"
                ),
            }
            self.integration_operation.put_api(json=payload)


================================================
File: omni_pro_oms/views/__init__.py
================================================



================================================
File: omni_pro_oms/views/base.py
================================================
from omni_pro_oms.permissions import TokenValidScope
from rest_framework import permissions, views


class OMNIAPIView(views.APIView):
    permission_classes = [TokenValidScope]


class InternalBaseView(views.APIView):
    permission_classes = [permissions.AllowAny]


================================================
File: omni_pro_oms/views/config.py
================================================
from oauth2_provider.contrib.rest_framework import TokenHasReadWriteScope
from rest_framework import viewsets

from omni_pro_oms.models import Config
from omni_pro_oms.serializers import ConfigSerializer


class ConfigViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows configs to be viewed or edited.
    """

    queryset = Config.objects.all()
    serializer_class = ConfigSerializer
    permission_classes = [TokenHasReadWriteScope]


================================================
File: omni_pro_oms/views/operation.py
================================================
from oauth2_provider.contrib.rest_framework import TokenHasReadWriteScope
from rest_framework import viewsets

from omni_pro_oms.models import Operation
from omni_pro_oms.serializers import OperationSerializer


class OperationViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows configs to be viewed or edited.
    """

    queryset = Operation.objects.all()
    serializer_class = OperationSerializer
    permission_classes = [TokenHasReadWriteScope]


================================================
File: omni_pro_oms/views/operation_type.py
================================================
from oauth2_provider.contrib.rest_framework import TokenHasReadWriteScope
from rest_framework import viewsets

from omni_pro_oms.models import OperationType
from omni_pro_oms.serializers import OperationTypeSerializer


class OperationTypeViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows configs to be viewed or edited.
    """

    queryset = OperationType.objects.all()
    serializer_class = OperationTypeSerializer
    permission_classes = [TokenHasReadWriteScope]


================================================
File: omni_pro_oms/views/task.py
================================================
from oauth2_provider.contrib.rest_framework import TokenHasReadWriteScope
from rest_framework import viewsets

from omni_pro_oms.models import Task
from omni_pro_oms.serializers import TaskSerializer


class TaskViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows configs to be viewed or edited.
    """

    queryset = Task.objects.all()
    serializer_class = TaskSerializer
    permission_classes = [TokenHasReadWriteScope]


================================================
File: omni_pro_oms/views/tenant.py
================================================
from oauth2_provider.contrib.rest_framework import TokenHasReadWriteScope
from rest_framework import viewsets

from omni_pro_oms.models import Tenant
from omni_pro_oms.serializers import TenantSerializer


class TenantViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows configs to be viewed or edited.
    """

    queryset = Tenant.objects.all()
    serializer_class = TenantSerializer
    permission_classes = [TokenHasReadWriteScope]


================================================
File: omni_pro_oms/views/tenant_operation.py
================================================
from oauth2_provider.contrib.rest_framework import TokenHasReadWriteScope
from rest_framework import viewsets

from omni_pro_oms.models import TenantOperation
from omni_pro_oms.serializers import TenantOperationSerializer


class TenantOperationViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows configs to be viewed or edited.
    """

    queryset = TenantOperation.objects.all()
    serializer_class = TenantOperationSerializer
    permission_classes = [TokenHasReadWriteScope]


