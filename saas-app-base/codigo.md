Directory structure:
└── omnipro-solutions-saas-app-base/
    ├── README.md
    ├── LICENSE
    ├── MANIFEST.in
    ├── make_migrations.py
    ├── requirements.txt
    ├── setup.py
    └── omni_pro_base/
        ├── __init__.py
        ├── apps.py
        ├── backends.py
        ├── http_request.py
        ├── urls.py
        ├── util.py
        ├── admin/
        │   ├── __init__.py
        │   ├── auth.py
        │   ├── base_admin.py
        │   └── users.py
        ├── forms/
        │   ├── __init__.py
        │   └── users.py
        ├── migrations/
        │   ├── 0001_initial.py
        │   └── __init__.py
        ├── models/
        │   ├── __init__.py
        │   ├── base_model.py
        │   └── users.py
        ├── serializers/
        │   ├── __init__.py
        │   └── users.py
        ├── settings/
        │   ├── __init__.py
        │   ├── base.py
        │   ├── local.py
        │   └── production.py
        ├── static/
        │   └── vendor/
        │       └── omni/
        │           ├── css/
        │           │   └── main.css
        │           ├── img/
        │           └── js/
        │               └── main.js
        ├── tests/
        │   └── __init__.py
        └── views/
            ├── __init__.py
            └── users.py

# LIBRERIA UTILIZADA DENTRO DE LOS PROYECTOS DE OMS Y SUS MICROSERVICIOS
## nombre repo: saas-app-oms, link: (https://github.com/Omnipro-Solutions/saas-app-base)
================================================
File: README.md
================================================
# saas-app-base
Librería del modulo base para app de conexión a OMS

================================================
File: LICENSE
================================================
Copyright (c) 2023, OMNI.PRO

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

================================================
File: MANIFEST.in
================================================
recursive-include omni_pro_base/static *

================================================
File: make_migrations.py
================================================
import os
import sys

from django.conf import settings
from django.core.management import call_command

# Configuración básica de Django. Ajusta según sea necesario.
BASE_DIR = os.path.dirname(os.path.abspath(__file__))

BASE_APPS = [
    "jazzmin",
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
]

THIRD_PARTY_APPS = [
    "oauth2_provider",
    "rest_framework",
    "allow_cidr",
    "health_check",
]

LOCAL_APPS = [
    "omni_pro_base",
]

INSTALLED_APPS = BASE_APPS + THIRD_PARTY_APPS + LOCAL_APPS

settings.configure(
    DEBUG=True,
    DATABASES={
        "default": {
            "ENGINE": "django.db.backends.sqlite3",
            "NAME": os.path.join(BASE_DIR, "db.sqlite3"),
        }
    },
    INSTALLED_APPS=INSTALLED_APPS,
    SECRET_KEY="django-insecure-_xm%ar7&b@9n84@bkgiy@m#cl_lhqdgpg*p(+l#ie%8dzw#51+",
    MIDDLEWARE=(
        "allow_cidr.middleware.AllowCIDRMiddleware",
        "django.middleware.security.SecurityMiddleware",
        "django.contrib.sessions.middleware.SessionMiddleware",
        "django.middleware.common.CommonMiddleware",
        "django.middleware.csrf.CsrfViewMiddleware",
        "django.contrib.auth.middleware.AuthenticationMiddleware",
        "django.contrib.messages.middleware.MessageMiddleware",
        "django.middleware.clickjacking.XFrameOptionsMiddleware",
    ),
)

if __name__ == "__main__":
    # Asegúrate de que Django esté configurado para tu proyecto.
    os.environ.setdefault("DJANGO_SETTINGS_MODULE", "omni_pro_base.mig_settings")
    try:
        # Inicializa las configuraciones de Django
        import django

        django.setup()

        # Genera las migraciones para tu aplicación
        call_command("makemigrations", "omni_pro_base")

    except Exception as e:
        print(f"Error al generar migraciones: {e}")
        sys.exit(1)


================================================
File: requirements.txt
================================================
setuptools==65.5.1
Django==5.0
environs==9.5.0
django-jazzmin==2.6.0
djangorestframework==3.14.0
django-oauth-toolkit==2.3.0 # Tokenización endpoints, vistas
django-allow-cidr==0.7.1
django-health-check==3.18.1
dj-database-url==2.1.0
django-celery-results==2.5.1
psycopg2-binary==2.9.9
whitenoise==6.6.0
argon2-cffi==23.1.0
celery==5.3.6
redis==5.0.1
django-jazzmin-admin-rangefilter==1.0.0
newrelic==9.10.0
django-import-export==4.1.0
django-db-connection-pool==1.2.5

================================================
File: setup.py
================================================
from pathlib import Path

from setuptools import find_packages, setup

# The directory containing this file
HERE = Path(__file__).parent

# The text of the README file
README = (HERE / "README.md").read_text()
DESCRIPTION = "Python library designed to be a apps for OMS Django apps."
VERSION = "0.0.0"
PACKAGE_NAME = "omni-pro-app-base"
AUTHOR = "OMNI.PRO"
AUTHOR_EMAIL = "development@omni.pro"
URL = "https://github.com/Omnipro-Solutions/saas-app-base"
INSTALL_REQUIRES = [
    "Django==5.0",
    "environs==9.5.0",
    "django-jazzmin==3.0.0",
    "djangorestframework==3.14.0",
    "django-oauth-toolkit==2.3.0",
    "django-auditlog==2.3.0",
    "django-allow-cidr==0.7.1",
    "django-health-check==3.18.1",
    "django-celery-results==2.5.1",
    "django-json-widget==2.0.1",
    "requests==2.31.0",
    "requests-oauthlib==2.0.0",
    "dj-database-url==2.1.0",
    "psycopg2-binary==2.9.9",
    "whitenoise==6.6.0",
    "argon2-cffi==23.1.0",
    "celery==5.3.6",
    "redis==5.0.1",
    "django-jazzmin-admin-rangefilter==1.0.0",
    "newrelic==9.10.0",
    "django-celery-beat==2.6.0",
    "django-import-export==4.1.0",
    "django-db-connection-pool==1.2.5",
]
# with open(HERE / "requirements.txt") as f:
#     INSTALL_REQUIRES = f.read().splitlines()

# This call to setup() does all the work
setup(
    name=PACKAGE_NAME,
    version=VERSION,
    description=DESCRIPTION,
    long_description=README,
    long_description_content_type="text/markdown",
    url=URL,
    author=AUTHOR,
    author_email=AUTHOR_EMAIL,
    license="MIT",
    packages=find_packages(exclude=("tests",)),
    package_data={"": ["*.pyi", "data/*.csv"]},
    include_package_data=True,
    install_requires=INSTALL_REQUIRES,
    classifiers=[
        "Development Status :: 3 - Alpha",
        "Intended Audience :: Developers",
        "License :: OSI Approved :: MIT License",
        "Programming Language :: Python :: 3.11",
    ],
    extras_require={
        "dev": [
            "pytest",
        ]
    },
    test_suite="tests",
    python_requires=">=3.11",
)


================================================
File: omni_pro_base/apps.py
================================================
from django.apps import AppConfig


class BaseConfig(AppConfig):
    default_auto_field = "django.db.models.BigAutoField"
    name = "omni_pro_base"


================================================
File: omni_pro_base/backends.py
================================================
import requests
from django.conf import settings
from django.contrib.auth.backends import BaseBackend
from django.contrib.auth.hashers import check_password
from omni_pro_base.models.users import User


class SettingsBackend(BaseBackend):
    """
    Authenticate against the settings ADMIN_LOGIN and ADMIN_PASSWORD.

    Use the login name and a hash of the password. For example:

    ADMIN_LOGIN = 'admin'
    ADMIN_PASSWORD = 'pbkdf2_sha256$30000$Vo0VlMnkR4Bk$qEvtdyZRWTcOsCnI/oQ7fVOu1XAURIZYoOZ3iq8Dr4M='
    """

    def authenticate(self, request, username=None, password=None):
        login_valid = settings.ADMIN_LOGIN == username
        pwd_valid = check_password(password, settings.ADMIN_PASSWORD)
        if login_valid and pwd_valid:
            try:
                user = User.objects.get(email=username)
            except User.DoesNotExist:
                # Create a new user. There's no need to set a password
                # because only the password from settings.py is checked.
                user = User(username=settings.ADMIN_USERNAME)
                user.email = settings.ADMIN_LOGIN
                user.first_name = settings.ADMIN_FIRST_NAME
                user.last_name = settings.ADMIN_LAST_NAME
                user.is_staff = True
                user.is_superuser = True
                user.save()
            return user
        return None

    def get_user(self, user_id):
        try:
            return User.objects.get(pk=user_id)
        except User.DoesNotExist:
            return None


class AppUserBackend(BaseBackend):

    def authenticate(self, request, username=None, password=None):
        try:
            response = requests.post(
                settings.AUTH_APP_SERVICE_URL,
                json={"email": username, "password": password},
            )
            response.raise_for_status()
            response_data = response.json()
            user = User.objects.get(email=username)
        except User.DoesNotExist:
            user_data = response_data["user"]
            user = User(username=user_data["username"])
            user.email = user_data["email"]
            user.first_name = user_data["first_name"]
            user.last_name = user_data["last_name"]
            user.is_staff = user_data["is_staff"]
            user.is_superuser = user_data["is_superuser"]
            user.is_active = user_data["is_active"]
            user.save()
        except Exception:
            return None
        return user

    def get_user(self, user_id: int):
        try:
            return User.objects.get(pk=user_id)
        except User.DoesNotExist:
            return None


================================================
File: omni_pro_base/http_request.py
================================================
import json
from json.decoder import JSONDecodeError

import requests
from requests.models import Response


class OmniRequest:
    @staticmethod
    def call_api(url, http_method, body: dict = {}, params={}, headers={}, **kwargs):
        request_params = {
            "method": http_method,
            "url": url,
            "headers": headers,
            "params": params,
        }
        if body:
            request_params["data"] = json.dumps(body).encode("utf-8")
            request_params["headers"]["Content-Type"] = "application/json"
            request_params["headers"]["charset"] = "utf-8"
        return requests.request(**request_params | kwargs)

    @staticmethod
    def get_response(response: Response):

        if not isinstance(response, Response):
            raise Exception("Param 'response' not atribute 'Response' class")

        def strftimedelta(t):
            mm, ss = divmod(t.seconds, 60)
            hh, mm = divmod(mm, 60)
            s = "%d:%d:%02d:%02d.%06d" % (t.days, hh, mm, ss, t.microseconds)
            return s

        response_object = dict(
            success=response.ok,
            status_code=response.status_code,
            decode=False,
            json_data={},
            content_type="json",
            elapsed=strftimedelta(response.elapsed),
            reason=response.reason,
            method=response.request.method,
            path_url=response.request.path_url,
            url=response.request.url,
            request_header=dict(response.request.headers),
            response_header=dict(response.headers),
        )

        try:
            json_data = response.json()
            decode = True
        except JSONDecodeError:
            json_data = response.text
            decode = False

        response_object["json_data"] = json_data
        response_object["decode"] = decode
        return response_object


================================================
File: omni_pro_base/urls.py
================================================
from django.urls import include, path

urlpatterns = [
    path(r"base/", include('health_check.urls')),
]


================================================
File: omni_pro_base/util.py
================================================
from functools import reduce

DEFAULT_RECORD_LIMIT = 10000


def nested(data: dict, keys: str, default=None):
    """
    Receives a dictionary and a list of keys, and returns the value associated with the keys in order,
    searching the dictionary to any depth, not including lists. in order, searching the dictionary to
    any depth, not including lists. If the key is not found, it returns the default value.
    """
    return reduce(lambda d, key: d.get(key, default) if isinstance(d, dict) else default, keys.split("."), data)


================================================
File: omni_pro_base/admin/__init__.py
================================================
from .auth import PermissionAdmin
from .base_admin import BaseAdmin, MixinSaveAdmin
from .users import UserAdmin

================================================
File: omni_pro_base/admin/auth.py
================================================
from django.contrib import admin
from django.contrib.auth.models import Permission


@admin.register(Permission)
class PermissionAdmin(admin.ModelAdmin):
    list_display = ("name", "content_type", "codename")
    list_filter = ("content_type",)
    search_fields = ("name", "codename")


================================================
File: omni_pro_base/admin/base_admin.py
================================================
from django.contrib import admin
from django.utils.translation import gettext_lazy as _


class MixinSaveAdmin(object):
    def save_model(self, request, obj, form, change):
        if not obj.pk:
            obj.created_by = request.user
        obj.updated_by = request.user
        super().save_model(request, obj, form, change)


class BaseAdmin(MixinSaveAdmin, admin.ModelAdmin):
    exclude = ("created_at", "updated_at")
    list_per_page = 20
    fieldsets = (
        (
            _("Audit Info"),
            {
                "fields": (
                    "is_active",
                    "created_by",
                    "updated_by",
                )
            },
        ),
    )


================================================
File: omni_pro_base/admin/users.py
================================================
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin as AuthUserAdmin
from django.utils.translation import gettext_lazy as _
from omni_pro_base.admin import MixinSaveAdmin
from omni_pro_base.models import User


@admin.register(User)
class UserAdmin(MixinSaveAdmin, AuthUserAdmin):
    list_display = (
        "email",
        "username",
        "name",
        "date_joined",
        "last_login",
        "is_staff",
        "is_active",
        "created_by",
        "updated_by",
    )
    list_filter = (
        "last_login",
        "date_joined",
        "is_active",
        "is_staff",
    )
    fieldsets = (
        (_("Primary info"), {"fields": ("email", "username", "password")}),
        (_("Personal info"), {"fields": ("first_name", "last_name")}),
        (
            _("Permissions"),
            {
                "fields": (
                    "is_active",
                    "is_staff",
                    "is_superuser",
                    "groups",
                ),
            },
        ),
    )
    add_fieldsets = (
        (
            None,
            {
                "classes": ("wide",),
                "fields": ("email", "username", "password1", "password2", "is_staff", "is_active", "groups"),
            },
        ),
    )
    search_fields = ("email", "username", "first_name", "last_name")
    ordering = ("email",)


================================================
File: omni_pro_base/forms/users.py
================================================
from django.contrib.auth.forms import UserChangeForm, UserCreationForm
from omni_pro_base.models import User


class UserCreationForm(UserCreationForm):
    class Meta:
        model = User
        fields = ("email",)


class UserChangeForm(UserChangeForm):
    class Meta:
        model = User
        fields = ("email",)


================================================
File: omni_pro_base/migrations/0001_initial.py
================================================
# Generated by Django 5.0 on 2024-02-02 15:53

import django.contrib.auth.models
import django.contrib.auth.validators
import django.db.models.deletion
import django.utils.timezone
from django.conf import settings
from django.db import migrations, models


class Migration(migrations.Migration):

    initial = True

    dependencies = [
        ("auth", "0012_alter_user_first_name_max_length"),
        migrations.swappable_dependency(settings.AUTH_USER_MODEL),
    ]

    operations = [
        migrations.CreateModel(
            name="User",
            fields=[
                ("id", models.BigAutoField(auto_created=True, primary_key=True, serialize=False, verbose_name="ID")),
                ("password", models.CharField(max_length=128, verbose_name="password")),
                ("last_login", models.DateTimeField(blank=True, null=True, verbose_name="last login")),
                (
                    "is_superuser",
                    models.BooleanField(
                        default=False,
                        help_text="Designates that this user has all permissions without explicitly assigning them.",
                        verbose_name="superuser status",
                    ),
                ),
                (
                    "username",
                    models.CharField(
                        error_messages={"unique": "A user with that username already exists."},
                        help_text="Required. 150 characters or fewer. Letters, digits and @/./+/-/_ only.",
                        max_length=150,
                        unique=True,
                        validators=[django.contrib.auth.validators.UnicodeUsernameValidator()],
                        verbose_name="username",
                    ),
                ),
                ("first_name", models.CharField(blank=True, max_length=150, verbose_name="first name")),
                ("last_name", models.CharField(blank=True, max_length=150, verbose_name="last name")),
                (
                    "is_staff",
                    models.BooleanField(
                        default=False,
                        help_text="Designates whether the user can log into this admin site.",
                        verbose_name="staff status",
                    ),
                ),
                (
                    "is_active",
                    models.BooleanField(
                        default=True,
                        help_text="Designates whether this user should be treated as active. Unselect this instead of deleting accounts.",
                        verbose_name="active",
                    ),
                ),
                ("date_joined", models.DateTimeField(default=django.utils.timezone.now, verbose_name="date joined")),
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
                ("email", models.EmailField(max_length=254, unique=True, verbose_name="email address")),
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
                    "groups",
                    models.ManyToManyField(
                        blank=True,
                        help_text="The groups this user belongs to. A user will get all permissions granted to each of their groups.",
                        related_name="user_set",
                        related_query_name="user",
                        to="auth.group",
                        verbose_name="groups",
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
                    "user_permissions",
                    models.ManyToManyField(
                        blank=True,
                        help_text="Specific permissions for this user.",
                        related_name="user_set",
                        related_query_name="user",
                        to="auth.permission",
                        verbose_name="user permissions",
                    ),
                ),
            ],
            options={
                "verbose_name": "user",
                "verbose_name_plural": "users",
                "abstract": False,
            },
            managers=[
                ("objects", django.contrib.auth.models.UserManager()),
            ],
        ),
    ]


================================================
File: omni_pro_base/models/__init__.py
================================================
from .base_model import OmniModel
from .users import User


================================================
File: omni_pro_base/models/base_model.py
================================================
from django.conf import settings
from django.db import models
from django.utils.translation import gettext_lazy as _


class ActivateManager(models.Manager):
    def get_queryset(self):
        return super(ActivateManager, self).get_queryset().filter(is_active=True)


class OmniModel(models.Model):
    created_at = models.DateTimeField(
        _("created at"),
        auto_now_add=True,
        help_text=_("Date time on which the object was created"),
    )

    updated_at = models.DateTimeField(
        _("updated by"),
        auto_now=True,
        help_text=_("Date time on which the object was last modified"),
    )

    is_active = models.BooleanField(
        _("is active"),
        default=True,
        help_text=_(
            "Designates whether this user should be treated as active. Unselect this instead of deleting accounts."
        ),
    )

    created_by = models.ForeignKey(
        settings.AUTH_USER_MODEL,
        on_delete=models.SET_NULL,
        null=True,
        related_name="%(app_label)s_%(class)s_created_by",
        verbose_name=_("created by"),
    )

    updated_by = models.ForeignKey(
        settings.AUTH_USER_MODEL,
        on_delete=models.SET_NULL,
        null=True,
        related_name="%(app_label)s_%(class)s_updated_by",
        verbose_name=_("updated by"),
    )

    objects = models.Manager()
    active_objects = ActivateManager()

    class Meta:
        """Meta options."""

        abstract = True
        get_latest_by = "created_at"
        ordering = ["-created_at", "-updated_at"]

    def save(self, *args, **kwargs):
        user = kwargs.pop("user", None)
        if self._state.adding and user:
            self.created_by = user
        if user:
            self.updated_by = user
        super().save(*args, **kwargs)


================================================
File: omni_pro_base/models/users.py
================================================
from django.contrib.auth.models import AbstractUser
from django.db import models
from django.utils.translation import gettext_lazy as _
from omni_pro_base.models.base_model import OmniModel


class User(AbstractUser, OmniModel):
    email = models.EmailField(_("email address"), unique=True)
    USERNAME_FIELD = "email"
    REQUIRED_FIELDS = ["username", "first_name", "last_name"]

    @property
    def name(self):
        return self.get_full_name()

    def __str__(self):
        return self.username


================================================
File: omni_pro_base/serializers/__init__.py
================================================
from .users import GroupSerializer, UserLoginSerializer, UserModelSerializer, UserSerializer

================================================
File: omni_pro_base/serializers/users.py
================================================
from django.contrib.auth import authenticate
from django.contrib.auth.models import Group
from omni_pro_base.models import User
from rest_framework import serializers
from rest_framework.authtoken.models import Token


class UserSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = User
        fields = [
            "id",
            "email",
            "username",
            "name",
            "first_name",
            "last_name",
            "url",
            "groups",
            "is_active",
            "last_login",
            "created_by",
            "created_at",
            "updated_by",
            "updated_at",
        ]


class GroupSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = Group
        fields = ["url", "name"]


class UserLoginSerializer(serializers.Serializer):
    """User login Serializer.

    Handle the login request data.
    """

    username = serializers.CharField(max_length=150)
    password = serializers.CharField(min_length=8, max_length=64)

    def validate(self, data):
        user = authenticate(username=data["username"], password=data["password"])
        if not user:
            raise serializers.ValidationError("Invalid credentials")
        self.context["user"] = user
        return data

    def create(self, data):
        """Generate or retrieve"""
        token, created = Token.objects.get_or_create(user=self.context["user"])
        return self.context["user"], token.key


class UserModelSerializer(serializers.ModelSerializer):
    class Meta:
        model = User
        fields = ("username", "first_name", "last_name", "email", "is_active")


================================================
File: omni_pro_base/settings/base.py
================================================
from pathlib import Path

from environs import Env
from kombu import Queue as kombuQueue

BASE_DIR = Path(__file__).resolve().parent.parent

env = Env()
env.read_env()

# Quick-start development settings - unsuitable for production
# See https://docs.djangoproject.com/en/5.0/howto/deployment/checklist/

# SECURITY WARNING: keep the secret key used in production secret!
SECRET_KEY = env.str("SECRET_KEY", default="django-insecure--fspfc--yg!p^)bi--2brjgyzb^fmu-3bh-#xxmb7gye7(b1-f")

# Internationalization
# https://docs.djangoproject.com/en/5.0/topics/i18n/
TIME_ZONE = env.str("TIME_ZONE", default="UTC")
LANGUAGE_CODE = env.str("LANGUAGE_CODE", default="en-us")
SITE_ID = 1
USE_I18N = env.bool("USE_I18N", default=True)
USE_TZ = env.bool("USE_TZ", default=True)

THEME_APPS = ["jazzmin"]

# Application definition
DJANGO_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
]

THIRD_PARTY_APPS = [
    "oauth2_provider",
    "rest_framework",
    "rest_framework.authtoken",
    "auditlog",
    "django_json_widget",
    "django_celery_results",
    "omni_pro_base",
    "omni_pro_oms",
    "rangefilter",
    "django_celery_beat",
    "import_export",
]

INSTALLED_APPS = THEME_APPS + DJANGO_APPS + THIRD_PARTY_APPS

MIDDLEWARE = [
    "allow_cidr.middleware.AllowCIDRMiddleware",
    "django.middleware.security.SecurityMiddleware",
    "django.contrib.sessions.middleware.SessionMiddleware",
    "django.middleware.common.CommonMiddleware",
    "django.middleware.csrf.CsrfViewMiddleware",
    "django.contrib.auth.middleware.AuthenticationMiddleware",
    "django.contrib.messages.middleware.MessageMiddleware",
    "django.middleware.clickjacking.XFrameOptionsMiddleware",
]

TEMPLATES = [
    {
        "BACKEND": "django.template.backends.django.DjangoTemplates",
        "DIRS": [],
        "APP_DIRS": True,
        "OPTIONS": {
            "context_processors": [
                "django.template.context_processors.debug",
                "django.template.context_processors.request",
                "django.contrib.auth.context_processors.auth",
                "django.contrib.messages.context_processors.messages",
            ],
        },
    },
]

# Database
# https://docs.djangoproject.com/en/5.0/ref/settings/#databases

DATABASES = {
    "default": env.dj_db_url("DATABASE_URL", default="sqlite:///db.sqlite3"),
}

# Configurar las opciones adicionales para la conexión
DATABASES["default"]["ATOMIC_REQUESTS"] = True

# Asegurarte de que el motor sea el correcto
DATABASES["default"]["ENGINE"] = "dj_db_conn_pool.backends.postgresql"

# Agregar las opciones del pool de conexiones
DATABASES["default"]["POOL_OPTIONS"] = {
    "POOL_SIZE": env.int("POOL_OPTIONS__POOL_SIZE", 10),  # The number of connections to use in the pool.
    "MAX_OVERFLOW": env.int("POOL_OPTIONS__MAX_OVERFLOW", 10),  # The maximum overflow size of the pool.
    "RECYCLE": env.int("POOL_OPTIONS__RECYCLE", 5 * 60),  # 15 minutes
}

# Jazzmin settings
JAZZMIN_SETTINGS = {
    "site_title": "OMS App",
    "site_header": "OMS App",
    "welcome_sign": "Welcome to OMS App",
    "site_brand": "OMS APP",
    "copyright": "© ATM Services All Rights Reserved",
    "login_logo": "vendor/omni/img/logo_login.svg",
    "custom_css": "vendor/omni/css/main.css",
    "custom_js": "vendor/omni/js/main.js",
    "site_logo": "vendor/omni/img/logo.svg",
    "site_icon": "vendor/omni/img/favicon.ico",
    "related_modal_active": True,
    "icons": {
        "auth": "fas fa-users-cog",
        "auth.user": "fas fa-user",
        "auth.Group": "fas fa-users",
    },
    "default_icon_parents": "fas fa-chevron-circle-right",
    "default_icon_children": "fas fa-cube",
    "changeform_format": "horizontal_tabs",
}

JAZZMIN_UI_TWEAKS = {
    "theme": "flatly",
    "dark_mode_theme": None,
    "sidebar": "sidebar-light-primary",
    "body_small_text": True,
    "sidebar_nav_compact_style": True,
}

JAZZMIN_SETTINGS["show_ui_builder"] = False

# Application definition
REST_FRAMEWORK = {
    "DEFAULT_AUTHENTICATION_CLASSES": [
        "rest_framework.authentication.TokenAuthentication",
        "rest_framework.authentication.BasicAuthentication",
        "rest_framework.authentication.SessionAuthentication",
        "oauth2_provider.contrib.rest_framework.OAuth2Authentication",
    ],
    "DEFAULT_RENDERER_CLASSES": [
        "rest_framework.renderers.JSONRenderer",
        "rest_framework.renderers.BrowsableAPIRenderer",
    ],
    "DEFAULT_PAGINATION_CLASS": "rest_framework.pagination.PageNumberPagination",
    "PAGE_SIZE": 10,
    "DEFAULT_PERMISSION_CLASSES": (
        "rest_framework.permissions.DjangoModelPermissionsOrAnonReadOnly",
        "oauth2_provider.contrib.rest_framework.TokenHasReadWriteScope",
        "rest_framework.permissions.IsAuthenticated",
    ),
}

OAUTH2_PROVIDER = {
    # this is the list of available scopes
    "SCOPES": {"read": "Read scope", "write": "Write scope"}
}

# Password validation
# https://docs.djangoproject.com/en/5.0/ref/settings/#auth-password-validators

AUTH_PASSWORD_VALIDATORS = [
    {
        "NAME": "django.contrib.auth.password_validation.UserAttributeSimilarityValidator",
    },
    {
        "NAME": "django.contrib.auth.password_validation.MinimumLengthValidator",
    },
    {
        "NAME": "django.contrib.auth.password_validation.CommonPasswordValidator",
    },
    {
        "NAME": "django.contrib.auth.password_validation.NumericPasswordValidator",
    },
]

PASSWORD_HASHERS = [
    "django.contrib.auth.hashers.Argon2PasswordHasher",
    "django.contrib.auth.hashers.PBKDF2PasswordHasher",
    "django.contrib.auth.hashers.PBKDF2SHA1PasswordHasher",
    "django.contrib.auth.hashers.BCryptSHA256PasswordHasher",
    "django.contrib.auth.hashers.ScryptPasswordHasher",
]

AUTH_USER_MODEL = "omni_pro_base.User"
LOGIN_REDIRECT_URL = "/admin/"

ADMIN_URL = env.str("ADMIN_URL", default="admin/")
ADMIN_LOGIN = env.str("ADMIN_LOGIN", default="oms@omni.pro")
ADMIN_PASSWORD = env.str(
    "ADMIN_PASSWORD",
    default="argon2$argon2id$v=19$m=102400,t=2,p=8$WVlMYVg1ZkJhMDRyV1hkb2hhb1BkdA$xsgpDV8dbFLBKM83JkTxJDCYCk30pbMo35KzwUXo848",
)
ADMIN_USERNAME = env.str("ADMIN_USERNAME", default=ADMIN_LOGIN)
ADMIN_FIRST_NAME = env.str("ADMIN_FIRST_NAME", default="OMS")
ADMIN_LAST_NAME = env.str("ADMIN_LAST_NAME", default="OMNI")
AUTH_BASE_URL = env.str("AUTH_BASE_URL", default="http://localhost:8000")
AUTH_APP_SERVICE_URL = env.str("AUTH_APP_SERVICE_URL", default=f"{AUTH_BASE_URL}/auth/users/login/")

AUTHENTICATION_BACKENDS = [
    "omni_pro_base.backends.SettingsBackend",
    "omni_pro_base.backends.AppUserBackend",
    "django.contrib.auth.backends.ModelBackend",
]

ADMINS = [("Author", "OMNI.PRO")]
MANAGERS = ADMINS

# Security
SESSION_COOKIE_HTTPONLY = True
CSRF_COOKIE_HTTPONLY = True
SECURE_BROWSER_XSS_FILTER = True
X_FRAME_OPTIONS = "SAMEORIGIN"

# Email
EMAIL_BACKEND = env.str("DJANGO_EMAIL_BACKEND", default="django.core.mail.backends.console.EmailBackend")

# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/5.0/howto/static-files/

STATIC_URL = env.str("STATIC_URL", default="static/")
STATIC_ROOT = env.str("STATIC_ROOT", default=str(BASE_DIR / "staticfiles/"))
STATICFILES_FINDERS = [
    "django.contrib.staticfiles.finders.FileSystemFinder",
    "django.contrib.staticfiles.finders.AppDirectoriesFinder",
]

MEDIA_URL = env.str("MEDIA_URL", default="media/")
MEDIA_ROOT = env.str("MEDIA_ROOT", default=str(BASE_DIR / "media/"))

# Default primary key field type
# https://docs.djangoproject.com/en/5.0/ref/settings/#default-auto-field

DEFAULT_AUTO_FIELD = "django.db.models.BigAutoField"

# CONFIGURATION CELERY
if USE_TZ:
    CELERY_TIMEZONE = TIME_ZONE
else:
    CELERY_TIMEZONE = "UTC"

CELERY_NAME_APP_DJANGO = env.str("CELERY_NAME_APP_DJANGO", default=None)
CELERY_BROKER_URL = env.str("CELERY_BROKER_URL", default="redis://127.0.0.1:6379/0")
# RESULT_BACKEND = env.str("RESULT_BACKEND", default=CELERY_BROKER_URL)
# RESULT_BACKEND = "django-db"

# QUEUE
# Celery settings
CELERY_NAME_QUEUE = CELERY_NAME_APP_DJANGO + "QUEUE_1"
CELERY_TASK_QUEUES = (kombuQueue(CELERY_NAME_QUEUE, routing_key=CELERY_NAME_QUEUE),)

CELERY_TASK_DEFAULT_QUEUE = CELERY_NAME_QUEUE
CELERY_TASK_DEFAULT_ROUTING_KEY = CELERY_NAME_QUEUE

CELERY_TASK_ROUTES = {
    f"{CELERY_NAME_APP_DJANGO}.tasks.*": {"queue": CELERY_NAME_QUEUE},
}

ACCEPT_CONTENT = ["json"]
RESULT_SERIALIZER = "json"
TASK_SERIALIZER = "json"

RESULT_PERSISTENT = True
CELERY_TASK_PERSISTENT = True
broker_connection_retry_on_startup = True

CELERY_MAX_RETRIES = env.int("CELERY_MAX_RETRIES", default=3)
CELERY_SECONDS_TIME_TO_RETRY = env.int("CELERY_SECONDS_TIME_TO_RETRY", default=30)

# CONFIGURATION CELERY RESULTS
CELERY_RESULT_EXTENDED = True
CELERY_CACHE_BACKEND = "django-cache"
CELERY_RESULT_BACKEND = "django-db"

ASYNC_TIMEOUT = env.int("ASYNC_TIMEOUT", default=30)  # tiempo en segundos

# CONFIGURATION CELERY BEAT
CELERY_BEAT_SCHEDULER = "django_celery_beat.schedulers:DatabaseScheduler"

# CONFIGURATION LOGGING
LOGGING_LEVEL = env.str("LOGGING_LEVEL", default="INFO")
LOGGING = {
    "version": 1,
    "disable_existing_loggers": False,
    "formatters": {
        "verbose": {
            "format": "[{levelname}] - [{asctime}]: {name} in line {lineno} - {message}",
            "style": "{",
        },
    },
    "handlers": {
        "console": {
            "class": "logging.StreamHandler",
            "formatter": "verbose",
        },
        # "file": {  # Handler for logging to a file
        #     "class": "logging.FileHandler",
        #     "filename": "debug.log",
        #     "formatter": "verbose",
        # },
    },
    "root": {
        "handlers": ["console"],
        "level": LOGGING_LEVEL,
    },
}


================================================
File: omni_pro_base/settings/local.py
================================================
"""  Local settings for the project. """

from .base import *  # NOQA

# SECURITY WARNING: don't run with debug turned on in production!
DEBUG = True

ALLOWED_HOSTS = ["*"]

# Cache
# TODO: falta por implementar
# CACHES = {"default": {"BACKEND": "django.core.cache.backends.locmem.LocMemCache", "LOCATION": ""}}


================================================
File: omni_pro_base/settings/production.py
================================================
""" Production settings """

from .base import *  # NOQA

# SECURITY WARNING: don't run with debug turned on in production!
DEBUG = False

ALLOWED_HOSTS = env.list("ALLOWED_HOSTS", default=["*.omni.pro"])
ALLOWED_CIDR_NETS = env.list("ALLOWED_CIDR_NETS", default=[])
CSRF_TRUSTED_ORIGINS = env.list("CSRF_TRUSTED_ORIGINS", default=[])

DJA = len(THEME_APPS + DJANGO_APPS)
INSTALLED_APPS.insert(DJA, "corsheaders")

MIDDLEWARE.insert(2, "whitenoise.middleware.WhiteNoiseMiddleware")
MIDDLEWARE.insert(4, "corsheaders.middleware.CorsMiddleware")

# whitenoise settings
STORAGES = {
    "default": {
        "BACKEND": "django.core.files.storage.FileSystemStorage",
    },
    "staticfiles": {
        "BACKEND": "whitenoise.storage.CompressedManifestStaticFilesStorage",
    },
}
STATIC_HOST = env.str("DJANGO_STATIC_HOST", default="")
STATIC_URL = STATIC_HOST + "/static/"

# Cache
# TODO: falta por implementar
# CACHES = {
#     "default": {
#         "BACKEND": "django_redis.cache.RedisCache",
#         "LOCATION": env.list("REDIS_URL", default=["redis://127.0.0.1:6379"]),
#         "OPTIONS": {
#             "CLIENT_CLASS": "django_redis.client.DefaultClient",
#             "IGNORE_EXCEPTIONS": True,
#         },
#     }
# }


================================================
File: omni_pro_base/static/vendor/omni/css/main.css
================================================
.navbar {
    background-color: #122DFF;
    /* Puedes cambiar "blue" al color que desees */
}

.navbar-light .navbar-nav .nav-link {
    color: #fff;
}

.btn-info {
    color: #fff;
    background-color: #0096ff;
    border-color: #0096ff;
}

.fa-inverse {
    color: #000000;
}

.nav-sidebar>.nav-item>.nav-link.active,
.sidebar-light-primary .nav-sidebar>.nav-item>.nav-link.active {
    color: #fff;
    background-color: #122DFF;
}

================================================
File: omni_pro_base/views/__init__.py
================================================
from .users import UserViewSet, GroupViewSet

================================================
File: omni_pro_base/views/users.py
================================================
from django.contrib.auth.models import Group
from omni_pro_base.models import User
from omni_pro_base.serializers import GroupSerializer, UserLoginSerializer, UserModelSerializer, UserSerializer
from rest_framework import status, viewsets
from rest_framework.decorators import action
from rest_framework.permissions import AllowAny, IsAuthenticated
from rest_framework.response import Response


class UserViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows users to be viewed or edited.
    """

    queryset = User.active_objects.all().order_by("-date_joined")
    serializer_class = UserSerializer


class GroupViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows groups to be viewed or edited.
    """

    queryset = Group.objects.all()
    serializer_class = GroupSerializer


class UserLoginViewSet(viewsets.GenericViewSet):
    serializer_class = UserLoginSerializer

    @action(detail=False, methods=["post"])
    def login(self, request):
        serializer = UserLoginSerializer(data=request.data)
        serializer.is_valid(raise_exception=True)
        user, token = serializer.save()
        data = {
            "user": UserModelSerializer(user).data,
            "access_token": token,
        }
        return Response(data, status=status.HTTP_200_OK)

    def get_permissions(self):
        if self.action in ["login"]:
            permissions = [AllowAny]
        else:
            permissions = [IsAuthenticated]
        return [permission() for permission in permissions]


