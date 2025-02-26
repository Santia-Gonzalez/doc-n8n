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

<a href="https://github.com/omnipro-solutions/saas-app-base.git">
    <img src="https://pngimg.com/uploads/github/github_PNG78.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">saas-app-base</h3>

<p align="center">
  Una base de aplicación SaaS para integrar con OMS utilizando Django.
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

El repositorio `omnipro-solutions-saas-app-base` proporciona una base de aplicación para conectar con OMS (Organización Multiservicios) utilizando Django. Está diseñado para facilitar el desarrollo rápido de aplicaciones SaaS en un entorno Django, ofreciendo herramientas y configuraciones esenciales.

### Funcionalidades Principales

- **Autenticación**: Soporte tanto para autenticación estática como mediante servicios externos.
- **Gestión de Usuarios**: Modelos personalizados y vistas RESTful para la gestión eficiente de usuarios y grupos.
- **Serialización**: Serializadores que permiten convertir datos entre objetos Python y formatos JSON.
- **Configuraciones Modulares**: Configuraciones separadas para entornos de desarrollo, producción y base.
- **Integración con Celery**: Soporte para tareas asincrónicas y programación periódica.

### Estructura del Repositorio

El repositorio está estructurado de la siguiente manera:

- `README.md`: Documentación básica sobre el propósito y uso del repositorio.
- `LICENSE`: Licencia MIT que permite un amplio uso bajo ciertas condiciones.
- `MANIFEST.in`, `make_migrations.py`, `requirements.txt`, `setup.py`: Scripts e instrucciones para la gestión de dependencias, configuración y distribución.

El directorio principal `omni_pro_base/` contiene:

- **Modelos**: Definidos en `models/`, incluyendo un modelo base (`OmniModel`) y usuarios personalizados.
- **Vistas**: Implementadas en `views/` usando el framework REST Framework de Django.
- **Serializadores**: Ubicados en `serializers/`.
- **Formularios**: Personalizados en `forms/`.
- **Admin**: Configuraciones en `admin/`.
- **Configuraciones**: Separadas por entornos (`base.py`, `local.py`, `production.py`) en `settings/`.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Stack Tecnológico

El proyecto utiliza las siguientes tecnologías:

* [![Python][Python]][Python-url]
* [![Django][Django]][Django-url]
* [![Celery][Celery]][Celery-url]
* [![Redis][Redis]][Redis-url]
* [![PostgreSQL][PostgreSQL]][PostgreSQL-url]
* [![DRF][drf]][drf-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Comenzando

Para configurar el proyecto en tu entorno local, sigue estos pasos:

### Prerequisitos

- Python 3.11 o superior
- Django 5.0
- Dependencias listadas en `requirements.txt`

### Instalación

1. Clona el repositorio:
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```

2. Crea un entorno virtual (opcional pero recomendado):
   ```bash
   python -m venv env
   source env/bin/activate  # En Windows: env\Scripts\activate
   ```

3. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

4. Configura las variables de entorno creando un archivo `.env` en la raíz del proyecto y definiendo las necesarias como `SECRET_KEY`, `DATABASE_URL`, etc.

5. Genera migraciones:
   ```bash
   python make_migrations.py
   ```

6. Ejecuta las migraciones:
   ```bash
   python manage.py migrate
   ```

7. Crea un superusuario (para acceso al admin):
   ```bash
   python manage.py createsuperuser
   ```

8. Inicia el servidor de desarrollo:
   ```bash
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Para utilizar la aplicación, asegúrate de haber seguido los pasos de instalación. Luego, puedes acceder a las funcionalidades mediante el panel de administración de Django o interactuar con las APIs RESTful proporcionadas.

_For more examples, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implementación de caché
- [ ] Mejoras en seguridad para entornos de producción
- [ ] Añadir más pruebas unitarias y de integración
- [ ] Ampliar la documentación interna

Mira las [ISSUES](https://github.com/omnipro-solutions/saas-app-base/issues) para una lista completa de mejoras (problemas conocidos).

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

<a href="https://github.com/omnipro-solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=omnipro-solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENCIA -->
## Licencia

Distribuido bajo la licencia MIT. Ve a `LICENSE.txt` para más información.

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
[pull-request-shield]: https://img.shields.io/github/issues-pr-raw/omnipro-solutions/saas-app-base.svg?style=for-the-badge
[pull-request-url]: https://github.com/omnipro-solutions/saas-app-base/pulls
[license-shield]: https://img.shields.io/github/license/omnipro-solutions/saas-app-base.svg?style=for-the-badge
[license-url]: https://github.com/omnipro-solutions/saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/

<!-- Tecnología Badges -->
[Python]: https://img.shields.io/badge/python-3.11-blue?style=for-the-badge&logo=python
[Python-url]: https://www.python.org/
[Django]: https://img.shields.io/badge/django-5.0-green?style=for-the-badge&logo=django
[Django-url]: https://www.djangoproject.com/
[Celery]: https://img.shields.io/badge/celery-blueviolet?style=for-the-badge&logo=celery
[Celery-url]: http://www.celeryproject.org/
[Redis]: https://img.shields.io/badge/redis-red?style=for-the-badge&logo=redis
[Redis-url]: https://redis.io/
[PostgreSQL]: https://img.shields.io/badge/postgres-13.3-blueviolet?style=for-the-badge&logo=postgresql
[PostgreSQL-url]: https://www.postgresql.org/
[drf]: https://img.shields.io/badge/django_rest_framework-3.14.0-blue?style=for-the-badge&logo=django-rest-framework
[drf-url]: https://www.django-rest-framework.org/