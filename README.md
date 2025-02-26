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

<h3 align="center">OmniPro Solutions SaaS App Base</h3>

  <p align="center">
    Biblioteca de módulos base para aplicaciones Django con funcionalidades comunes para proyectos SaaS.
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
        <li><a href="#stack-tecnologico">Stack</a></li>
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

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de módulos base diseñada para ser utilizada en aplicaciones Django, específicamente para conectar con OMS (Omnipro Solutions). Su propósito principal es proporcionar funcionalidades básicas y comunes que pueden ser reutilizadas en diferentes proyectos de SaaS basados en Django. Las funcionalidades principales incluyen autenticación, gestión de usuarios y grupos, configuraciones base, herramientas administrativas mejoradas con `django-jazzmin`, y una API RESTful utilizando Django Rest Framework.

El repositorio está estructurado siguiendo una arquitectura típica de proyectos Django, con carpetas para modelos, vistas, formularios, serializadores, configuraciones y más. Entre los archivos principales se encuentran `README.md` para la documentación básica, `LICENSE` bajo MIT, `requirements.txt` para las dependencias necesarias, y el script `make_migrations.py` para generar migraciones de base de datos.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Stack tecnológico

* [![Django][django]][django-url]
* [![Python][python]][python-url]
* [![PostgreSQL][postgresql]][postgresql-url]
* [![Redis][redis]][redis-url]
* [![Celery][celery]][celery-url]
* [![DRF][drf]][drf-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Iniciar Proyecto

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Prerequisitos

Antes de comenzar, asegúrate de tener instalado:

- Python 3.8 o superior
- PostgreSQL
- Redis
- Pip (gestor de paquetes de Python)

### Instalación

1. Clona el repositorio:
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```
2. Crea un entorno virtual (opcional pero recomendado):
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: env\Scripts\activate
   ```
3. Instala las dependencias:
   ```sh
   pip install -r requirements.txt
   ```
4. Configura tus variables de entorno creando un archivo `.env` en la raíz del proyecto y define las variables necesarias, como `SECRET_KEY`, `DATABASE_URL`, etc.
5. Genera migraciones y aplícalas:
   ```sh
   python make_migrations.py
   python manage.py migrate
   ```
6. Crea un superusuario (opcional):
   ```sh
   python manage.py createsuperuser
   ```
7. Ejecuta el servidor de desarrollo:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Para utilizar la biblioteca, puedes comenzar integrando sus funcionalidades en tu proyecto Django. Por ejemplo, para gestionar usuarios y autenticación, puedes usar los modelos y vistas proporcionados en el directorio `omni_pro_base`.

_For more examples, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implementación de caché
- [ ] Pruebas automatizadas completas
- [ ] Documentación ampliada con guías detalladas y mejores prácticas
- [ ] Medidas de seguridad adicionales, como validación de entradas y uso de HTTPS en producción
- [ ] Integración avanzada de monitoreo y logging

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
[license-shield]: https://img.shields.io/github/license/omnipro-solutions/saas-app-base.svg?style=for-the-badge
[license-url]: https://github.com/omnipro-solutions/saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/

<!-- Badges -->
[django]: https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white
[django-url]: https://www.djangoproject.com/
[python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[python-url]: https://www.python.org/
[postgresql]: https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white
[postgresql-url]: https://www.postgresql.org/
[redis]: https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white
[redis-url]: https://redis.io/
[celery]: https://img.shields.io/badge/Celery-008080?style=for-the-badge&logo=celery&logoColor=white
[celery-url]: http://www.celeryproject.org/
[drf]: https://img.shields.io/badge/Django_REST_Framework-3B8EFF?style=for-the-badge&logo=django-rest-framework&logoColor=white
[drf-url]: https://www.django-rest-framework.org/