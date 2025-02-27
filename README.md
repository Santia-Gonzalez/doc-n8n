<a id="readme-top"></a>
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![PR][pull-request-shield]][pull-request-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<br />

<div align="center">

<a href="https://github.com/omnipro-solutions/saas-app-base.git">
    <img src="https://pngimg.com/uploads/github/github_PNG78.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">saas-app-base</h3>

  <p align="center">
    Una biblioteca de Python para aplicaciones Django SaaS, proporcionando una base robusta y funcional que facilita el desarrollo rápido.
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

El repositorio `saas-app-base` es una biblioteca de Python diseñada para aplicaciones Django, ofreciendo una base sólida y funcional para el desarrollo rápido de aplicaciones SaaS. Este proyecto se centra en proporcionar un marco que facilite la integración con sistemas de gestión de servicios (OMS), asegurando una estructura robusta para desarrolladores.

**Funciones Clave:**
- **Autenticación:** Soporta métodos básicos y OAuth2, permitiendo la integración fluida con servicios externos.
- **Serialización:** Utiliza Django REST Framework para serializar datos de modelos `User`.
- **Gestión de Usuarios y Grupos:** Facilita operaciones CRUD sobre usuarios y grupos a través de API.
- **Configuración Dinámica:** Permite configuraciones específicas del entorno (local, producción) mediante archivos separados.
- **Middleware Personalizado:** Incluye middleware para permitir CIDR específico y seguridad básica.
- **Integración con Celery:** Soporta la ejecución de tareas asíncronas.

**Estructura Principal:**
- `README.md`: Descripción del propósito del repositorio.
- `LICENSE`: Licencia MIT bajo la cual se distribuye el software.
- `MANIFEST.in`, `make_migrations.py`, `requirements.txt`, `setup.py`: Configuraciones y dependencias necesarias para el proyecto.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Stack tecnológico

* [![Django][Django]][Django-url]
* [![Python][Python]][Python-url]
* [![Django REST Framework][drf]][drf-url]
* [![Celery][Celery]][Celery-url]
* [![Redis][Redis]][Redis-url]
* [![PostgreSQL][PostgreSQL]][PostgreSQL-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Comenzando

Para configurar el proyecto en tu entorno local, sigue estas instrucciones detalladas.

### Prerequisitos

Asegúrate de tener instalado:
- Python 3.x
- Pip (gestor de paquetes de Python)
- PostgreSQL
- Redis
- Docker (opcional)

### Instalación

1. Clona el repositorio:
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-base.git
   cd saas-app-base/
   ```

2. Crea y activa un entorno virtual (recomendado):
   ```bash
   python -m venv env
   source env/bin/activate  # En Windows: env\Scripts\activate
   ```

3. Instala las dependencias:
   ```sh
   pip install -r requirements.txt
   ```

4. Configura las variables de entorno necesarias en un archivo `.env` (por ejemplo, `SECRET_KEY`, `DATABASE_URL`).

5. Ejecuta migraciones para configurar la base de datos:
   ```sh
   python manage.py makemigrations
   python manage.py migrate
   ```

6. Crea un superusuario (opcional):
   ```bash
   python manage.py createsuperuser
   ```

7. Inicia el servidor de desarrollo:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Para utilizar la biblioteca, asegúrate de haber seguido los pasos de configuración. Puedes acceder a las APIs proporcionadas para gestionar usuarios y grupos.

Ejemplo básico de cómo interactuar con el sistema:

```python
from myapp.models import User

# Crear un nuevo usuario
new_user = User.objects.create(username='testuser', email='test@example.com')
```

_For more examples, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Mejorar la documentación interna.
- [x] Implementar autenticación OAuth2.
- [ ] Optimizar el rendimiento de las consultas a la base de datos.
- [ ] Agregar soporte para multi-tenencia.

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
[pull-request-shield]: https://img.shields.io/github/issues-pr-raw/omnipro-solutions/saas-app-base.svg?style=for-the-badge
[pull-request-url]: https://github.com/omnipro-solutions/saas-app-base/pulls

[Django]: https://img.shields.io/badge/Django-%23092E20.svg?style=for-the-badge&logo=Django&logoColor=white
[Django-url]: https://www.djangoproject.com/
[Python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[Python-url]: https://www.python.org/
[drf]: https://img.shields.io/badge/django_rest_framework-%230092E20.svg?style=for-the-badge&logo=djangorestframework&logoColor=white
[drf-url]: https://www.django-rest-framework.org/
[Celery]: https://img.shields.io/badge/Celery-4A154B?style=for-the-badge&logo=celery&logoColor=white
[Celery-url]: http://www.celeryproject.org/
[Redis]: https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white
[Redis-url]: https://redis.io/
[PostgreSQL]: https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white
[PostgreSQL-url]: https://www.postgresql.org/
[Event-Url]: ----
