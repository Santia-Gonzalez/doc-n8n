<a id="readme-top"></a>
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![PR][pull-request-shield]][pull-request-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<a href="https://github.com/omnipro-solutions/saas-app-core.git">
    <img src="https://pngimg.com/uploads/github/github_PNG78.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">saas-app-core</h3>

  <p align="center">
    Gestión robusta de operaciones y tareas en un entorno multiinquilino utilizando Django, DRF, Celery y PostgreSQL.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Documentación oficial »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-core/issues">Reportar errores</a>
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-core/issues">Solicitar mejoras</a>
  </p>
</div>

<!-- TABLA DE CONTENIDO -->
<details>
  <summary>Tabla de contenido</summary>
  <ol>
    <li>
      <a href="#descripción">Descripción</a>
      <ul>
        <li><a href="#stack-tecnológico">Stack</a></li>
      </ul>
    </li>
    <li>
      <a href="#comenzando">Comenzando</a>
      <ul>
        <li><a href="#prerequisitos">Prerequisitos</a></li>
        <li><a href="#instalacion">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#usao">Uso</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contribuyendo">Contribuyendo</a></li>
    <li><a href="#top-contribuyentes">Top Contribuyentes</a></li>
    <li><a href="#licencia">Licencia</a></li>
  </ol>
</details>

<!-- SOBRE EL PROYECTO -->
## Descripción

**saas-app-core** es un proyecto de gestión integral para operaciones y tareas diseñado para entornos multiinquilinos. Utiliza Django como marco principal, facilitando la creación de modelos ORM robustos para gestionar configuraciones, operaciones, tipos de operaciones, tareas y detalles de inquilinos. La integración con el framework RESTful de Django (DRF) permite exponer una API REST completa que soporta operaciones CRUD sobre estos modelos.

El proyecto también incorpora Celery para procesamiento asíncrono de tareas, asegurando un manejo eficiente y escalable de cargas de trabajo. Las características clave incluyen la gestión de tokens, el seguimiento del estado de las tareas y notificaciones por correo electrónico cuando cambia el estado de una tarea.

### Stack tecnológico

* [![Django][Django]][Django-url]
* [![DRF][drf]][drf-url]
* [![PostgreSQL][postgresql]][postgresql-url]
* [![Celery][celery]][celery-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Comenzando

Para configurar el proyecto en tu entorno local, sigue los pasos detallados a continuación.

### Prerequisitos

Asegúrate de tener instalado:

- Python 3.8 o superior
- PostgreSQL
- Redis (para Celery)
- Git

### Instalación

1. Clona el repositorio:
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-core.git
   ```
2. Navega al directorio del proyecto:
   ```sh
   cd saas-app-core
   ```
3. Crea un entorno virtual y activalo (para Windows):
   ```sh
   python -m venv env
   .\env\Scripts\activate
   ```
   O para macOS/Linux:
   ```sh
   python3 -m venv env
   source env/bin/activate
   ```
4. Instala las dependencias de Python:
   ```sh
   pip install -r requirements.txt
   ```
5. Configura tu base de datos PostgreSQL y actualiza `settings.py` con tus credenciales.
6. Ejecuta migraciones para crear la estructura de la base de datos:
   ```sh
   python manage.py migrate
   ```
7. Inicia el servidor local:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Una vez que tu entorno esté configurado, puedes comenzar a utilizar el proyecto para gestionar operaciones y tareas. Aquí hay un ejemplo básico:

1. Accede al servidor local en `http://127.0.0.1:8000`.
2. Utiliza la API REST proporcionada por DRF para crear nuevas operaciones o tareas.
3. Monitorea el estado de las tareas a través del panel administrativo de Django.

Para más ejemplos, consulta la [Documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Mejoras en el manejo de tokens
- [ ] Integración con servicios externos
- [ ] Optimización del rendimiento
    - [ ] Caché avanzado para consultas frecuentes

Mira las [ISSUES](https://github.com/omnipro-solutions/saas-app-core/issues) para una lista completa de mejoras (problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUYENDO -->
## Contribuyendo

Las contribuciones son lo que hace que la comunidad de código abierto sea un lugar increíble para aprender, inspirar y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que mejoraría este proyecto, "fork" el repositorio y crea una solicitud de pull request. También puedes simplemente abrir un problema con la etiqueta "mejora".
¡No te olvides de darle una estrella al proyecto! ¡Gracias de nuevo!

1. "Fork" el Proyecto
2. Crea tu rama "Feature" (`git checkout -b feature/AmazingFeature`)
3. Realiza un "commit" a tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. "Push" a tus cambios locales a la rama remota (`git push origin feature/AmazingFeature`)
5. Inicia una 'pull request'

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top Contribuyentes:

<a href="https://github.com/omnipro-solutions/saas-app-core/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=omnipro-solutions/saas-app-core" alt="contrib.rocks image" />
</a>

<!-- LICENCIA -->
## Licencia

Distribuido bajo la licencia MIT. Ve a `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/omnipro-solutions/saas-app-core.svg?style=for-the-badge
[contributors-url]: https://github.com/omnipro-solutions/saas-app-core/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/omnipro-solutions/saas-app-core.svg?style=for-the-badge
[forks-url]: https://github.com/omnipro-solutions/saas-app-core/network/members
[stars-shield]: https://img.shields.io/github/stars/omnipro-solutions/saas-app-core.svg?style=for-the-badge
[stars-url]: https://github.com/omnipro-solutions/saas-app-core/stargazers
[issues-shield]: https://img.shields.io/github/issues/omnipro-solutions/saas-app-core.svg?style=for-the-badge
[issues-url]: https://github.com/omnipro-solutions/saas-app-core/issues
[pull-request-shield]: https://img.shields.io/github/issues-pr-raw/omnipro-solutions/saas-app-core.svg?style=for-the-badge
[pull-request-url]: https://github.com/omnipro-solutions/saas-app-core/pulls
[license-shield]: https://img.shields.io/github/license/omnipro-solutions/saas-app-core.svg?style=for-the-badge
[license-url]: https://github.com/omnipro-solutions/saas-app-core/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/
[Django]: https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=Django&logoColor=white
[Django-url]: https://www.djangoproject.com/
[drf]: https://img.shields.io/badge/drf-3B8EFF?style=for-the-badge&logo=djangorestframework&logoColor=white
[drf-url]: https://www.django-rest-framework.org/
[postgresql]: https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white
[postgresql-url]: https://www.postgresql.org/
[celery]: https://img.shields.io/badge/Celery-4A154B?style=for-the-badge&logo=celery&logoColor=white
[celery-url]: http://www.celeryproject.org/