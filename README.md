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
    <img src="https://th.bing.com/th/id/OIP.ddlVF3lJNr9URRtdchRLcQHaHa?rs=1&pid=ImgDetMain" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Base de Aplicación SaaS para Omnipro Solutions</h3>

  <p align="center">
    Biblioteca base diseñada para facilitar la creación y gestión de aplicaciones SaaS conectadas a OMS (Omnipro Solutions).
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explora los documentos »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-base/issues">Reportar un error</a>
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-app-base/pullrequest">Solicitar una característica</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de Contenidos</summary>
  <ol>
    <li>
      <a href="#about-the-project">Acerca del Proyecto</a>
      <ul>
        <li><a href="#built-with">Construido Con</a></li>
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
    <li><a href="#contact">Contacto</a></li>
    <li><a href="#acknowledgments">Agradecimientos</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## Acerca del Proyecto

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca base diseñada para facilitar la creación y gestión de aplicaciones SaaS conectadas a OMS (Omnipro Solutions). Proporciona un conjunto de funcionalidades comunes que pueden ser reutilizadas en múltiples proyectos dentro del ecosistema de Omnipro, mejorando así la eficiencia y consistencia. Las principales características incluyen gestión de usuarios, interacción HTTP, configuración para diferentes entornos, modelos y serializadores para APIs REST, y interfaces administrativas personalizadas.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Construido Con

Este proyecto fue construido usando:

* [![Python][python]][python-url]
* [![Django][django]][django-url]
* [![Djangorestframework][djangorestframework]][djangorestframework-url]

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- GETTING STARTED -->
## Empezando

Sigue estas instrucciones para configurar el proyecto en tu entorno local.

### Requisitos previos

Asegúrate de tener instalado:

- Python 3.11 o superior
- Django 5.0

### Instalación

1. Clona el repositorio
   ```sh
   git clone https://github.com/omnipro-solutions/saas-app-base.git
   cd saas-app-base/
   ```
2. Crea un entorno virtual (opcional)
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: env\Scripts\activate
   ```
3. Instala las dependencias
   ```sh
   pip install -r requirements.txt
   ```
4. Configura las variables de entorno creando un archivo `.env` en la raíz del proyecto y define las variables necesarias, como `SECRET_KEY`, `DATABASE_URL`, etc.
5. Genera migraciones
   ```bash
   python make_migrations.py
   ```
6. Ejecuta el servidor de desarrollo
   ```bash
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- USAGE EXAMPLES -->
## Uso

Para utilizar esta biblioteca, puedes integrarla en tus proyectos Django y aprovechar las funcionalidades comunes que ofrece. Por ejemplo, puedes usar los backends personalizados para autenticación de usuarios o las funciones HTTP para realizar solicitudes a APIs externas.

Para más ejemplos, por favor refiérete a la [Documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- ROADMAP -->
## Ruta de Desarrollo

- [ ] Implementación del caché
- [ ] Mejoras en la seguridad
- [ ] Monitoreo y logging avanzados
- [ ] Pruebas automatizadas

Ver los [issues abiertos](https://github.com/omnipro-solutions/saas-app-base/issues) para una lista completa de características propuestas (y problemas conocidos).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Las contribuciones hacen que la comunidad de código abierto sea un lugar maravilloso para aprender, inspirarse y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un issue con la etiqueta "mejora".
¡No olvides darle al proyecto una estrella! ¡Gracias nuevamente!

1. Fork del Proyecto
2. Crea tu rama de característica (`git checkout -b feature/AmazingFeature`)
3. Realiza tus cambios y confirma (`git commit -m 'Add some AmazingFeature'`)
4. Empuja a la rama (`git push origin feature/AmazingFeature`)
5. Abre una solicitud de extracción

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Top contributors:

<a href="https://github.com/omnipro-solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=omnipro-solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. Consulta el archivo `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

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
[python]: https://img.shields.io/badge/python-3.11-blue
[python-url]: https://www.python.org/
[django]: https://img.shields.io/badge/django-5.0-green
[django-url]: https://www.djangoproject.com/
[djangorestframework]: https://img.shields.io/badge/djangorestframework-3.14-red
[djangorestframework-url]: https://www.django-rest-framework.org/