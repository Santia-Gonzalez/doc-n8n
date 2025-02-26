<a id="readme-top"></a>
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<a href="https://github.com/Omnipro-Solutions/saas-app-base.git">
    <img src="https://pngimg.com/uploads/github/github_PNG78.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">saas-app-base</h3>

  <p align="center">
    Biblioteca base para aplicaciones Django en el ecosistema de Omnipro Solutions
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Documentación oficial »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/Omnipro-Solutions/saas-app-base/issues/bug">Reportar errores</a>
    &middot;
    <a href="https://github.com/Omnipro-Solutions/saas-app-base/issues/features">Solicitar mejoras</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de contenido</summary>
  <ol>
    <li>
      <a href="#about-the-project">Sobre el proyecto</a>
      <ul>
        <li><a href="#built-with">Stack</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Comenzando</a>
      <ul>
        <li><a href="#prerequisites">Prerequisitos</a></li>
        <li><a href="#installation">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#usage">Uso</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contribuindo</a></li>
    <li><a href="#license">Licencia</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

El repositorio `saas-app-base` es una biblioteca de Python diseñada para ser un módulo base en aplicaciones Django que se conectan a Omnipro Solutions. Proporciona funcionalidades comunes y configuraciones necesarias para desarrollar aplicaciones SaaS dentro del ecosistema de Omnipro. Las características principales incluyen autenticación, modelos de usuario personalizados, serialización y gestión de datos, configuración modular, y una integración fluida con los servicios externos de Omnipro.

### Built With

* [![Python][Python]][Python-url]
* [![Django][Django]][Django-url]
* [![Django REST Framework][DRF]][DRF-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Prerequisites

- Python 3.11 o superior
- Django 5.0
- Dependencias listadas en `requirements.txt`

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/
   ```

2. Create a virtual environment (Opcional)
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: .\env\Scripts\activate
   ```

3. Install dependencies
   ```sh
   pip install -r requirements.txt
   ```

4. Configure environment variables
   Crea un archivo `.env` en la raíz del proyecto y define las variables necesarias, como `SECRET_KEY`, `DATABASE_URL`, etc.

5. Generate and apply migrations
   ```sh
   python make_migrations.py
   python manage.py migrate
   ```

6. Run the development server
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage

Para utilizar la biblioteca, asegúrate de haber seguido los pasos de instalación. Puedes explorar el uso del módulo en la [documentación oficial](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implementar cache
- [ ] Mejoras en seguridad
- [ ] Ampliar documentación interna
- [ ] Implementar pruebas automatizadas
- [ ] Optimización de rendimiento

Ver los [issues abiertos](https://github.com/Omnipro-Solutions/saas-app-base/issues) para una lista completa de características propuestas (y problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Las contribuciones hacen que la comunidad de código abierto sea un lugar increíble para aprender, inspirarse y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea un pull request. También puedes simplemente abrir un issue con la etiqueta "enhancement". No olvides darle al proyecto una estrella! Gracias de nuevo!

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

Distribuido bajo la Licencia MIT. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

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

[Python]: https://img.shields.io/badge/python-grey?style=for-the-badge&logo=python
[Python-url]: https://www.python.org/
[Django]: https://img.shields.io/badge/django-grey?style=for-the-badge&logo=django
[Django-url]: https://www.djangoproject.com/
[DRF]: https://img.shields.io/badge/DRF-grey?style=for-the-badge&logo=djangorestframework
[DRF-url]: https://www.django-rest-framework.org/