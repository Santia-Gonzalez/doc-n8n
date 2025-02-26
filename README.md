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
href="https://github.com/github_username/repo_name.git">
    <img src="https://th.bing.com/th/id/OIP.ddlVF3lJNr9URRtdchRLcQHaHa?rs=1&pid=ImgDetMain" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">saas-app-oms</h3>

  <p align="center">
    Repositorio base para aplicaciones SaaS en Django conectadas a Omnipro Solutions.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explore la documentación »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/github_username/issues/repo_name.git">Reportar un error</a>
    &middot;
    <a href="https://github.com/github_username/pullrequest/repo_name.git">Solicitar una característica</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de Contenidos</summary>
  <ol>
    <li>
      <a href="#about-the-project">Acerca del Proyecto</a>
      <ul>
        <li><a href="#built-with">Desarrollado con</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Empezando</a>
      <ul>
        <li><a href="#prerequisites">Requisitos previos</a></li>
        <li><a href="#installation">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#usage">Uso</a></li>
    <li><a href="#roadmap">Ruta del proyecto</a></li>
    <li><a href="#contributing">Contribuyendo</a></li>
    <li><a href="#license">Licencia</a></li>
    <li><a href="#contact">Contacto</a></li>
    <li><a href="#acknowledgments">Agradecimientos</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## Acerca del Proyecto

El repositorio `saas-app-oms` es una librería diseñada para ser el módulo base de aplicaciones Django que se conectan a Omnipro Solutions. Su propósito principal es proporcionar las funcionalidades básicas necesarias para construir aplicaciones SaaS (Software as a Service) dentro del ecosistema de Omnipro. Las funcionalidades principales incluyen autenticación y autorización, gestión de usuarios y grupos, configuraciones dinámicas y soporte para tareas asincrónicas mediante Celery.

### Built With

* [![Django][Django]][Django-url]
* [![Python][Python]][Python-url]
* [![Celery][Celery]][Celery-url]

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- GETTING STARTED -->
## Empezando

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Prerequisites

- Python 3.11 o superior
- Django 5.0
- Dependencias listadas en `requirements.txt`

### Installation

1. Clona el repositorio
   ```sh
   git clone https://github.com/github_username/repo_name.git
   ```
2. Instala las dependencias necesarias
   ```sh
   pip install -r requirements.txt
   ```
3. Configura tus variables de entorno copiando `local.py` a `settings/local.py`.
4. Crea la base de datos ejecutando:
   ```sh
   python manage.py migrate
   ```

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- USAGE EXAMPLES -->
## Uso

Para un ejemplo práctico de cómo utilizar esta biblioteca, consulta la [documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- ROADMAP -->
## Ruta del proyecto

- [ ] Mejora en el manejo de caché
- [ ] Implementación de pruebas unitarias
- [ ] Refinamiento de configuraciones de seguridad

Para ver la lista completa de características propuestas (y problemas conocidos), revisa los [issues abiertos](#).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Las contribuciones son lo que hacen a la comunidad de código abierto un lugar tan maravilloso para aprender, inspirarse y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "mejora".
¡No olvides darle al proyecto una estrella! Gracias de nuevo!

1. Fork del Proyecto
2. Crea tu rama de característica (`git checkout -b feature/AmazingFeature`)
3. Comita tus Cambios (`git commit -m 'Add some AmazingFeature'`)
4. Empuja a la Rama (`git push origin feature/AmazingFeature`)
5. Abre una Solicitud de Extracción

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Top contributors:

<a href="https://github.com/github_username/repo_name/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=github_username/repo_name" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. Consulta `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/github_username/repo_name.svg?style=for-the-badge
[contributors-url]: https://github.com/github_username/repo_name/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[stars-shield]: https://img.shields.io/github/stars/github_username/repo_name.svg?style=for-the-badge
[stars-url]: https://github.com/github_username/repo_name/stargazers
[issues-shield]: https://img.shields.io/github/issues/github_username/repo_name.svg?style=for-the-badge
[issues-url]: https://github.com/github_username/repo_name/issues
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/
[Django]: https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white
[Django-url]: https://www.djangoproject.com/
[Python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[Python-url]: https://www.python.org/
[Celery]: https://img.shields.io/badge/Celery-79D8FF?style=for-the-badge&logo=celery&logoColor=black
[Celery-url]: http://www.celeryproject.org/
```

Este documento proporciona una guía completa y profesional para el repositorio `saas-app-oms`, incluyendo información sobre su propósito, estructura, dependencias y cómo contribuir.
