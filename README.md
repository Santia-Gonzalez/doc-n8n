# Repositorio `omnipro-solutions-saas-app-base`

<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<a href="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDI0IiBoZWlnaHQ9IjEwMjQiIHZpZXdCb3g9IjAgMCAxMDI0IDEwMjQiPjxwYXRoIGZpbGw9ImN1cnJlbnRDb2xvciIgZD0iTTYyOC43MzYgNTI4Ljg5NkE0MTYgNDE2IDAgMCAxIDkyOCA5MjhIOTZhNDE1Ljg3IDQxNS44NyAwIDAgMSAyOTkuMjY0LTM5OS4xMDRMNTEyIDcwNHpNNzIwIDMwNGEyMDggMjA4IDAgMSAxLTQxNiAwYTIwOCAyMDggMCAwIDEgNDE2IDAiLz48L3N2Zz4=">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Biblioteca Base para Aplicaciones SaaS</h3>

  <p align="center">
    Una biblioteca de módulos base diseñada para facilitar el desarrollo de aplicaciones SaaS que se integran con Omnipro Solutions, ofreciendo funcionalidades estándar y configurables.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explora la documentación »</strong></a>
    <br />
    <br />
    &middot;
    <a href="#">Reportar un error</a>
    &middot;
    <a href="#">Solicitar una característica</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de Contenidos</summary>
  <ol>
    <li>
      <a href="#about-the-project">Acerca del Proyecto</a>
      <ul>
        <li><a href="#built-with">Construido con</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Comenzando</a>
      <ul>
        <li><a href="#prerequisites">Requisitos previos</a></li>
        <li><a href="#installation">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#usage">Uso</a></li>
    <li><a href="#roadmap">Plan de Desarrollo</a></li>
    <li><a href="#contributing">Contribuciones</a></li>
    <li><a href="#license">Licencia</a></li>
    <li><a href="#contact">Contacto</a></li>
    <li><a href="#acknowledgments">Agradecimientos</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## Acerca del Proyecto

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de módulos base para aplicaciones que se integran con Omnipro Solutions. Su propósito principal es proporcionar funcionalidades estándar y configurables que faciliten el desarrollo de aplicaciones SaaS, integrando servicios como autenticación, gestión de usuarios y API RESTful.

### Funcionalidades Principales

- **Autenticación y Autorización**: Soporte para la autenticación mediante tokens OAuth2.
- **Gestión de Usuarios**: Modelos personalizados que extienden `AbstractUser` de Django, permitiendo el uso del email como nombre de usuario principal.
- **Serialización de Datos**: Utiliza el framework REST Framework de Django para serializar usuarios y grupos.
- **Administración de Django**: Configuraciones personalizadas del panel de administración utilizando Jazzmin, un tema moderno y configurable.
- **APIs RESTful**: Endpoints para la gestión de usuarios y grupos.
- **Soporte Celery**: Configuración básica para el manejo de tareas asíncronas con Celery.

### Construido con

* [![Django][Django]][Django-url]
* [![Python][Python]][Python-url]
* [![REST Framework][DRF]][DRF-url]
* [![Celery][Celery]][Celery-url]

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>


<!-- GETTING STARTED -->
## Comenzando

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Requisitos previos

Asegúrate de tener instalado Python y Django. También necesitarás Redis para Celery.

### Instalación

1. Clona el repositorio
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   ```
2. Navega al directorio del proyecto
   ```sh
   cd saas-app-base
   ```
3. Crea un entorno virtual y activalo
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: .\env\Scripts\activate
   ```
4. Instala las dependencias necesarias
   ```sh
   pip install -r requirements.txt
   ```
5. Configura tus variables de entorno en un archivo `.env` con las siguientes claves:
   - `SECRET_KEY`
   - `DATABASE_URL`
6. Genera y aplica migraciones
   ```sh
   python make_migrations.py
   python manage.py migrate
   ```
7. (Opcional) Crea un superusuario Django
   ```sh
   python manage.py createsuperuser
   ```

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>


<!-- USAGE EXAMPLES -->
## Uso

Para utilizar la biblioteca en un proyecto Django, sigue estos pasos:

1. Añade `omni_pro_base` a `INSTALLED_APPS` en tu archivo `settings.py`.
2. Configura el backend de autenticación personalizado en `AUTHENTICATION_BACKENDS`.
3. Define rutas adicionales en `urls.py`, incluyendo las proporcionadas por `omni_pro_base.urls`.

Ejemplo básico para iniciar una aplicación:

```python
# settings.py
INSTALLED_APPS = [
    # Otros apps
    'omni_pro_base',
]

AUTHENTICATION_BACKENDS = [
    'omni_pro_base.backends.SettingsBackend',
    'django.contrib.auth.backends.ModelBackend',
]

# urls.py
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/', include('omni_pro_base.urls')),
]
```

Para más ejemplos, consulta la [documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- ROADMAP -->
## Plan de Desarrollo

- [ ] Implementación completa del caché
- [ ] Pruebas automáticas
- [ ] Documentación mejorada
- [ ] Seguridad adicional

Consulta los [issues abiertos](https://github.com/Omnipro-Solutions/saas-app-base/issues) para una lista completa de características propuestas y problemas conocidos.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- CONTRIBUTING -->
## Contribuciones

Las contribuciones hacen que la comunidad de código abierto sea un lugar increíble para aprender, inspirarse y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forke el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "mejora".
¡No olvides darle al proyecto una estrella! ¡Gracias nuevamente!

1. Fork del Proyecto
2. Crea tu rama de característica (`git checkout -b feature/AmazingFeature`)
3. Comitea tus Cambios (`git commit -m 'Añade alguna AmazingFeature'`)
4. Empuja a la Rama (`git push origin feature/AmazingFeature`)
5. Abre una Solicitud de Extracción

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Principales contribuidores:

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="Contribuciones de los usuarios" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. Consulta el archivo `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/Omnipro-Solutions/saas-app-base/network/members
[stars-shield]: https://img.shields.io/github/stars/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[stars-url]: https://github.com/Omnipro-Solutions/saas-app-base/stargazers
[issues-shield]: https://img.shields.io/github/issues/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/Omnipro-Solutions/saas-app-base/issues
[license-shield]: https://img.shields.io/github/license/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[license-url]: https://github.com/Omnipro-Solutions/saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/

[Django]: https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=djangoproject&logoColor=white
[Django-url]: https://www.djangoproject.com/
[Python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[Python-url]: https://www.python.org/
[DRF]: https://img.shields.io/badge/Django_REST_Framework-092E20?style=for-the-badge&logo=djangorestframework&logoColor=white
[DRF-url]: https://www.django-rest-framework.org/
[Celery]: https://img.shields.io/badge/Celery-008000?style=for-the-badge&logo=celery&logoColor=white
[Celery-url]: http://www.celeryproject.org/