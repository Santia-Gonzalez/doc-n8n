<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![Project License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<a href="https://github.com/Omnipro-Solutions/saas-app-base.git">
    <img src="https://th.bing.com/th/id/OIP.ddlVF3lJNr9URRtdchRLcQHaHa?rs=1&pid=ImgDetMain" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Omnipro Solutions SaaS App Base</h3>

  <p align="center">
    Una base sólida para la construcción de aplicaciones SaaS conectadas a OmniPro Solutions.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/Omnipro-Solutions/saas-app-base/issues">Report Bug</a>
    &middot;
    <a href="https://github.com/Omnipro-Solutions/saas-app-base/pulls">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de Contenidos</summary>
  <ol>
    <li>
      <a href="#sobre-el-proyecto">Acerca del Proyecto</a>
      <ul>
        <li><a href="#construido-con">Construido Con</a></li>
      </ul>
    </li>
    <li>
      <a href="#inicio-rápido">Inicio Rápido</a>
      <ul>
        <li><a href="#prerrequisitos">Prerrequisitos</a></li>
        <li><a href="#instalación">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#ejemplo-de-uso">Ejemplo de Uso</a></li>
    <li><a href="#planificación">Planificación</a></li>
    <li><a href="#colaborando">Colaborando</a></li>
    <li><a href="#licencia">Licencia</a></li>
    <li><a href="#contacto">Contacto</a></li>
    <li><a href="#reconocimientos">Reconocimientos</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## Acerca del Proyecto

El repositorio `omnipro-solutions-saas-app-base` está diseñado como una librería reutilizable para desarrollar aplicaciones SaaS conectadas a OmniPro Solutions. Este proyecto aprovecha Django para proporcionar funcionalidades avanzadas como autenticación, serialización de datos y APIs RESTful.

### Construido Con

Este repositorio hace uso de varias tecnologías destacadas:

* [![Python][python-logo]][python-url]
* [![Django][django-logo]][django-url]
* [![Django Rest Framework][drf-logo]][drf-url]
* [![PostgreSQL][postgresql-logo]][postgresql-url]

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

## Inicio Rápido

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Prerrequisitos

Asegúrate de tener instalado lo siguiente:

- Python 3.8 o superior
- Pip
- PostgreSQL

### Instalación

1. Clona el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```

2. Configura un entorno virtual (opcional pero recomendado):
   ```sh
   python -m venv venv
   source venv/bin/activate  # en Windows: venv\Scripts\activate
   ```

3. Instala las dependencias:
   ```sh
   pip install -r requirements.txt
   ```

4. Configura tus variables de entorno creando un archivo `.env` basado en `settings/base.py`, asegurándote de tener los valores correctos para tu entorno.

5. Crea y aplica las migraciones iniciales:
   ```sh
   python manage.py makemigrations
   python manage.py migrate
   ```

6. Inicia el servidor web de desarrollo:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

## Ejemplo de Uso

Para usar esta biblioteca como punto de partida para una aplicación SaaS, crea una nueva aplicación Django y configúrala para extender las funcionalidades ofrecidas por `omnipro-solutions-saas-app-base`. Consulta la documentación detallada en [Documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core) para más ejemplos de uso.

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

## Planificación

Actualmente, este proyecto se centra en proporcionar una base estable y modular. Aquí están las funcionalidades planificadas:

- Mejoras en la documentación para una integración más fácil.
- Implementación de pruebas unitarias e integración.
- Soporte para bases de datos multi-database.

Mira los [issues abiertos](https://github.com/Omnipro-Solutions/saas-app-base/issues) para una lista completa de características propuestas y problemas conocidos.

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

## Colaborando

Las contribuciones hacen que la comunidad de código abierto sea un lugar increíble para aprender, inspirar y crear. Cualquier contribución que hagas es **altamente apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repo y crea una solicitud de extracción. También puedes simplemente abrir un issue con la etiqueta "enhancement".
¡No olvides darle a este proyecto una estrella! ¡Gracias nuevamente!

1. Fork del Proyecto
2. Crea tu Rama de Característica (`git checkout -b feature/AmazingFeature`)
3. Comitea tus Cambios (`git commit -m 'Add some AmazingFeature'`)
4. Empuja a la Rama (`git push origin feature/AmazingFeature`)
5. Abre una "pull request"

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

### Top contributors:

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. Consulta `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/Omnipro-Solutions/saas-app-base/network/members
[issues-shield]: https://img.shields.io/github/issues/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/Omnipro-Solutions/saas-app-base/issues
[license-shield]: https://img.shields.io/github/license/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[license-url]: https://github.com/Omnipro-Solutions/saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/

<!-- LOGOS -->
[python-logo]: https://www.python.org/static/community_logos/python-powered-w-100x40.png
[python-url]: https://www.python.org/
[django-logo]: https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/Django.svg/1200px-Django.svg.png
[django-url]: https://www.djangoproject.com/
[drf-logo]: https://media.geeksforgeeks.org/wp-content/uploads/20190813151924/drfLogo.png
[drf-url]: https://www.django-rest-framework.org/
[postgresql-logo]: https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Postgresql_elephant.svg/200px-Postgresql_elephant.svg.png
[postgresql-url]: https://www.postgresql.org/


Esta plantilla se ha adaptado para ser profesional y clara, incluyendo las especificaciones solicitadas. Las partes marcadas como `EJEMPLOS:` en la solicitud original han sido reemplazadas con los detalles específicos de esta biblioteca Django SaaS.
