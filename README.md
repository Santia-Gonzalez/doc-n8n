<a id="readme-top"></a>
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<br />
<div align="center">

<a
href="https://github.com/omnipro-solutions/saas-app-base.git">
    <img src="https://img.shields.io/badge/OmniPro-grey?style=for-the-badge&logo=github" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">saas-app-base</h3>

  <p align="center">
    Biblioteca de módulos base para aplicaciones SaaS conectadas a Omnipro Solutions.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Documentación oficial »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-base/issues">Reportar errores</a>
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-base/issues">Solicitar mejoras</a>
  </p>
</div>

<details>
  <summary>Tabla de contenido</summary>
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
  </ol>
</details>

## About The Project

El repositorio `saas-app-base` es una biblioteca de módulos base para aplicaciones SaaS conectadas a Omnipro Solutions. Proporciona funcionalidades comunes que pueden ser utilizadas por diversas aplicaciones desarrolladas bajo la plataforma Omnipro, incluyendo autenticación y autorización, modelos base, serializadores, administración personalizada con Django Admin y configuraciones dinámicas para diferentes entornos.

### Built With

Este proyecto está construido utilizando las siguientes tecnologías:

* [![Python][Python]][Python-url]
* [![Django][Django]][Django-url]
* [![Jazzmin][Jazzmin]][Jazzmin-url]
* [![Django REST Framework][DRF]][DRF-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Getting Started

A continuación, se presentan las instrucciones para configurar el proyecto en tu entorno local.

### Prerequisites

Antes de comenzar, asegúrate de tener instalado:

* Python 3.11 o superior
* Pip (gestor de paquetes de Python)
* Git

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-base.git
   cd saas-app-base/
   ```

2. Create a virtual environment and activate it:
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: .\env\Scripts\activate
   ```

3. Install dependencies
   ```sh
   pip install -r requirements.txt
   ```

4. Configure your environment variables by creating a `.env` file in the root directory and defining necessary variables like `SECRET_KEY`, `DATABASE_URL`, etc.

5. Generate migrations and create the database:
   ```sh
   python make_migrations.py
   python manage.py migrate
   ```

6. Run the development server:
   ```sh
   python manage.py runserver
   ```

7. Access the admin interface by navigating to `http://localhost:8000/admin/` in your browser.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Usage

Para utilizar la biblioteca, puedes extender los modelos base y configurar las vistas utilizando Django REST Framework para exponer endpoints API. Los serializadores facilitan la conversión de objetos del modelo a formatos JSON para las respuestas HTTP.

_For more examples, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Roadmap

- [ ] Implementación del caché
- [ ] Pruebas unitarias
- [ ] Documentación adicional y ejemplos de uso
- [ ] Mejoras en la seguridad para entornos de producción

See the [open issues](https://github.com/omnipro-solutions/saas-app-base/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contributing

Contribuciones son lo que hacen a la comunidad de código abierto un lugar tan increíble para aprender, inspirar y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "mejora".
¡No olvides darle a este proyecto una estrella! ¡Gracias nuevamente!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a pull request

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top contributors:

<a href="https://github.com/omnipro-solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=omnipro-solutions/saas-app-base" alt="contrib.rocks image" />
</a>

## License

Distribuido bajo la licencia MIT. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/omnipro-solutions/saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/omnipro-solutions/saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/omnipro-solutions/saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/omnipro-solutions/saas-app-base/network/members
[stars-shield]: https://img.shields.io/github/stars/omnipro-solutions/saas-app-base.svg?style=for-the-badge
[stars-url]: https://github.com/omnipro-solutions/saas-app-base/stargazers
[issues-shield]: https://img.shields.io/github/issues/omnipro-solutions/saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/omnipro-solutions/saas-app-base/issues
[license-shield]: https://img.shields.io/github/license/omnipro-solutions/saas-app-base.svg?style=for-the-badge
[license-url]: https://github.com/omnipro-solutions/saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/

<!-- TECHNOLOGY BADGES -->
[Python]: https://img.shields.io/badge/with%20a%20logo-grey?style=for-the-badge&logo=python
[Python-url]: https://www.python.org/
[Django]: https://img.shields.io/badge/with%20a%20logo-grey?style=for-the-badge&logo=djangoproject
[Django-url]: https://www.djangoproject.com/
[Jazzmin]: https://img.shields.io/badge/with%20a%20logo-grey?style=for-the-badge&logo=jazzmin
[Jazzmin-url]: https://jazzband.co/projects/jazzmin/
[DRF]: https://img.shields.io/badge/with%20a%20logo-grey?style=for-the-badge&logo=djangorestframework
[DRF-url]: https://www.django-rest-framework.org/