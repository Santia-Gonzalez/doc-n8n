# Documentación del Repositorio `omnipro-solutions-saas-app-base`

<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![Project License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<a href="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDI0IiBoZWlnaHQ9IjEwMjQiIHZpZXdCb3g9IjAgMCAxMDI0IDEwMjQiPjxwYXRoIGZpbGw9ImN1cnJlbnRDb2xvciIgZD0iTTYyOC43MzYgNTI4Ljg5NkE0MTYgNDE2IDAgMCAxIDkyOCA5MjhIOTZhNDE1Ljg3IDQxNS44NyAwIDAgMSAyOTkuMjY0LTM5OS4xMDRMNTEyIDcwNHpNNzIwIDMwNGEyMDggMjA4IDAgMSAxLTQxNiAwYTIwOCAyMDggMCAwIDEgNDE2IDAiLz48L3N2Zz4=">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Biblioteca de Módulos Base para Aplicaciones SaaS en Django</h3>

  <p align="center">
    Una biblioteca de módulos base diseñada para facilitar el desarrollo de aplicaciones SaaS conectadas a Omnipro Solutions.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explora la documentación »</strong></a>
    <br />
    <br />
    &middot;
    <a href="#">Reportar Error</a>
    &middot;
    <a href="#">Solicitar Característica</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de Contenidos</summary>
  <ol>
    <li>
      <a href="#about-the-project">Acerca del Proyecto</a>
      <ul>
        <li><a href="#built-with">Construido con</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Comenzando</a>
      <ul>
        <li><a href="#prerequisites">Prerrequisitos</a></li>
        <li><a href="#installation">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#usage">Uso</a></li>
    <li><a href="#roadmap">Ruta de Desarrollo</a></li>
    <li><a href="#contributing">Contribuyendo</a></li>
    <li><a href="#license">Licencia</a></li>
    <li><a href="#contact">Contacto</a></li>
    <li><a href="#acknowledgments">Agradecimientos</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## Acerca del Proyecto

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca integral de módulos base diseñada para ser utilizada en aplicaciones Django que se conectan a Omnipro Solutions. Su propósito principal es proporcionar funcionalidades comunes y configuraciones estándar, simplificando el desarrollo de aplicaciones SaaS basadas en la plataforma de Omnipro. Entre sus principales características están:

- **Autenticación**: Implementa mecanismos robustos tanto a nivel de configuración como mediante un servicio externo.
- **Modelos Personalizados**: Extiende el modelo `User` de Django para adaptarse mejor a las necesidades específicas del sistema, incluyendo campos adicionales como `created_by`, `updated_by` y `is_active`.
- **Serialización y Vistas REST**: Facilita la creación de APIs RESTful utilizando serializers personalizados y viewsets.
- **Configuraciones Base**: Ofrece configuraciones base para entornos de desarrollo, producción y local.
- **Interfaz Administrativa Mejorada**: Integra el tema `jazzmin` para una interfaz administrativa mejorada.
- **Gestión de Migraciones**: Incluye herramientas para generar migraciones automáticamente.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Construido con

* [![Django][Django]][Django-url]
* [![React][React.js]][React-url]
* [![Vue][Vue.js]][Vue-url]
* [![Angular][Angular.io]][Angular-url]
* [![Svelte][Svelte.dev]][Svelte-url]
* [![Laravel][Laravel.com]][Laravel-url]
* [![Bootstrap][Bootstrap.com]][Bootstrap-url]
* [![JQuery][JQuery.com]][JQuery-url]

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- GETTING STARTED -->
## Comenzando

Esta es una guía de ejemplo sobre cómo configurar tu proyecto localmente. Sigue estos pasos simples para tener un entorno funcional:

### Prerrequisitos

Para utilizar este software, necesitarás lo siguiente:

- Python 3.x
- Pip instalado en tu sistema
- Un editor de código como VSCode o PyCharm

### Instalación

1. Clona el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```

2. Crea un entorno virtual (Opcional):
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows, usa `env\Scripts\activate`
   ```

3. Instala las dependencias:
   ```sh
   pip install -r requirements.txt
   ```

4. Configura las variables de entorno asegurándote de que el archivo `.env` esté configurado con las variables necesarias como `SECRET_KEY`, `DATABASE_URL`, etc.

5. Crea la base de datos:
   ```sh
   python manage.py migrate
   ```

6. Ejecuta el servidor de desarrollo:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- USAGE EXAMPLES -->
## Uso

Aquí tienes un ejemplo sencillo sobre cómo utilizar esta biblioteca o explicaciones detalladas de su uso. Este espacio es ideal para mostrar ejemplos útiles de cómo se puede usar el proyecto, con capturas adicionales, ejemplos de código y demos.

Para más ejemplos, por favor refiérase a la [Documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- ROADMAP -->
## Ruta de Desarrollo

- [ ] Implementación de Caché
- [ ] Pruebas Unitarias
- [ ] Configuración Avanzada de Celery
  - [ ] Manejo avanzado de colas
- [ ] Mejoras en Seguridad para el entorno de producción

Consulte los [problemas abiertos](#) para una lista completa de características propuestas (y problemas conocidos).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Las contribuciones hacen que la comunidad de código abierto sea un lugar maravilloso para aprender, inspirar y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea un pull request. También puedes simplemente abrir un problema con la etiqueta "mejora". ¡No olvides darle al proyecto una estrella! Gracias de nuevo!

1. Fork del Proyecto
2. Crea tu Rama de Característica (`git checkout -b feature/AmazingFeature`)
3. Realiza tus Cambios (`git commit -m 'Añadir AmazingFeature'`)
4. Empuja a la Rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Principales Contribuidores:

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. Consulta el archivo `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

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

[Django]: https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=djangoproject&logoColor=white
[Django-url]: https://www.djangoproject.com/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vue.js]: https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white
[Vue-url]: https://vuejs.org/
[Angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[Angular-url]: https://angular.io/
[Svelte.dev]: https://img.shields.io/badge/Svelte-333333?style=for-the-badge&logo=svelte&logoColor=E39400
[Svelte-url]: https://svelte.dev/
[Laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[Laravel-url]: https://laravel.com/
[Bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[Bootstrap-url]: https://getbootstrap.com/
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com/