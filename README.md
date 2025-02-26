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
    <img src="https://pngimg.com/uploads/github/github_PNG78.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Base de Código para Aplicaciones SaaS</h3>

  <p align="center">
    Base de código diseñada para aplicaciones SaaS que se conectan con OMS.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Documentación oficial »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-base/issues">Reportar errores</a>
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-base/issues">Solicitar mejoras</a>
  </p>
</div>

<!-- TABLA DE CONTENIDO -->
<details>
  <summary>Tabla de contenido</summary>
  <ol>
    <li>
      <a href="#descripción">Descripción</a>
      <ul>
        <li><a href="#stack-tecnologico">Stack Tecnológico</a></li>
      </ul>
    </li>
    <li>
      <a href="#comenzando">Comenzando</a>
      <ul>
        <li><a href="#prerequisitos">Prerrequisitos</a></li>
        <li><a href="#instalación">Instalación</a></li>
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

El repositorio `omnipro-solutions-saas-app-base` es una base de código diseñada para facilitar el desarrollo de aplicaciones SaaS que se conectan con Omnímetro (OMS). Proporciona un conjunto robusto de herramientas y funcionalidades comunes necesarias para construir aplicaciones Django, incluyendo autenticación avanzada, gestión de usuarios, configuraciones de base de datos optimizadas, integración con servicios externos como Celery para tareas asíncronas, y configuraciones detalladas de logging.

La estructura del repositorio está organizada siguiendo el patrón MVC (Model-View-Controller) típico en Django. Incluye modelos personalizados, vistas utilizando Django Rest Framework, serializadores para APIs RESTful, formularios personalizados y configuraciones administrativas detalladas.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Stack tecnológico

* [![Django][Django]][Django-url]
* [![Python][Python]][Python-url]
* [![DRF][drf]][drf-url]
* [![Celery][Celery]][Celery-url]
* [![Redis][Redis]][Redis-url]
* [![PostgreSQL][PostgreSQL]][PostgreSQL-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Comenzando

Para configurar el proyecto en tu entorno local, sigue las instrucciones detalladas a continuación.

### Prerrequisitos

- Python 3.8 o superior
- PostgreSQL instalado y funcionando
- Redis instalado para manejar tareas asíncronas con Celery
- Git para clonar el repositorio

### Instalación

1. Clone the repo
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-base.git
   cd saas-app-base/
   ```

2. Create a virtual environment (recommended)
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: .\env\Scripts\activate
   ```

3. Install dependencies
   ```sh
   pip install -r requirements.txt
   ```

4. Configure your environment variables by creating a `.env` file in the root directory with necessary settings like `SECRET_KEY`, `DATABASE_URL`, etc.

5. Create and apply migrations
   ```sh
   python manage.py makemigrations
   python manage.py migrate
   ```

6. Run the development server
   ```sh
   python manage.py runserver
   ```

7. Access the application by navigating to `http://127.0.0.1:8000/admin/` in your browser.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Para comenzar a utilizar la base de código, asegúrate de haber seguido todos los pasos de instalación. Una vez que el servidor esté en funcionamiento, puedes acceder al panel administrativo para gestionar usuarios y configuraciones.

_For more examples and detailed usage instructions, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implementar sistema de caché para desarrollo y pruebas.
- [ ] Desarrollar suite completa de pruebas unitarias.
- [ ] Mejorar documentación con configuraciones específicas y ejemplos de uso.
- [ ] Integrar más servicios externos según sea necesario.

Mira las [ISSUES](https://github.com/omnipro-solutions/saas-app-base/issues) para una lista completa de mejoras (problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Contribuciones son lo que hacen a la comunidad de código abierto un lugar tan maravilloso para aprender, inspirar y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor "fork" el repo y crea una pull request. También puedes simplemente abrir un issue con la etiqueta "enhancement".
¡No olvides darle al proyecto una estrella! ¡Gracias de nuevo!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top Contribuyentes:

<a href="https://github.com/omnipro-solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=omnipro-solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENCIA -->
## Licencia

Distribuido bajo la Licencia MIT. Ve a `LICENSE.txt` para más información.

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

[Django]: https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=djangoproject&logoColor=white
[Django-url]: https://www.djangoproject.com/
[Python]: https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54
[Python-url]: https://www.python.org/
[drf]: https://img.shields.io/badge/django%20rest-framework-3DDC84.svg?style=for-the-badge&logo=django-rest-framework&logoColor=white
[drf-url]: https://www.django-rest-framework.org/
[Celery]: https://img.shields.io/badge/Celery-4A154B?style=for-the-badge&logo=celery&logoColor=white
[Celery-url]: http://www.celeryproject.org/
[Redis]: https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white
[Redis-url]: https://redis.io/
[PostgreSQL]: https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white
[PostgreSQL-url]: https://www.postgresql.org/