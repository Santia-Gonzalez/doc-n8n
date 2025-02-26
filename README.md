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

<h3 align="center">Biblioteca de Aplicaciones SaaS Base para Django</h3>

  <p align="center">
    Una base robusta y configurable para el desarrollo de aplicaciones SaaS con Django.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues">Report Bug</a>
    &middot;
    <a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/pullrequest">Request Feature</a>
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

La biblioteca `omnipro-solutions-saas-app-base` está diseñada para servir como una base sólida y flexible en proyectos Django, enfocándose específicamente en soluciones de Software as a Service (SaaS) gestionadas por OMNI.PRO. Proporciona funcionalidades comunes y configuraciones estándar que pueden ser reutilizadas en múltiples proyectos SaaS.

### Funciones Principales

- **Autenticación:** Soporta varios métodos de autenticación, incluyendo contraseñas del sistema y servicios externos.
- **Gestión de Usuarios:** Ofrece modelos extendidos con campos adicionales como `created_by` y `updated_by`.
- **Serialización RESTful:** Incluye serializadores para la gestión de datos de usuario y grupos en APIs RESTful.
- **Configuraciones de Django:** Proporciona configuraciones estándar para proyectos Django, incluyendo middleware, aplicaciones instaladas y ajustes de seguridad.
- **Integración con Celery:** Configura tareas asíncronas utilizando el sistema de colas Celery.

### Built With

* [![Python][Python]][Python-url]
* [![Django][Django]][Django-url]
* [![Celery][Celery]][Celery-url]
* [![Redis][Redis]][Redis-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

A continuación se presentan las instrucciones para configurar el proyecto en tu entorno local.

### Prerequisites

- Python 3.11 o superior
- Django 5.0
- Redis instalado y ejecutándose (para Celery)

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base.git
   cd omnipro-solutions-saas-app-base/
   ```
2. Create a virtual environment and activate it:
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: env\Scripts\activate
   ```
3. Install dependencies
   ```sh
   pip install -r requirements.txt
   ```
4. Configure the environment variables by creating a `.env` file in the project root and defining necessary variables like `SECRET_KEY`, `DATABASE_URL`.

5. Generate database migrations:
   ```sh
   python make_migrations.py
   ```

6. Run the development server:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage

Para utilizar la biblioteca en tu proyecto Django, asegúrate de incluir `omni_pro_base` en las aplicaciones instaladas y configurar los ajustes necesarios. Puedes referirte a la [documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core) para ejemplos más detallados.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implementación del sistema de caché con Redis
- [ ] Expandir las pruebas unitarias y funcionales
- [ ] Mejoras en el sistema de autenticación, como autenticación multifactor

See the [open issues](https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Contribuciones son lo que hacen que la comunidad de código abierto sea un lugar tan maravilloso para aprender, inspirarse y crear. Cualquier contribución que hagas es **altamente apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea un pull request. También puedes simplemente abrir un problema con la etiqueta "enhancement".
¡No olvides darle al proyecto una estrella! ¡Gracias de nuevo!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a 'pull request'

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top contributors:

<a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/omnipro-solutions-saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## License

Distribuido bajo la licencia MIT. Consulta `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Para consultas o colaboraciones, contacta a:

- **Correo Electrónico:** [email@omni.pro](mailto:email@omni.pro)
- **LinkedIn:** [linkedin.com/in/omni-pro](https://www.linkedin.com/company/omni.pro)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

Gracias a todos los colaboradores y usuarios que han contribuido al desarrollo de esta biblioteca. Tu soporte es invaluable.

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/network/members
[issues-shield]: https://img.shields.io/github/issues/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues
[license-shield]: https://img.shields.io/github/license/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[license-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/
[Python]: https://img.shields.io/badge/-Python-3776AB?style=flat-square&logo=python&logoColor=white
[Python-url]: https://www.python.org/
[Django]: https://img.shields.io/badge/-Django-092E20?style=flat-square&logo=djangoproject&logoColor=white
[Django-url]: https://www.djangoproject.com/
[Celery]: https://img.shields.io/badge/-Celery-3776AB?style=flat-square&logo=celery&logoColor=white
[Celery-url]: http://www.celeryproject.org/
[Redis]: https://img.shields.io/badge/-Redis-DC382D?style=flat-square&logo=redis&logoColor=white
[Redis-url]: https://redis.io/