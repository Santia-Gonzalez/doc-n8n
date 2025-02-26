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
href="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDI0IiBoZWlnaHQ9IjEwMjQiIHZpZXdCb3g9IjAgMCAxMDI0IDEwMjQiPjxwYXRoIGZpbGw9ImN1cnJlbnRDb2xvciIgZD0iTTYyOC43MzYgNTI4Ljg5NkE0MTYgNDE2IDAgMCAxIDkyOCA5MjhIOTZhNDE1Ljg3IDQxNS44NyAwIDAgMSAyOTkuMjY0LTM5OS4xMDRMNTEyIDcwNHpNNzIwIDMwNGEyMDggMjA4IDAgMSAxLTQxNiAwYTIwOCAyMDggMCAwIDEgNDE2IDAiLz48L3N2Zz4=">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Biblioteca Base de Aplicaciones SaaS para Django</h3>

  <p align="center">
    Una biblioteca de módulos base diseñada para aplicaciones SaaS basadas en Django, facilitando la autenticación, gestión de usuarios y configuración del entorno.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explore los documentos »</strong></a>
    <br />
    <br />
    &middot;
    <a href="#">Reportar un error</a>
    &middot;
    <a href="#">Solicitar una característica</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de Contenidos</summary>
  <ol>
    <li>
      <a href="#about-the-project">Acerca del Proyecto</a>
      <ul>
        <li><a href="#built-with">Hecho con</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Comenzando</a>
      <ul>
        <li><a href="#prerequisites">Requisitos previos</a></li>
        <li><a href="#installation">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#usage">Uso</a></li>
    <li><a href="#roadmap">Hoja de ruta</a></li>
    <li><a href="#contributing">Contribuciones</a></li>
    <li><a href="#license">Licencia</a></li>
    <li><a href="#contact">Contacto</a></li>
    <li><a href="#acknowledgments">Agradecimientos</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## Acerca del Proyecto

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de módulos base diseñada para facilitar el desarrollo rápido y eficiente de aplicaciones SaaS utilizando Django. Proporciona funcionalidades esenciales como autenticación, gestión de usuarios y configuración del entorno de desarrollo. Este proyecto está orientado a servir como un punto de partida sólido para desarrolladores que buscan implementar soluciones de software como servicio (SaaS) con Django.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Hecho con

Este proyecto está construido utilizando las siguientes tecnologías:

* [![Django][Django]][Django-url]
* [![Python][Python]][Python-url]
* [![Celery][Celery]][Celery-url]
* [![Redis][Redis]][Redis-url]

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- GETTING STARTED -->
## Comenzando

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Requisitos previos

Asegúrate de tener instalados los siguientes componentes:

- Python 3.11 o superior
- PostgreSQL (o SQLite para desarrollo local)
- Redis

### Instalación

1. Clona el repositorio
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```
2. Crea un entorno virtual (opcional pero recomendado):
   ```sh
   python -m venv venv
   source venv/bin/activate  # En Windows, usa `venv\Scripts\activate`
   ```
3. Instala las dependencias:
   ```sh
   pip install -r requirements.txt
   ```
4. Configura variables de entorno creando un archivo `.env` en el directorio raíz con las siguientes variables: `SECRET_KEY`, `DATABASE_URL`.
5. Genera migraciones y ejecuta la base de datos:
   ```sh
   python make_migrations.py
   ./manage.py migrate
   ```
6. Ejecuta el servidor localmente:
   ```sh
   ./manage.py runserver
   ```

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- USAGE EXAMPLES -->
## Uso

A continuación, se muestra un ejemplo de cómo utilizar las vistas para autenticar a un usuario:

```python
# Importar las clases y funciones necesarias
from omni_pro_base.views import UserLoginViewSet
from rest_framework.test import APIClient

# Crear cliente HTTP para realizar solicitudes
client = APIClient()

# Datos del usuario (deberían ser validados en una aplicación real)
data = {
    "username": "user@example.com",
    "password": "securepassword123"
}

# Realizar solicitud POST a la vista de login
response = client.post('/auth/users/login/', data)

if response.status_code == 200:
    print("Login exitoso!")
    # Acceder al token y datos del usuario en respuesta
    user_data = response.json()
else:
    print("Error en el login:", response.data)
```

Para más ejemplos, por favor consulta la [Documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- ROADMAP -->
## Hoja de ruta

- [ ] Implementar caché distribuida
- [ ] Mejoras en la seguridad
- [ ] Monitoreo y logging avanzados
- [ ] Soporte multi-inquilino

Consulta los [problemas abiertos](#) para ver una lista completa de características propuestas (y problemas conocidos).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- CONTRIBUTING -->
## Contribuciones

Las contribuciones hacen que la comunidad de código abierto sea un lugar tan increíble para aprender, inspirarse y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "mejora". ¡No olvides darle al proyecto una estrella! Gracias de nuevo!

1. Fork del Proyecto
2. Crea tu Rama de Característica (`git checkout -b feature/AmazingFeature`)
3. Realiza tus Cambios y Confirma (`git commit -m 'Add some AmazingFeature'`)
4. Empuja a la Rama (`git push origin feature/AmazingFeature`)
5. Abre una Solicitud de Extracción

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Principales contribuyentes:

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. Consulta `LICENSE.txt` para más información.

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
[Django]: https://img.shields.io/static/v1?label=Django&message=framework&color=092E20&logo=djangoproject&style=for-the-badge
[Django-url]: https://www.djangoproject.com/
[Python]: https://img.shields.io/badge/python-3.11-blue.svg?style=for-the-badge&logo=python&logoColor=white
[Python-url]: https://www.python.org/
[Celery]: https://img.shields.io/static/v1?label=Celery&message=distributed&color=A020F0&logo=celery&style=for-the-badge
[Celery-url]: http://www.celeryproject.org/
[Redis]: https://img.shields.io/badge/redis-10.5.7-blue.svg?style=for-the-badge&logo=redis&logoColor=white
[Redis-url]: https://redis.io/
```

Este formato proporciona una documentación clara, profesional y detallada para el repositorio `omnipro-solutions-saas-app-base`, facilitando su comprensión y uso eficiente.
