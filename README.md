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
href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base.git">
    <img src="https://img.shields.io/badge/OmniPro-grey?style=for-the-badge&logo=github" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Biblioteca de Módulos Base para Aplicaciones SaaS</h3>

  <p align="center">
    Una biblioteca de módulos base diseñada para facilitar el desarrollo de aplicaciones SaaS conectadas a OMS (Omnipro Solutions).
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Documentación oficial »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues/bug">Reportar errores</a>
    &middot;
    <a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues/features">Solicitar mejoras</a>
  </p>
</div>

<!-- TABLA DE CONTENIDO -->
<details>
  <summary>Tabla de contenido</summary>
  <ol>
    <li>
      <a href="#about-the-project">Acerca del Proyecto</a>
      <ul>
        <li><a href="#built-with">Construido con</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Empezando</a>
      <ul>
        <li><a href="#prerequisites">Requisitos previos</a></li>
        <li><a href="#installation">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#usage">Uso</a></li>
    <li><a href="#roadmap">Ruta de Desarrollo</a></li>
    <li><a href="#contributing">Contribuyendo</a></li>
    <li><a href="#license">Licencia</a></li>
  </ol>
</details>

<!-- SOBRE EL PROYECTO -->
## Acerca del Proyecto

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de módulos base diseñada para el desarrollo eficiente y escalable de aplicaciones SaaS conectadas a Omnipro Solutions. Proporciona funcionalidades comunes como autenticación, gestión de usuarios, configuraciones dinámicas y más, facilitando la integración con sistemas externos y permitiendo una personalización extensa.

### Construido con

* [![Python][Python-logo]][Python-url]
* [![Django][Django-logo]][Django-url]
* [![Django Rest Framework][DRF-logo]][DRF-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Empezando

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Prerrequisitos

Antes de comenzar, asegúrate de tener instalado:

- Python 3.11 o superior
- Pip (gestor de paquetes de Python)
- Git

### Instalación

1. Clona el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base.git
   ```
2. Navega al directorio del proyecto clonado:
   ```sh
   cd omnipro-solutions-saas-app-base
   ```
3. Crea un entorno virtual y actívalo:
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: .\env\Scripts\activate
   ```
4. Instala las dependencias necesarias:
   ```sh
   pip install -r requirements.txt
   ```
5. Configura tus variables de entorno creando un archivo `.env` en la raíz del proyecto y añadiendo configuraciones como `SECRET_KEY`, `DATABASE_URL`, etc.
6. Genera migraciones para la base de datos:
   ```sh
   python make_migrations.py
   ```
7. Inicia el servidor de desarrollo:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Para utilizar la biblioteca en tu proyecto, asegúrate de haber seguido todos los pasos de instalación. Una vez configurado, puedes integrar las funcionalidades comunes como autenticación y gestión de usuarios a través del Django Rest Framework.

_For more examples, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Ruta de Desarrollo

- [ ] Implementación de caché avanzada
- [ ] Expansión del sistema de pruebas unitarias
- [ ] Mejoras adicionales en la seguridad
    - [ ] Auditorías de seguridad regulares

See the [open issues](https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Las contribuciones son lo que hacen que la comunidad de código abierto sea un lugar tan maravilloso para aprender, inspirar y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir una incidencia con la etiqueta "mejora".
¡No olvides darle a este proyecto una estrella! ¡Gracias de nuevo!

1. Fork del Proyecto
2. Crea tu rama de característica (`git checkout -b feature/AmazingFeature`)
3. Haz tus cambios y confirma (`git commit -m 'Add some AmazingFeature'`)
4. Empuja los cambios a la rama (`git push origin feature/AmazingFeature`)
5. Abre una solicitud de extracción

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top contribuidores:

<a href="https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/omnipro-solutions-saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[contributors-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[forks-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/network/members
[stars-shield]: https://img.shields.io/github/stars/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[stars-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/stargazers
[issues-shield]: https://img.shields.io/github/issues/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[issues-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/issues
[license-shield]: https://img.shields.io/github/license/Omnipro-Solutions/omnipro-solutions-saas-app-base.svg?style=for-the-badge
[license-url]: https://github.com/Omnipro-Solutions/omnipro-solutions-saas-app-base/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/

[Python-logo]: https://img.shields.io/badge/with%20a%20logo-grey?style=for-the-badge&logo=python
[Python-url]: https://www.python.org/
[Django-logo]: https://img.shields.io/badge/with%20a%20logo-grey?style=for-the-badge&logo=django
[Django-url]: https://www.djangoproject.com/
[DRF-logo]: https://img.shields.io/badge/with%20a%20logo-grey?style=for-the-badge&logo=djangorestframework
[DRF-url]: https://www.django-rest-framework.org/