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

<h3 align="center">Base de Aplicaciones SaaS para Omni-Solutions</h3>

  <p align="center">
    Base de código diseñada para aplicaciones Software as a Service (SaaS) que se conectan al sistema OMS.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explore la documentación »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues">Reportar Error</a>
    &middot;
    <a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/pullrequest">Solicitar Característica</a>
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
      <a href="#getting-started">Inicio Rápido</a>
      <ul>
        <li><a href="#prerequisites">Requisitos Previos</a></li>
        <li><a href="#installation">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#usage">Uso</a></li>
    <li><a href="#roadmap">Plan de Ruta</a></li>
    <li><a href="#contributing">Contribuyendo</a></li>
    <li><a href="#license">Licencia</a></li>
    <li><a href="#contact">Contacto</a></li>
    <li><a href="#acknowledgments">Agradecimientos</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## Acerca del Proyecto

El repositorio `omnipro-solutions-saas-app-base` proporciona una base de código modular para aplicaciones SaaS que se conectan con el sistema OMS. Está construido sobre Django y ofrece funcionalidades esenciales como gestión de usuarios, autenticación personalizada, integración con librerías de terceros, y más.

La solución permite a los desarrolladores centrarse en la creación de características específicas del negocio sin tener que reinventar las ruedas. Esta base de código asegura estándares consistentes y reduce significativamente el tiempo de desarrollo para aplicaciones SaaS en el ecosistema Omni-Solutions.

### Desarrollado con

* [![Django][Django.js]][Django-url]
* [![Python][Python.org]][Python-url]

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- GETTING STARTED -->
## Inicio Rápido

A continuación se describen las instrucciones para configurar el proyecto en tu entorno local.

### Requisitos Previos

Para ejecutar este repositorio, asegúrate de tener instalados:

* Python 3.11 o superior
* Django 5.0
* Otros paquetes listados en `requirements.txt`

### Instalación

1. Clona el repositorio
   ```sh
   git clone https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base.git
   ```
2. Navega al directorio del proyecto
   ```sh
   cd omnipro-solutions-saas-app-base
   ```
3. Instala las dependencias necesarias
   ```sh
   pip install -r requirements.txt
   ```
4. Crea las migraciones y actualiza la base de datos
   ```sh
   python manage.py makemigrations
   python manage.py migrate
   ```
5. Corre el servidor (en desarrollo)
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- USAGE EXAMPLES -->
## Uso

Para utilizar la biblioteca en tus propios proyectos SaaS, puedes comenzar a integrar los módulos específicos de usuario y autenticación. Asegúrate de revisar las configuraciones de entorno para personalizar los parámetros según tu caso particular.

_**Nota:** Para más ejemplos, consulta la [Documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- ROADMAP -->
## Plan de Ruta

- [ ] Integrar autenticación basada en API Keys
- [ ] Mejorar la interfaz del administrador de Django
- [ ] Añadir soporte multi-bilingüe
    - [ ] Traducciones automáticas para mensajes

Verifica los [problemas abiertos](https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues) para una lista completa de características propuestas (y problemas conocidos).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Las contribuciones son lo que hace tan maravilloso al mundo del software libre. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea un pull request. También puedes simplemente abrir un problema con la etiqueta "mejora".
No olvides darle al proyecto una estrella. ¡Gracias de nuevo!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a 'pull request'

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Top contributors:

<a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/omnipro-solutions-saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. Consulta el archivo `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/network/members
[stars-shield]: https://img.shields.io/github/stars/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[stars-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/stargazers
[issues-shield]: https://img.shields.io/github/issues/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues
[license-shield]: https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge
[license-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/

[Django.js]: https://img.shields.io/badge/Django-092E20?style=flat-square&logo=djangoproject&logoColor=white
[Django-url]: https://djangoproject.com/
[Python.org]: https://img.shields.io/badge/Python-FFD43B?style=for-the-badge&logo=python&logoColor=darkgreen
[Python-url]: https://www.python.org/