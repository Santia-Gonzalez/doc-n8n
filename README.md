```markdown
<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<a
href="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDI0IiBoZWlnaHQ9IjEwMjQiIHZpZXdCb3g9IjAgMCAxMDI0IDEwMjQiPjxwYXRoIGZpbGw9ImN1cnJlbnRDb2xvciIgZD0iTTYyOC43MzYgNTI4Ljg5NkE0MTYgNDE2IDAgMCAxIDkyOCA5MjhIOTZhNDE1Ljg3IDQxNS44NyAwIDAgMSAyOTkuMjY0LTM5OS4xMDRMNTEyIDcwNHpNNzIwIDMwNGEyMDggMjA4IDAgMSAxLTQxNiAwYTIwOCAyMDggMCAwIDEgNDE2IDAiLz48L3N2Zz4=">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Omni-Pro Solutions SaaS App Base</h3>

  <p align="center">
    Biblioteca de módulos base para aplicaciones Django que se conectan a Omnipro Solutions.
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

El repositorio `omni-pro-solutions-saas-app-base` es una biblioteca de módulos base diseñada para aplicaciones Django que se integran con Omnipro Solutions. Proporciona funcionalidades esenciales como la gestión de usuarios, autenticación personalizada y configuraciones del entorno de desarrollo, facilitando el despliegue rápido y seguro de aplicaciones SaaS.

### Built With

* [![Django][Django]][Django-url]
* [![DJANGO REST Framework][DRF]][DRF-url]
* [![Celery][Celery]][Celery-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Prerequisites

Asegúrate de tener instalados:

- Python 3.8 o superior
- Pip (gestor de paquetes)
- Git

### Installation

1. Clona el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```

2. Crea un entorno virtual (opcional pero recomendado):
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: .\env\Scripts\activate
   ```

3. Instala las dependencias:
   ```sh
   pip install -r requirements.txt
   ```

4. Genera migraciones iniciales y ejecútalas:
   ```sh
   python make_migrations.py
   ```

5. Inicia el servidor Django:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage

Para utilizar la biblioteca en un proyecto Django, sigue estos pasos:

1. Agrega `omni_pro_base` a `INSTALLED_APPS`:
   ```python
   INSTALLED_APPS = [
       ...
       'omni_pro_base',
   ]
   ```

2. Configura las URLs:
   En tu archivo `urls.py`, incluye las URL del módulo base:
   ```python
   from django.urls import path, include

   urlpatterns = [
       path('base/', include('omni_pro_base.urls')),
       ...
   ]
   ```

3. Accede a la API de Usuarios:
   - Crea un usuario utilizando el `UserCreationForm` personalizado.
   - Autentica un usuario enviando una solicitud POST al endpoint `/base/users/login/`.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implementación de caché
- [ ] Agregar pruebas unitarias
- [ ] Mejorar documentación avanzada

Ver los [issues abiertos](https://github.com/Omnipro-Solutions/saas-app-base/issues) para una lista completa de características propuestas (y problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Las contribuciones hacen que la comunidad de código abierto sea un lugar increíble para aprender, inspirarse y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forke el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "enhancement". No olvides darle a este proyecto una estrella! ¡Gracias nuevamente!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top contributors:

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## License

Distribuido bajo la licencia MIT. Consulta el archivo `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Para cualquier consulta, no dudes en contactarnos a través de nuestro [LinkedIn](https://www.linkedin.com/company/omni.pro/) o por correo electrónico: `info@omnipro.solutions`.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/Omnipro-Solutions/saas-app-base/network/members
[issues-shield]: https://img.shields.io/github/issues/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/Omnipro-Solutions/saas-app-base/issues
[license-shield]: https://img.shields.io/github/license/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[license-url]: https://github.com/Omnipro-Solutions/saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/

[Django]: https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=djangoproject&logoColor=white
[Django-url]: https://www.djangoproject.com/
[DRF]: https://img.shields.io/badge/drf-3.13.1-blue.svg?style=flat-square
[DRF-url]: https://www.django-rest-framework.org/
[Celery]: https://img.shields.io/badge/Celery-4.4.7-yellowgreen.svg?style=flat-square
[Celery-url]: http://www.celeryproject.org/

```

Este documento proporciona una guía completa sobre el repositorio `omni-pro-solutions-saas-app-base`, incluyendo su propósito, cómo configurarlo y utilizarlo en un entorno local. Está diseñado para ser profesional, claro y visualmente atractivo para los usuarios.