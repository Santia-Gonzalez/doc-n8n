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

<a href="https://github.com/Omnipro-Solutions/saas-app-base.git">
    <img src="https://pngimg.com/uploads/github/github_PNG78.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Omni Pro Solutions SaaS App Base</h3>

  <p align="center">
    Biblioteca de módulos base para aplicaciones Django que se conectan a Omnipro Solutions.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Documentación oficial »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/Omnipro-Solutions/saas-app-base/issues/bug">Reportar errores</a>
    &middot;
    <a href="https://github.com/Omnipro-Solutions/saas-app-base/issues/features">Solicitar mejoras</a>
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

El repositorio `omni_pro_solutions_saas_app_base` es una biblioteca de módulos base diseñada para facilitar el desarrollo de aplicaciones SaaS basadas en Django que se integran con Omnipro Solutions. Proporciona funcionalidades comunes necesarias para crear aplicaciones robustas y escalables, incluyendo autenticación y autorización avanzada, modelos básicos, serializadores eficientes, administración mejorada mediante Django Jazzmin, y soporte para tareas asíncronas con Celery.

### Stack tecnológico
* [![Python][Python]][Python-url]
* [![Django][Django]][Django-url]
* [![Celery][Celery]][Celery-url]
* [![Redis][Redis]][Redis-url]
* [![Jazzmin][Jazzmin]][Jazzmin-url]
* [![PostgreSQL][PostgreSQL]][PostgreSQL-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Comenzando

Para configurar el proyecto en tu entorno local, sigue las instrucciones detalladas a continuación.

### Prerrequisitos

- Python 3.11 o superior
- Django 5.0
- PostgreSQL (para producción) o SQLite (por defecto)
- Redis instalado y ejecutándose para Celery

### Instalación

1. Clona el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```

2. Crea un entorno virtual (recomendado):
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: .\env\Scripts\activate
   ```

3. Instala las dependencias:
   ```sh
   pip install -r requirements.txt
   ```

4. Configura tus variables de entorno en un archivo `.env`:
   ```
   SECRET_KEY=django-insecure-...
   DATABASE_URL=postgresql://user:password@localhost/db_name
   CELERY_BROKER_URL=redis://localhost:6379/0
   ```

5. Genera migraciones y aplica las mismas:
   ```sh
   python manage.py makemigrations
   python manage.py migrate
   ```

6. Ejecuta el servidor de desarrollo:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- EJEMPLOS DE USO -->
## Uso

Para utilizar la biblioteca, primero asegúrate de haber configurado el entorno local. Luego, puedes extender los modelos base y aprovechar las funcionalidades proporcionadas para desarrollar tu aplicación SaaS.

Por ejemplo, para crear un nuevo modelo que herede de `OmniModel`:

```python
from omni_pro_base.models.base_model import OmniModel

class MyCustomModel(OmniModel):
    name = models.CharField(max_length=255)
```

Para más ejemplos detallados, consulta la [documentación oficial](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Mejoras en el sistema de caché
- [ ] Ampliación de pruebas unitarias y de integración
- [ ] Documentación mejorada para autenticación avanzada
  - [ ] Guía paso a paso para configurar OAuth2

Mira las [issues](https://github.com/Omnipro-Solutions/saas-app-base/issues) para una lista completa de mejoras (problemas conocidos).

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

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENCIA -->
## Licencia

Distribuido bajo la licencia MIT. Ve a `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/Omnipro-Solutions/saas-app-base/network/members
[pull-request-shield]: https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge
[pull-request-url]: http://makeapullrequest.com
[issues-shield]: https://img.shields.io/github/issues/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/Omnipro-Solutions/saas-app-base/issues
[license-shield]: https://img.shields.io/github/license/Omnipro-Solutions/saas-app-base.svg?style=for-the-badge
[license-url]: https://github.com/Omnipro-Solutions/saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/
[Python]: https://img.shields.io/badge/python-3.11-blue?style=for-the-badge&logo=python
[Python-url]: https://www.python.org/downloads/release/python-3110/
[Django]: https://img.shields.io/badge/django-5.0-green?style=for-the-badge&logo=djangoproject
[Django-url]: https://docs.djangoproject.com/en/5.0/
[Celery]: https://img.shields.io/badge/celery-blue?style=for-the-badge&logo=celery
[Celery-url]: http://www.celeryproject.org/
[Redis]: https://img.shields.io/badge/redis-6.2-red?style=for-the-badge&logo=redis
[Redis-url]: https://redis.io/download
[Jazzmin]: https://img.shields.io/badge/jazzmin-green?style=for-the-badge&logo=jazzmin
[Jazzmin-url]: https://github.com/app-generator/django-jazzmin
[PostgreSQL]: https://img.shields.io/badge/postgresql-13-blue?style=for-the-badge&logo=postgresql
[PostgreSQL-url]: https://www.postgresql.org/download/