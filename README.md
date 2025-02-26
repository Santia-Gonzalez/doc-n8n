<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />

<div align="center">
  <a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base.git">
    <img src="https://th.bing.com/th/id/OIP.ddlVF3lJNr9URRtdchRLcQHaHa?rs=1&pid=ImgDetMain" alt="Logo" width="80" height="80">
  </a>
  
  <h3 align="center">omnipro-solutions-saas-app-base</h3>

  <p align="center">
    Librería base para aplicaciones Django que se conectan a OMS (Open Management System).
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues">Report Bug</a>
    &middot;
    <a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/pulls">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de Contenidos</summary>
  <ol>
    <li>
      <a href="#sobre-el-proyecto">Sobre el Proyecto</a>
      <ul>
        <li><a href="#construido-con">Construido con</a></li>
      </ul>
    </li>
    <li>
      <a href="#configuración-inicial">Configuración Inicial</a>
      <ul>
        <li><a href="#requisitos-previos">Requisitos previos</a></li>
        <li><a href="#instalación">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#uso">Uso</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contribuyendo">Contribuyendo</a></li>
    <li><a href="#licencia">Licencia</a></li>
    <li><a href="#contacto">Contacto</a></li>
    <li><a href="#agradecimientos">Agradecimientos</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## Sobre el Proyecto

El repositorio `omnipro-solutions-saas-app-base` es una librería base para aplicaciones Django que se conectan a OMS (Open Management System). Su propósito principal es proporcionar funcionalidades comunes y configuraciones predeterminadas para desarrolladores que desean crear aplicaciones SaaS basadas en Django. Entre sus principales características incluyen:

- **Autenticación**: Ofrece múltiples métodos de autenticación, como el uso del backend personalizado `SettingsBackend` y `AppUserBackend`.
- **Serialización y API RESTful**: Incluye serializadores para modelos de usuario y grupos, así como vistas basadas en conjuntos (ViewSet) que facilitan la creación de endpoints RESTful.
- **Admin Personalizado**: Proporciona una interfaz administrativa personalizada con campos adicionales y funcionalidades específicas del proyecto.
- **Manejo de Migraciones**: Utiliza un script (`make_migrations.py`) para generar migraciones automáticamente.
- **Configuración de Entorno**: Incluye archivos como `requirements.txt` y `setup.py`, que facilitan la instalación y configuración del entorno de desarrollo.

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

### Construido con

* [![Django][Django.com]][Django-url]
* [![DRF][DRF.com]][DRF-url]
* [![Python][Python.com]][Python-url]

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

<!-- GETTING STARTED -->
## Configuración Inicial

Dame instrucciones claras y precisas de cómo configurar el proyecto en mi entorno local.

### Requisitos Previos

Para instalar y ejecutar este repositorio, necesitarás lo siguiente:

- Python 3.8 o superior
- Django 5.0
- pip

### Instalación

1. Clona el repositorio
   ```sh
   git clone https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base.git
   ```
2. Crea un entorno virtual y actívalo
   ```sh
   python3 -m venv env
   source env/bin/activate
   ```
3. Instala las dependencias del proyecto
   ```sh
   pip install -r requirements.txt
   ```
4. Configura la base de datos (por ejemplo, SQLite)
   ```bash
   export DATABASE_URL=sqlite:///db.sqlite3
   ```
5. Corre los scripts para crear y aplicar migraciones
   ```sh
   python make_migrations.py
   python manage.py migrate
   ```
6. Crea un superusuario para el panel administrativo
   ```sh
   python manage.py createsuperuser
   ```

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

<!-- USAGE EXAMPLES -->
## Uso

El repositorio `omnipro-solutions-saas-app-base` proporciona funcionalidades comunes para aplicaciones Django SaaS, incluyendo autenticación personalizada, serialización de modelos y vistas RESTful.

### Ejemplo: Crear un endpoint API para usuarios

Para crear un endpoint API que permita gestionar usuarios:

1. Añade el módulo `omni_pro_base` a tus aplicaciones en `settings.py`.
2. Importa los serializadores necesarios desde `serializers.users`.
3. Define las vistas basadas en conjuntos (`ViewSet`) para manejar operaciones CRUD.
4. Configura las rutas URL para los endpoints API.

```python
from django.urls import path, include
from rest_framework.routers import DefaultRouter
from omni_pro_base.serializers.users import UserViewSet

router = DefaultRouter()
router.register(r'users', UserViewSet)

urlpatterns = [
    path('api/', include(router.urls)),
]
```

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Mejorar la documentación detallada
- [ ] Ampliar las pruebas unitarias en `tests/`
- [ ] Implementar soporte adicional para otros métodos de autenticación
- [ ] Mejorar la personalización visual con CSS y JavaScript adicionales
- [ ] Generar documentación automática para los endpoints RESTful

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Las contribuciones son lo que hacen a la comunidad de código abierto un lugar tan increíble. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia para mejorar el proyecto, por favor crea un pull request o abre un issue con la etiqueta "enhancement".

1. Haz un fork del repositorio
2. Crea tu rama (`git checkout -b feature/AmazingFeature`)
3. Realiza tus cambios y haz commit (`git commit -m 'Añade alguna característica'`)
4. Empuja a tu ramificación (`git push origin feature/AmazingFeature`)
5. Abre un pull request

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

### Top contributors:

<a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/omnipro-solutions-saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. Consulta el archivo `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[contributors-shield]: https://img.shields.io/github/contributors/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/network/members
[stars-shield]: https://img.shields.io/github/stars/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[stars-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/stargazers
[issues-shield]: https://img.shields.io/github/issues/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/Omnipro-Solutions/imos-backend/issues
[license-shield]: https://img.shields.io/github/license/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[license-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/
[Django.com]: https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white
[Django-url]: https://djangoproject.com
[DRF.com]: https://img.shields.io/badge/DRF-64656D?style=for-the-badge&logo=djangorestframework&logoColor=white
[DRF-url]: https://www.django-rest-framework.org/
[Python.com]: https://img.shields.io/badge/python-%2314354C.svg?style=for-the-badge&logo=python&logoColor=ffdd54
[Python-url]: https://www.python.org/