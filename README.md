# Documentación del Repositorio: `omnipro-solutions-saas-app-base`

<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![Project License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<a href="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDI0IiBoZWlnaHQ9IjEwMjQiIHZpZXdCb3g9IjAgMCAxMDI0IDEwMjQiPjxwYXRoIGZpbGw9ImN1cnJlbnRDb2xvciIgZD0iTTYyOC43MzYgNTI4Ljg5NkE0MTYgNDE2IDAgMCAxIDkyOCA5MjhIOTZhNDE1Ljg3IDQxNS44NyAwIDAgMSAyOTkuMjY0LTM5OS4xMDRMNTEyIDcwNHpNNzIwIDMwNGEyMDggMjA4IDAgMSAxLTQxNiAwYTIwOCAyMDggMCAwIDEgNDE2IDAiLz48L3N2Zz4=">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Biblioteca Base para Aplicaciones SaaS</h3>

  <p align="center">
    Una biblioteca de módulo base diseñada para facilitar el desarrollo de aplicaciones SaaS conectadas a Open Management System (OMS).
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    &middot;
    <a href="#">Report Bug</a>
    &middot;
    <a href="#">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

El repositorio `omnipro-solutions-saas-app-base` actúa como una biblioteca de módulo base para aplicaciones SaaS conectadas a OMS (Open Management System). Su propósito principal es proporcionar un conjunto de funcionalidades comunes que pueden ser utilizadas por las aplicaciones desarrolladas bajo el ecosistema OMNI.PRO. Las principales características incluyen:

- **Gestión de Usuarios y Permisos**: Modelos, vistas y serializadores para gestionar usuarios y grupos.
- **Autenticación y Autorización**: Backends personalizados para autenticación a través de configuraciones estáticas o servicios externos.
- **Configuración del Entorno Django**: Configuraciones base y locales para entornos de desarrollo y producción.
- **Soporte para Celery**: Integración con Celery para la ejecución de tareas asíncronas.

Este repositorio facilita el desarrollo rápido y eficiente de aplicaciones SaaS al proporcionar herramientas esenciales que se integran sin problemas en el ecosistema OMNI.PRO.

### Built With

La biblioteca está construida utilizando una variedad de tecnologías líderes:

* [![Python][Python]][Python-url]
* [![Django][Django]][Django-url]
* [![Celery][Celery]][Celery-url]
* [![Redis][Redis]][Redis-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

A continuación, se presentan las instrucciones para configurar el proyecto en tu entorno local.

### Prerequisites

Antes de comenzar, asegúrate de tener instalados los siguientes componentes:

- Python 3.11 o superior
- PostgreSQL (o un motor de base de datos compatible)
- Redis

### Installation

1. **Clonar el Repositorio**
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```

2. **Crear un Entorno Virtual (Opcional pero Recomendado)**
   ```bash
   python -m venv env
   source env/bin/activate  # En Windows: .\env\Scripts\activate
   ```

3. **Instalar Dependencias**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configurar Variables de Entorno**
   Copiar `omni_pro_base/settings/local.py.example` a `local.py` y ajustar las variables según sea necesario.

5. **Ejecutar Migraciones**
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

6. **Crear un Superusuario (Opcional)**
   ```bash
   python manage.py createsuperuser
   ```

7. **Iniciar el Servidor de Desarrollo**
   ```bash
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage

Para utilizar esta biblioteca en tu proyecto, sigue estos pasos:

1. **Crear una Aplicación Django** y agregar `omni_pro_base` a tus `INSTALLED_APPS`.
2. **Definir Rutas**: Incluir las vistas proporcionadas en tu archivo `urls.py`.

```python
# urls.py de la aplicación Django
from django.urls import path, include

urlpatterns = [
    path('api/', include('omni_pro_base.urls')),
]
```

Esto te permitirá acceder a funcionalidades del módulo base, como gestionar usuarios y grupos a través de endpoints RESTful proporcionados por `UserViewSet` y `GroupViewSet`.

_For more examples, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

Proyectos futuros incluyen:

- Mejorar los backends de autenticación para soportar más proveedores externos.
- Implementar pruebas unitarias completas en el directorio `tests/`.
- Extender las capacidades de internacionalización e implementar traducciones adicionales.

Verifica la lista completa de características propuestas y problemas conocidos [aquí](#).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Las contribuciones son lo que hacen a la comunidad de código abierto un lugar tan maravilloso para aprender, inspirar y crear. ¡Cualquier contribución que hagas es **muy apreciada**!

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "enhancement". 
No olvides darle al proyecto una estrella. ¡Gracias nuevamente!

1. **Fork the Project**
2. **Create your Feature Branch** (`git checkout -b feature/AmazingFeature`)
3. **Commit your Changes** (`git commit -m 'Add some AmazingFeature'`)
4. **Push to the Branch** (`git push origin feature/AmazingFeature`)
5. **Open a Pull Request**

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top contributors:

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="Contributors Image" />
</a>

<!-- LICENSE -->
## License

Distribuido bajo la licencia MIT. Consulta `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Para cualquier consulta o sugerencia, puedes contactar a través de:

- **Email**: [email@omni.pro](mailto:email@omni.pro)
- **LinkedIn**: [OMNI.PRO LinkedIn Page](https://www.linkedin.com/company/omni.pro)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

Agradecimientos especiales a:

- El equipo de OMNI.PRO por su apoyo continuo.
- La comunidad de código abierto que contribuye al proyecto.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/Omnipro-Solutions/saas-app-base/network/members
[stars-shield]: https://img.shields.io/github/stars/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[stars-url]: https://github.com/Omnipro-Solutions/saas-app-base/stargazers
[issues-shield]: https://img.shields.io/github/issues/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/Omnipro-Solutions/saas-app-base/issues
[license-shield]: https://img.shields.io/badge/license-MIT-blue.svg?style=for-the-badge
[license-url]: https://github.com/Omnipro-Solutions/saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/

[Python]: https://img.shields.io/badge/python-3.11-blue.svg
[Python-url]: https://www.python.org/
[Django]: https://img.shields.io/badge/django-5.0-green.svg
[Django-url]: https://www.djangoproject.com/
[Celery]: https://img.shields.io/badge/celery-brightgreen.svg
[Celery-url]: http://www.celeryproject.org/
[Redis]: https://img.shields.io/badge/redis-blueviolet.svg
[Redis-url]: https://redis.io/