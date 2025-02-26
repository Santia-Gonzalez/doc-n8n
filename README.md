<a id="readme-top"></a>
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<br />
<div align="center">

<a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base.git">
    <img src="https://th.bing.com/th/id/OIP.ddlVF3lJNr9URRtdchRLcQHaHa?rs=1&pid=ImgDetMain" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Omnipro Solutions SaaS App Base</h3>

  <p align="center">
    Una biblioteca de Python diseñada para facilitar la creación de aplicaciones Django adaptadas a las necesidades del módulo base de Omnipro Solutions.
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
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

El repositorio `omnipro-solutions-saas-app-base` es una poderosa biblioteca de Python diseñada para facilitar la creación y gestión de aplicaciones Django específicamente adaptadas a las necesidades del módulo base de Omnipro Solutions. Su propósito principal es proporcionar un conjunto de funcionalidades predefinidas que pueden ser integradas en proyectos SaaS, permitiendo una rápida configuración y gestión de características comunes como autenticación, administración de usuarios, manejo de solicitudes HTTP, migraciones de base de datos, entre otras. Este repositorio está diseñado para acelerar el desarrollo de aplicaciones SaaS robustas utilizando Django.

### Built With

Este proyecto fue construido usando:

* [![Python][Python-logo]][Python-url]
* [![Django][Django-logo]][Django-url]
* [![Django REST Framework][DRF-logo]][DRF-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

Para configurar el proyecto en tu entorno local, sigue las siguientes instrucciones:

### Prerequisites

Antes de comenzar, asegúrate de tener instalado lo siguiente:

- Python 3.11 o superior
- Pip (gestor de paquetes de Python)

### Installation

1. Clona el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base.git
   cd omnipro-solutions-saas-app-base/
   ```

2. Crea un entorno virtual (opcional pero recomendado):
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows, usa `env\Scripts\activate`
   ```

3. Instala las dependencias:
   ```sh
   pip install -r requirements.txt
   ```

4. Configura tus variables de entorno creando un archivo `.env` en la raíz del proyecto y configurando las variables necesarias (por ejemplo, `SECRET_KEY`, URLs de base de datos, etc.).

5. Genera migraciones:
   ```sh
   python make_migrations.py
   ```

6. Ejecuta el servidor Django:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage

Para utilizar la biblioteca en tu proyecto, puedes seguir estos pasos:

1. Importa el módulo base de Omnipro Solutions en tu proyecto Django.
2. Integra las funcionalidades predefinidas como autenticación y administración de usuarios según sea necesario.
3. Configura tus rutas URL y vistas utilizando los archivos `urls.py` y `views.py` proporcionados.

Para más ejemplos, por favor refiérete a la [Documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Mejoras en seguridad, como protección contra CSRF y XSS.
- [ ] Soporte para otros sistemas de base de datos además de PostgreSQL.
- [ ] Documentación ampliada con ejemplos prácticos de uso.

Ver los [issues abiertos](#) para una lista completa de características propuestas (y problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Las contribuciones son lo que hacen que la comunidad de código abierto sea un lugar tan maravilloso para aprender, inspirar y crear. Cualquier contribución que hagas es **altamente apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "enhancement". ¡No olvides darle a este proyecto una estrella! Muchas gracias.

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

Distribuido bajo la Licencia MIT. Consulta `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Si tienes preguntas o necesitas soporte, por favor contacta a [email@omni.pro](mailto:email@omni.pro).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

- Gracias a toda la comunidad de Django y Python por su apoyo continuo.
- Agradecimientos especiales a [LinkedIn](https://www.linkedin.com/company/omni.pro/) por el soporte profesional.

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/network/members
[stars-shield]: https://img.shields.io/github/stars/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[stars-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/stargazers
[issues-shield]: https://img.shields.io/github/issues/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues
[license-shield]: https://img.shields.io/github/license/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[license-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/

[Python-logo]: https://www.python.org/static/img/python-logo.png
[Python-url]: https://www.python.org/
[Django-logo]: https://djangoproject.com/logos/django-logo-negative.svg
[Django-url]: https://www.djangoproject.com/
[DRF-logo]: https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png
[DRF-url]: https://www.django-rest-framework.org/