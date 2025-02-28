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

<a
href="https://github.com/omnipro-solutions/saas-app-oms.git">
    <img src="https://pngimg.com/uploads/github/github_PNG78.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">OMNI Pro OMS</h3>

  <p align="center">
    Sistema de gestión de operaciones y tareas multiinquilino.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Documentación oficial »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-oms/issues/bug">Reportar errores</a>
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-oms/issues/features">Solicitar mejoras</a>
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

El proyecto **OMNI Pro OMS** es un marco robusto diseñado para la gestión de operaciones y tareas en entornos multiinquilino. Utiliza Django como su base, proporcionando una estructura organizada que facilita el manejo de configuraciones, operaciones, tareas y relaciones entre inquilinos.

### Componentes clave:
- **Configuración**: Gestiona detalles esenciales como tokens y URLs.
- **Operaciones**: Representa diversas operaciones con atributos detallados como métodos HTTP y configuraciones de notificación.
- **Tipos de Operación**: Define categorías específicas para las operaciones.
- **Tareas**: Administra tareas relacionadas con operaciones, incluyendo datos de origen y destino.
- **Inquilinos**: Representa inquilinos con detalles como ID del cliente y secretos.

### Funcionalidades:
- **Gestión Multiinquilino**: Soporta múltiples inquilinos con aislamiento de datos.
- **Gestión de Tareas**: Supervisa el estado de las tareas y gestiona notificaciones.
- **Gestión de Configuraciones**: Permite almacenar y gestionar configuraciones para diferentes operaciones.
- **Notificaciones por Correo Electrónico**: Envía correos electrónicos cuando cambia el estado de una tarea.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Stack tecnológico

* [![Django][django]][django-url]
* [![DRF][drf]][drf-url]
* [![PostgreSQL][postgres]][postgres-url]
* [![Celery][celery]][celery-url]
* [![Redis][redis]][redis-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Comenzando

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Prerequisitos

- Python 3.8+
- PostgreSQL
- Redis
- Celery

### Instalación

1. Clone the repo
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-oms.git
   ```
2. Install dependencies using pip
   ```sh
   pip install -r requirements.txt
   ```
3. Set up your database and create a superuser
   ```sh
   python manage.py makemigrations
   python manage.py migrate
   python manage.py createsuperuser
   ```
4. Enter your API keys in the appropriate configuration files.
5. Change git remote URL to avoid accidental pushes to base project
   ```sh
   git remote set-url origin omnipro-solutions/saas-app-oms
   git remote -v # confirm the changes
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Para comenzar a utilizar el sistema, inicia los servicios necesarios y accede al panel administrativo para gestionar operaciones y tareas.

1. Iniciar servidores
   ```sh
   python manage.py runserver
   ```
2. Acceder al panel de administración en `http://localhost:8000/admin`

_For more examples, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Mejoras en la gestión de notificaciones
- [ ] Integración con más servicios externos
- [ ] Optimización del rendimiento para grandes volúmenes de datos
    - [ ] Implementar caché avanzada

Mira las [ISSUES](https://github.com/omnipro-solutions/saas-app-oms/issues) para una lista completa de mejoras (problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUYENDO -->
## Contribuyendo

Las contribuciones son lo que hace que la comunidad de código abierto sea un lugar increíble para aprender, inspirar y crear. Cualquier contribución que haga es **muy apreciada**.

Si tienes una sugerencia que mejoraría esto, "fork" el repositorio y crea una solicitud de pull request. También puede simplemente abrir un problema con la etiqueta "mejora".
¡No te olvides de darle una estrella al proyecto! ¡Gracias de nuevo!

1. "Fork" el Proyecto
2. Crea tu rama "Feature" (`git checkout -b feature/AmazingFeature`)
3. Realiza un "commit" a tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. "Push" a tus cambios locales a la rama remota (`git push origin feature/AmazingFeature`)
5. Inicia una 'pull request'

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top Contribuyentes:

<a href="https://github.com/omnipro-solutions/saas-app-oms/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=omnipro-solutions/saas-app-oms" alt="contrib.rocks image" />
</a>

<!-- LICENCIA -->
## Licencia

Distribuido bajo la licencia MIT. Ve a `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/omnipro-solutions/saas-app-oms.svg?style=for-the-badge
[contributors-url]: https://github.com/omnipro-solutions/saas-app-oms/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/omnipro-solutions/saas-app-oms.svg?style=for-the-badge
[forks-url]: https://github.com/omnipro-solutions/saas-app-oms/network/members
[stars-shield]: https://img.shields.io/github/stars/omnipro-solutions/saas-app-oms.svg?style=for-the-badge
[stars-url]: https://github.com/omnipro-solutions/saas-app-oms/stargazers
[issues-shield]: https://img.shields.io/github/issues/omnipro-solutions/saas-app-oms.svg?style=for-the-badge
[issues-url]: https://github.com/omnipro-solutions/saas-app-oms/issues
[pull-request-shield]: https://img.shields.io/github/issues-pr-raw/omnipro-solutions/saas-app-oms.svg?style=for-the-badge
[pull-request-url]: https://github.com/omnipro-solutions/saas-app-oms/pulls
[license-shield]: https://img.shields.io/github/license/omnipro-solutions/saas-app-oms.svg?style=for-the-badge
[license-url]: https://github.com/omnipro-solutions/saas-app-oms/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/
[django]: https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white
[django-url]: https://www.djangoproject.com/
[drf]: https://img.shields.io/badge/drf-3.13.1-black?style=for-the-badge&logo=python&logoColor=white
[drf-url]: https://www.django-rest-framework.org/
[postgres]: https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white
[postgres-url]: https://www.postgresql.org/
[celery]: https://img.shields.io/badge/celery-4.4.7-blue?style=for-the-badge&logo=python&logoColor=white
[celery-url]: http://www.celeryproject.org/
[redis]: https://img.shields.io/badge/Redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white
[redis-url]: https://redis.io/