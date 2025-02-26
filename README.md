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
    Biblioteca de módulos base para aplicaciones SaaS conectadas a OMS.
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
        <li><a href="#prerequisitos">Prerrequisitos</a></li>
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

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de módulos base diseñada para facilitar el desarrollo de aplicaciones SaaS que se integran con Open Management System (OMS). Este proyecto proporciona funcionalidades básicas y estructuras necesarias, incluyendo autenticación, modelos extendidos, serializadores, configuraciones de Django, integración con Django Rest Framework, y gestión de migraciones.

### Stack tecnológico
- [![Python][Python]][Python-url]
- [![Django][Django]][Django-url]
- [![DRF][drf]][drf-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Comenzando

Para configurar el proyecto en tu entorno local, sigue las instrucciones detalladas a continuación.

### Prerrequisitos

Asegúrate de tener instalados los siguientes componentes:
- Python 3.11 o superior
- Pip para la gestión de paquetes
- Git para control de versiones
- PostgreSQL como base de datos (SQLite para desarrollo)

### Instalación

1. Clona el repositorio
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```

2. Crea un entorno virtual (Opcional pero recomendado)
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: env\Scripts\activate
   ```

3. Instala las dependencias
   ```sh
   pip install -r requirements.txt
   ```

4. Configura variables de entorno
   Crea un archivo `.env` en el directorio raíz del proyecto y configura las variables necesarias (por ejemplo, `SECRET_KEY`, `DATABASE_URL`, etc.).

5. Ejecuta migraciones
   ```sh
   python make_migrations.py
   ```

6. Inicia el servidor de desarrollo
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Para utilizar la biblioteca, asegúrate de haber configurado correctamente el entorno. Puedes acceder a las APIs definidas en `urls.py` y utilizar los serializadores en `serializers/` para convertir objetos modelo a JSON.

_For more examples, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implementar soporte multi-tenencia
- [ ] Mejorar la integración con sistemas externos
- [ ] Desarrollar una capa frontend robusta
    - [ ] Integración con React o Vue.js

Mira las [ISSUES](https://github.com/omnipro-solutions/saas-app-base/issues) para una lista completa de mejoras (problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Contribuciones son lo que hacen a la comunidad de código abierto un lugar tan maravilloso para aprender, inspirar y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor fork el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "enhancement". ¡No olvides darle a este proyecto una estrella! Gracias nuevamente!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a 'pull request'

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

[Python]: https://img.shields.io/badge/python-3.11-blue?style=for-the-badge&logo=python
[Python-url]: https://www.python.org/
[Django]: https://img.shields.io/badge/django-5.0-green?style=for-the-badge&logo=django
[Django-url]: https://www.djangoproject.com/
[drf]: https://img.shields.io/badge/DRF-blue?style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABGdBTUEAAK/INwWK6QAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAACpSURBVDjLY/j//z8DJYGBgYEBAQEBgYGBgQEBAQEBgYGBgQEBAQEBgYGBgQEBAQEBgYGBgQEBAQEBgYGBgQEBAQEBgYGBgQEBAQEBgYGBgQEBAQEBgYGBgUEBAYHh4eHw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8PDw8Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4+Pj4AAAACXBIWXMAAAsTAAALEwEAmpwYAAAAAXNSR0IArs4c6QAAAABJRU5ErkJggg==
[drf-url]: https://www.django-rest-framework.org/