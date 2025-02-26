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
href="https://github.com/omnipro-solutions/saas-app-base.git">
    <img src="https://img.shields.io/badge/with%20a%20logo-grey?style=for-the-badge&logo=django" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Omnipro Solutions SaaS App Base</h3>

  <p align="center">
    Biblioteca de Python para aplicaciones Django conectadas a Omni Management System (OMS).
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-base/issues">Report Bug</a>
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-base/pullrequest">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
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

<!-- ABOUT THE PROJECT -->
## About The Project

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de Python diseñada para ser utilizada en aplicaciones Django, específicamente como un módulo base para la conexión con Omni Management System (OMS). Esta biblioteca proporciona funcionalidades clave que facilitan el desarrollo y mantenimiento de aplicaciones robustas. Algunas de las principales características incluyen:

- **Autenticación Personalizada**: Implementación de backends de autenticación personalizados para gestionar usuarios.
- **Gestión de Usuarios y Grupos**: API RESTful para la visualización, edición y creación de usuarios y grupos.
- **Serialización de Datos**: Utiliza serializers para convertir objetos del modelo a formatos JSON y viceversa.
- **Configuraciones Extendidas**: Ofrece configuraciones detalladas para diferentes entornos (base, local, producción).
- **Integración con Celery**: Configura tareas asincrónicas utilizando Celery para mejorar el rendimiento de la aplicación.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built With

Este proyecto fue desarrollado utilizando las siguientes tecnologías:

* [![Python][Python]][Python-url]
* [![Django][Django]][Django-url]
* [![Celery][Celery]][Celery-url]
* [![Redis][Redis]][Redis-url]
* [![PostgreSQL][PostgreSQL]][PostgreSQL-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

A continuación se presentan las instrucciones para configurar el proyecto en tu entorno local.

### Prerequisites

Antes de comenzar, asegúrate de tener instalado lo siguiente:

- Python (versión 3.8 o superior)
- Pip
- PostgreSQL
- Redis

### Installation

1. Clonar el repositorio:
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-base.git
   ```
2. Navegar al directorio del proyecto:
   ```bash
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```
3. Crear un entorno virtual (opcional pero recomendado):
   ```bash
   python -m venv env
   source env/bin/activate  # En Windows: env\Scripts\activate
   ```
4. Instalar las dependencias:
   ```bash
   pip install -r requirements.txt
   ```
5. Configurar variables de entorno según el archivo `settings.py` o crear un `.env`.
6. Generar migraciones y aplicarlas:
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage

Para utilizar esta biblioteca en tu proyecto Django, sigue estos pasos:

1. Agrega `omni_pro_base` a la lista de `INSTALLED_APPS` en tu archivo `settings.py`.
2. Configura las variables de entorno necesarias para la autenticación y conexión con OMS.
3. Utiliza los serializers y vistas proporcionados para gestionar usuarios y grupos.

Para más ejemplos, por favor consulta la [Documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Mejora de la documentación interna
- [ ] Implementación de caché para optimizar el rendimiento
- [ ] Desarrollo de pruebas unitarias para asegurar la calidad del código
    - [ ] Pruebas de autenticación
    - [ ] Pruebas de serialización

Ver los [issues abiertos](https://github.com/omnipro-solutions/saas-app-base/issues) para una lista completa de características propuestas (y problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Las contribuciones son lo que hacen a la comunidad de código abierto un lugar tan maravilloso para aprender, inspirar y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "mejora".
¡No olvides darle al proyecto una estrella! ¡Gracias de nuevo!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a 'pull request'

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top contributors:

<a href="https://github.com/omnipro-solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=omnipro-solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## License

Distribuido bajo la licencia MIT. Ver `LICENSE.txt` para más información.

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

<!-- BADGES -->
[Python]: https://img.shields.io/badge/-Python-3776AB?style=flat-square&logo=python&logoColor=white
[Python-url]: https://www.python.org/
[Django]: https://img.shields.io/badge/-Django-092E20?style=flat-square&logo=Django&logoColor=white
[Django-url]: https://www.djangoproject.com/
[Celery]: https://img.shields.io/badge/-Celery-3776AB?style=flat-square&logo=Celery&logoColor=white
[Celery-url]: http://www.celeryproject.org/
[Redis]: https://img.shields.io/badge/-Redis-DC382D?style=flat-square&logo=redis&logoColor=white
[Redis-url]: https://redis.io/
[PostgreSQL]: https://img.shields.io/badge/-PostgreSQL-336791?style=flat-square&logo=postgresql&logoColor=white
[PostgreSQL-url]: https://www.postgresql.org/