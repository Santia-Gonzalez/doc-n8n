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

<h3 align="center">omnipro-solutions-saas-app-base</h3>

  <p align="center">
    Biblioteca de módulos base para aplicaciones Django conectadas al Open Management System (OMS).
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/Omnipro-Solutions/saas-app-base/issues">Report Bug</a>
    &middot;
    <a href="https://github.com/Omnipro-Solutions/saas-app-base/pullrequest">Request Feature</a>
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

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de módulos base diseñada para ser utilizada en aplicaciones Django que se conectan al Open Management System (OMS). Su propósito principal es proporcionar componentes predefinidos, configuraciones y funcionalidades comunes que faciliten el desarrollo rápido y eficiente de aplicaciones dentro del ecosistema OMS. Entre sus características principales se incluyen:

- **Modelos de Usuario**: Implementación personalizada del modelo `User` con campos adicionales para manejar información de auditoría.
- **Autenticación**: Backends de autenticación que permiten el uso tanto de credenciales estáticas como dinámicas obtenidas a través de servicios externos.
- **Serialización y Formularios**: Definiciones de serializers y formularios para usuarios, facilitando la interacción con APIs RESTful.
- **Administración Django**: Personalizaciones en los administradores de modelos para incluir campos adicionales relacionados con auditoría.
- **Configuraciones Base**: Configuraciones para diferentes entornos (desarrollo, producción) que incluyen configuraciones de seguridad, middleware y manejo de archivos estáticos.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built With

Este proyecto ha sido construido utilizando las siguientes tecnologías:

* [![Python][python-logo]][python-url]
* [![Django][django-logo]][django-url]
* [![Django REST Framework][djangorestframework-logo]][djangorestframework-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

A continuación, se presentan instrucciones claras y precisas para configurar el proyecto en un entorno local.

### Prerequisites

Antes de comenzar, asegúrate de tener lo siguiente instalado:

- Python 3.11 o superior
- Django versión 5.0
- Dependencias adicionales listadas en `requirements.txt`

### Installation

1. Clona el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```

2. Crea un entorno virtual (opcional):
   ```bash
   python -m venv venv
   source venv/bin/activate  # En Windows: venv\Scripts\activate
   ```

3. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

4. Configura las variables de entorno copiando y editando el archivo `.env` para incluir las variables necesarias como `SECRET_KEY`, `DATABASE_URL`, etc.

5. Genera migraciones:
   ```bash
   python manage.py makemigrations
   ```

6. Aplica migraciones:
   ```bash
   python manage.py migrate
   ```

7. (Opcional) Crea un superusuario Django:
   ```bash
   python manage.py createsuperuser
   ```

8. Ejecuta el servidor de desarrollo:
   ```bash
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage

Para utilizar esta biblioteca, puedes crear una nueva aplicación Django que use este módulo base. Aquí te mostramos un ejemplo sencillo:

1. Crea un nuevo proyecto Django:
   ```bash
   django-admin startproject my_project
   cd my_project
   ```

2. Agrega `omni_pro_base` a `INSTALLED_APPS` en `settings.py`:
   ```python
   INSTALLED_APPS = [
       ...
       'omni_pro_base',
   ]
   ```

3. Configura la base de datos y otras variables de entorno.

4. Ejecuta el proyecto:
   ```bash
   python manage.py runserver
   ```

5. Accede a la interfaz administrativa navegando a `http://127.0.0.1:8000/admin/` e ingresa con las credenciales del superusuario.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implementación del sistema de caché para mejorar el rendimiento.
- [ ] Revisión y fortalecimiento de las políticas de seguridad, especialmente en producción.
- [ ] Añadir pruebas unitarias y de integración para asegurar la calidad del código.

Ver los [issues abiertos](https://github.com/Omnipro-Solutions/saas-app-base/issues) para una lista completa de características propuestas (y problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Las contribuciones son lo que hacen a la comunidad de código abierto un lugar increíble para aprender, inspirar y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "enhancement".
¡No olvides darle a este proyecto una estrella! ¡Gracias nuevamente!

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

Distribuido bajo la licencia MIT. Consulta `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Para consultas, por favor contacta a:

- **Correo Electrónico:** [contact@omni.pro](mailto:contact@omni.pro)
- **LinkedIn:** [linkedin.com/in/omnipro-solutions](https://www.linkedin.com/company/omni.pro)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

Agradecimientos especiales a todos los colaboradores y usuarios que han contribuido al desarrollo de este proyecto.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

[contributors-shield]: https://img.shields.io/github/contributors/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/Omnipro-Solutions/saas-app-base/network/members
[issues-shield]: https://img.shields.io/github/issues/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/Omnipro-Solutions/saas-app-base/issues
[license-shield]: https://img.shields.io/badge/license-MIT-blue.svg?style=for-the-badge
[license-url]: https://github.com/Omnipro-Solutions/saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/
[python-logo]: https://img.shields.io/badge/python-3.11-blue.svg?style=flat-square&logo=Python
[python-url]: https://www.python.org/
[django-logo]: https://img.shields.io/badge/Django-5.0-green.svg?style=flat-square&logo=Django
[django-url]: https://www.djangoproject.com/
[djangorestframework-logo]: https://img.shields.io/badge/django_rest_framework-3.14-blue.svg?style=flat-square&logo=Django+REST+Framework
[djangorestframework-url]: https://www.django-rest-framework.org/