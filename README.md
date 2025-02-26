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
href="https://github.com/omnipro-solutions/saas-app-base.git">
    <img src="https://pngimg.com/uploads/github/github_PNG78.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">saas-app-base</h3>

  <p align="center">
    Biblioteca de módulos base para aplicaciones Django SaaS conectadas a OMS.
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

El repositorio `omnipro-solutions/saas-app-base` es una biblioteca de módulos base diseñada para ser utilizada en aplicaciones Django, específicamente para conectar con OMS (Omnipro Solutions). Su propósito principal es proporcionar funcionalidades básicas y comunes que pueden ser reutilizadas en diferentes proyectos de SaaS (Software as a Service) basados en Django. Entre las principales características se incluyen:

- **Autenticación**: Manejo de autenticación tanto local como mediante un servicio externo.
- **Gestión de Usuarios y Grupos**: Modelos, vistas y serializadores para gestionar usuarios y grupos.
- **Configuraciones Base**: Configuraciones básicas para el entorno Django, incluyendo middleware, plantillas y bases de datos.
- **Herramientas Administrativas**: Integración con `django-jazzmin` para mejorar la interfaz del administrador de Django.
- **API RESTful**: Vistas y serializadores para crear endpoints API utilizando Django Rest Framework.

Los archivos más importantes incluyen:

- **README.md**: Documentación básica sobre el propósito del repositorio y cómo utilizarlo.
- **LICENSE**: Licencia MIT que permite el uso, modificación y distribución del código con ciertas condiciones.
- **MANIFEST.in**: Incluye archivos estáticos en la distribución del paquete.
- **make_migrations.py**: Script para generar automáticamente migraciones de base de datos.
- **requirements.txt**: Lista de dependencias necesarias para ejecutar el proyecto.
- **setup.py**: Configuración para instalar el paquete como una biblioteca Python.

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
## Comenzando

A continuación se presentan instrucciones claras y precisas para configurar el proyecto en tu entorno local.

### Prerequisitos

Para correr este repositorio, asegúrate de tener instalado:

- Python 3.8 o superior
- PostgreSQL
- Redis
- Celery (opcional, pero recomendado)

### Instalación

1. Clonar el repositorio:
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-base.git
   cd saas-app-base/
   ```

2. Crear un entorno virtual y activarlo (Opcional pero recomendado):
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: env\Scripts\activate
   ```

3. Instalar las dependencias:
   ```sh
   pip install -r requirements.txt
   ```

4. Configurar variables de entorno:
   Crea un archivo `.env` en la raíz del proyecto y define las variables necesarias, como `SECRET_KEY`, `DATABASE_URL`, etc.

5. Generar migraciones y aplicarlas:
   ```sh
   python make_migrations.py
   python manage.py migrate
   ```

6. (Opcional) Crear un superusuario:
   ```sh
   python manage.py createsuperuser
   ```

7. Ejecutar el servidor de desarrollo:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Para utilizar la biblioteca, puedes comenzar por explorar las vistas y serializadores proporcionados en el directorio `views/` y `serializers/`. Aquí tienes un ejemplo básico de cómo podrías usar una vista para gestionar usuarios:

```python
from rest_framework import viewsets
from .models import User
from .serializers import UserSerializer

class UserViewSet(viewsets.ModelViewSet):
    queryset = User.objects.all()
    serializer_class = UserSerializer
```

Para más ejemplos, por favor refiérete a la [Documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Mejorar el sistema de autenticación
- [ ] Implementar un sistema de caché robusto
- [ ] Desarrollar un conjunto completo de pruebas automatizadas
- [ ] Mejorar la documentación completa con guías detalladas y mejores prácticas

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

<!-- BADGES -->
[django]: https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=djangoproject&logoColor=white
[django-url]: https://djangoproject.com/
[python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[python-url]: https://www.python.org/
[postgresql]: https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white
[postgresql-url]: https://www.postgresql.org/
[redis]: https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white
[redis-url]: https://redis.io/
[celery]: https://img.shields.io/badge/Celery-00A1F1?style=for-the-badge&logo=celery&logoColor=white
[celery-url]: http://www.celeryproject.org/
[drf]: https://img.shields.io/badge/django-rest-framework-3DDC84?style=for-the-badge&logo=django-rest-framework&logoColor=white
[drf-url]: https://www.django-rest-framework.org/