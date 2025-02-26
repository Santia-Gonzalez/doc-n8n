<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![Project License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base.git">
    <img src="https://th.bing.com/th/id/OIP.ddlVF3lJNr9URRtdchRLcQHaHa?rs=1&pid=ImgDetMain" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">omnipro-solutions-saas-app-base</h3>

  <p align="center">
    Biblioteca de módulos base para aplicaciones SaaS que se conectan al sistema Omni Management System (OMS).
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

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de módulos base diseñada para facilitar el desarrollo rápido y eficiente de aplicaciones SaaS que se conectan al sistema Omni Management System (OMS). Proporciona funcionalidades comunes, estructuras de código reutilizables y herramientas necesarias para microservicios dentro del ecosistema OMS. Las principales características incluyen autenticación, modelos extendidos de usuario, serialización, configuraciones de Django, gestión de migraciones y pruebas.

### Built With

* [![Django][Django]][Django-url]
* [![Python][Python]][Python-url]
* [![React][React.js]][React-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Prerequisites

Asegúrate de tener instaladas las siguientes dependencias:

- Python 3.8 o superior
- Pip (venv)
- Git

### Installation

1. Clona el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base.git
   cd omnipro-solutions-saas-app-base/
   ```
2. Crea un entorno virtual (opcional pero recomendado):
   ```bash
   python -m venv env
   source env/bin/activate  # En Windows usa `env\Scripts\activate`
   ```
3. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```
4. Configura variables de entorno:
   Crea un archivo `.env` en la raíz del proyecto y define las variables necesarias, como `SECRET_KEY`, `DATABASE_URL`, etc.
5. Ejecuta migraciones:
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```
6. Inicia el servidor de desarrollo (opcional):
   ```bash
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage

Para utilizar la biblioteca `omni_pro_base`, asegúrate de que tu proyecto Django esté configurado para incluir este módulo como una aplicación. Los modelos extendidos, las vistas y los serializadores están disponibles para ser utilizados en tus aplicaciones SaaS.

Consulta la [documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core) para más ejemplos y guías detalladas sobre cómo integrar esta biblioteca en tu proyecto.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Mejoras en la autenticación
- [ ] Integraciones adicionales con APIs externas
- [ ] Ampliación de las pruebas unitarias y de integración
    - [ ] Pruebas automatizadas para nuevos modelos

Ver los [issues abiertos](https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues) para una lista completa de características propuestas (y problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Las contribuciones son lo que hacen a la comunidad de código abierto un lugar tan increíble para aprender, inspirarse y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea un pull request. También puedes simplemente abrir un issue con la etiqueta "enhancement". No olvides darle a este proyecto una estrella. ¡Gracias de nuevo!

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

Distribuido bajo la licencia MIT. Ver `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
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

[Django]: https://img.shields.io/static/v1?label=Django&message=framework&color=092E20&logo=djangoproject&logoColor=white
[Django-url]: https://www.djangoproject.com/
[Python]: https://img.shields.io/badge/python-3.8-blue.svg
[Python-url]: https://www.python.org/downloads/release/python-380/
[React.js]: https://img.shields.io/static/v1?label=React&message=framework&color=61DAFB&logo=react&logoColor=white
[React-url]: https://reactjs.org/