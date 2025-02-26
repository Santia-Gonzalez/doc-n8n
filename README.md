<a id="readme-top"></a>
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<br />
<div align="center">

<a href="https://github.com/omnipro-solutions/saas-app-base.git">
    <img src="https://img.shields.io/badge/OmniPro-grey?style=for-the-badge&logo=github" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Biblioteca Base para Aplicaciones SaaS de Omnipro</h3>

  <p align="center">
    Una biblioteca modular diseñada para facilitar el desarrollo de aplicaciones SaaS conectadas a OMS (Omnipro Solutions).
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Documentación oficial »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-base/issues/bug">Reportar errores</a>
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-base/issues/features">Solicitar mejoras</a>
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
    <li><a href="#roadmap">Ruta de desarrollo</a></li>
    <li><a href="#contributing">Contribuyendo</a></li>
    <li><a href="#license">Licencia</a></li>
  </ol>
</details>

<!-- SOBRE EL PROYECTO -->
## Acerca del Proyecto

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de módulos base diseñada para facilitar el desarrollo de aplicaciones SaaS conectadas a OMS (Omnipro Solutions). Proporciona funcionalidades comunes necesarias en las aplicaciones SaaS desarrolladas por Omnipro, incluyendo autenticación y autorización, gestión de usuarios, configuraciones dinámicas, migraciones de base de datos, y personalización del frontend.

### Construido con
* [![Django][Django]][Django-url]
* [![Python][Python]][Python-url]
* [![Django Rest Framework][DRF]][DRF-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Empezando

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Prerequisitos

- Python 3.11 o superior
- Django 5.0
- Dependencias de terceros (ver `requirements.txt`)

### Instalación

1. Clona el repositorio
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-base.git
   ```
2. Crea un entorno virtual y activalo
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: .\env\Scripts\activate
   ```
3. Instala las dependencias del proyecto
   ```sh
   pip install -r requirements.txt
   ```
4. Configura tus variables de entorno creando un archivo `.env` en la raíz del proyecto y configurando las variables necesarias (como `SECRET_KEY`, `DATABASE_URL`, etc.).

5. Genera migraciones para la base de datos
   ```sh
   python make_migrations.py
   ```

6. Ejecuta el servidor de desarrollo
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Para utilizar esta biblioteca en tu proyecto SaaS, asegúrate de haber seguido los pasos de instalación. Luego, puedes integrar los módulos base proporcionados para manejar autenticación, gestión de usuarios y otras funcionalidades comunes.

_For more examples, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Ruta de desarrollo

- [ ] Implementación de caché
- [ ] Pruebas unitarias completas
- [ ] Mejoras en seguridad
  - [ ] Validación más estricta de entradas
  - [ ] Auditorías de seguridad regulares

See the [open issues](https://github.com/omnipro-solutions/saas-app-base/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Las contribuciones hacen que la comunidad de código abierto sea un lugar maravilloso para aprender, inspirar y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "mejora".
¡No olvides darle a este proyecto una estrella! ¡Gracias nuevamente!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a 'pull request'

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top contributors:

<a href="https://github.com/omnipro-solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=omnipro-solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. See `LICENSE.txt` for more information.

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

[Django]: https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white
[Django-url]: https://www.djangoproject.com/
[Python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[Python-url]: https://www.python.org/
[DRF]: https://img.shields.io/badge/Django_REST_Framework-3B8BEB?style=for-the-badge&logo=djangorestframework&logoColor=white
[DRF-url]: https://www.django-rest-framework.org/