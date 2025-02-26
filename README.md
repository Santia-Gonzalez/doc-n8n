<a id="readme-top"></a>
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<a href="https://github.com/Omnipro-Solutions/saas-app-base.git">
    <img src="https://pngimg.com/uploads/github/github_PNG78.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">OmniPro Solutions SaaS App Base</h3>

  <p align="center">
    Una base sólida para construir aplicaciones SaaS que se conectan a OmniPro Solutions.
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

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de contenido</summary>
  <ol>
    <li>
      <a href="#about-the-project">Descripción</a>
      <ul>
        <li><a href="#built-with">Stack</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Comenzando</a>
      <ul>
        <li><a href="#prerequisites">Prerequisitos</a></li>
        <li><a href="#installation">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#usage">Uso</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contribuyendo</a></li>
    <li><a href="#license">Licencia</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## Descripción

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de módulos base para aplicaciones que se conectan a OmniPro Solutions. Diseñado como un proyecto Django, proporciona una sólida plataforma sobre la cual construir aplicaciones SaaS. Sus funcionalidades principales incluyen:

- **Gestión de Usuarios**: Modelos, serializadores y vistas para gestionar usuarios dentro del sistema.
- **Autenticación**: Soporte para múltiples métodos de autenticación interna y externa a través de servicios OAuth2.
- **Configuraciones Dinámicas**: Permite el uso de archivos de configuración separados para entornos local y producción, facilitando la gestión de diferentes configuraciones.
- **Integración con Django REST Framework (DRF)**: Proporciona endpoints API para gestionar usuarios y grupos.
- **Middleware Personalizado**: Incluye middleware como `AllowCIDRMiddleware` para permitir conexiones desde redes específicas.
- **Soporte para Celery**: Configuraciones para tareas asincrónicas con soporte de colas y resultados persistentes.

### Stack tecnológico
* [![Django][Django]][Django-url]
* [![Python][Python]][Python-url]
* [![Django REST Framework][DRF]][DRF-url]
* [![Celery][Celery]][Celery-url]
* [![Redis][Redis]][Redis-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Comenzando

Para configurar el proyecto en tu entorno local, sigue estas instrucciones detalladas.

### Prerequisitos

Asegúrate de tener instalado lo siguiente para poder ejecutar este repositorio:

- Python 3.8 o superior
- Pip (gestor de paquetes de Python)
- Git
- Un servidor PostgreSQL

### Instalación

1. Clona el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```

2. Crea un entorno virtual (Opcional pero recomendado):
   ```bash
   python -m venv env
   source env/bin/activate  # En Windows: .\env\Scripts\activate
   ```

3. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

4. Configura tus variables de entorno creando un archivo `.env` en la raíz del proyecto y definiendo las variables necesarias (referencia `settings/base.py`).

5. Crea migraciones y actualiza tu base de datos:
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

6. Ejecuta el servidor Django:
   ```bash
   python manage.py runserver
   ```

7. Accede a la aplicación: Abre un navegador y visita `http://127.0.0.1:8000/`.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Uso

Para utilizar esta biblioteca, puedes comenzar por explorar los endpoints API proporcionados para la gestión de usuarios y grupos. Asegúrate de revisar la documentación oficial en [Documentación Oficial](https://doc-oms.omni.pro/docs/reglas) para ejemplos más detallados.

_For more examples, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

El desarrollo futuro del proyecto incluirá:

- Mejoras en la seguridad, como implementar autenticación multifactor (MFA).
- Ampliación de soporte para otros backends de autenticación.
- Optimización del rendimiento mediante caché distribuida.
- Aumento de la cobertura de pruebas unitarias y mejora de la documentación.

Para ver una lista completa de mejoras, revisa las [ISSUES](https://github.com/Omnipro-Solutions/saas-app-base/issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Las contribuciones son lo que hacen a la comunidad de código abierto un lugar tan maravilloso para aprender, inspirar y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forke el repositorio y crea un pull request. También puedes simplemente abrir un problema con la etiqueta "enhancement". ¡No olvides darle a este proyecto una estrella! Gracias de nuevo!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a 'pull request'

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### MVP'S CODERS:

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. Para más información, ve a `LICENSE.txt`.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
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

[Django]: https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=djangoproject&logoColor=white
[Django-url]: https://www.djangoproject.com/
[Python]: https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54
[Python-url]: https://www.python.org/
[DRF]: https://img.shields.io/badge/django-rest-framework-%230092E20.svg?style=for-the-badge&logo=django-rest-framework&logoColor=white
[DRF-url]: https://www.django-rest-framework.org/
[Celery]: https://img.shields.io/badge/celery-4A154B?style=for-the-badge&logo=celery&logoColor=white
[Celery-url]: http://www.celeryproject.org/
[Redis]: https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white
[Redis-url]: https://redis.io/