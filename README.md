<a id="readme-top"></a>
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<br />
<div align="center">

<a href="https://github.com/Omnipro-Solutions/saas-app-base.git">
    <img src="https://th.bing.com/th/id/OIP.ddlVF3lJNr9URRtdchRLcQHaHa?rs=1&pid=ImgDetMain" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">omnipro-solutions-saas-app-base</h3>

  <p align="center">
    Una biblioteca de Python diseñada para ser un módulo base en aplicaciones Django, específicamente dirigida a integrarse con el sistema OMS (Omnipro Management System).
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

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de Python diseñada para ser un módulo base en aplicaciones Django, específicamente dirigida a integrarse con el sistema OMS (Omnipro Management System). Su propósito principal es proporcionar funcionalidades comunes y reutilizables que facilitan la creación de aplicaciones SaaS dentro del ecosistema Omnipro. Las principales funcionalidades incluyen autenticación, modelos auditados, serialización, personalización del panel de administración Django mediante Jazzmin, y soporte para configuraciones dinámicas.

### Built With

* [![Python][python]][python-url]
* [![Django][django]][django-url]
* [![Jazzmin][jazzmin]][jazzmin-url]
* [![Django Rest Framework][djangorestframework]][djangorestframework-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Prerequisites

- Python 3.8 o superior
- Django 3.2 o superior
- PostgreSQL (opcional, se puede usar SQLite)

### Installation

1. Clona el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```
2. Crea un entorno virtual y activa:
   ```bash
   python -m venv env
   source env/bin/activate  # En Windows: env\Scripts\activate
   ```
3. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```
4. Configura las variables de entorno necesarias (puedes usar un archivo `.env` y `environs` para gestionarlas).
5. Crea la base de datos SQLite (o configura PostgreSQL si lo prefieres):
   ```bash
   python manage.py migrate
   ```
6. Crea un superusuario:
   ```bash
   python manage.py createsuperuser
   ```
7. Inicia el servidor de desarrollo:
   ```bash
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage

Para utilizar la biblioteca, puedes extender los modelos y funcionalidades proporcionadas para crear aplicaciones SaaS personalizadas. A continuación se muestra un ejemplo básico de cómo integrar autenticación OAuth 2.0:

```python
from omnipro_solutions_saas_app_base.backends import CustomOAuth2Backend

# Configura el backend de autenticación en tu settings.py
AUTHENTICATION_BACKENDS = [
    'omnipro_solutions_saas_app_base.backends.CustomOAuth2Backend',
    # Otros backends...
]
```

Para más ejemplos, por favor refiérete a la [documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implementar caching para mejorar el rendimiento
- [ ] Desarrollar pruebas unitarias completas
- [ ] Soporte para múltiples bases de datos
  - [ ] Configuración avanzada de PostgreSQL

Ver los [issues abiertos](https://github.com/Omnipro-Solutions/saas-app-base/issues) para una lista completa de características propuestas (y problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Las contribuciones hacen que la comunidad de código abierto sea un lugar increíble para aprender, inspirarse y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "enhancement".
¡No olvides darle a este proyecto una estrella! ¡Gracias de nuevo!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a 'pull request'

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

Si tienes alguna pregunta o comentario, no dudes en contactar a través de [LinkedIn](https://www.linkedin.com/company/omni.pro/) o enviando un correo electrónico a `contact@omnipro.com`.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

- Agradecimientos especiales al equipo de Omnipro por su apoyo continuo.
- Inspiración y guía del [Django Documentation](https://docs.djangoproject.com/en/stable/).

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

[pic-python]: https://img.shields.io/badge/python-3.8+-blue.svg?style=flat-square&logo=python
[pic-django]: https://img.shields.io/badge/django-3.2-blue.svg?style=flat-square&logo=django
[pic-jazzmin]: https://img.shields.io/badge/jazzmin-0.4.1-green.svg?style=flat-square&logo=jazzmin
[pic-djangorestframework]: https://img.shields.io/badge/django_rest_framework-3.12.2-blue.svg?style=flat-square&logo=djangorestframework

[python-url]: https://www.python.org/
[django-url]: https://www.djangoproject.com/
[jazzmin-url]: https://github.com/app-generator/jazzmin
[djangorestframework-url]: https://www.django-rest-framework.org/