<a id="readme-top"></a>
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<br />
<div align="center">

<a href="https://github.com/Omnipro-Solutions/saas-app-base.git">
    <img src="https://th.bing.com/th/id/OIP.ddlVF3lJNr9URRtdchRLcQHaHa?rs=1&pid=ImgDetMain" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Base de Aplicación SaaS para Omnipro Solutions</h3>

  <p align="center">
    Biblioteca base diseñada para facilitar la creación y gestión de aplicaciones SaaS dentro del ecosistema de Omnipro, proporcionando funcionalidades comunes como autenticación de usuarios, interacción HTTP y configuraciones personalizadas.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explore la documentación »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/Omnipro-Solutions/saas-app-base/issues">Reportar un Bug</a>
    &middot;
    <a href="https://github.com/Omnipro-Solutions/saas-app-base/pullrequest">Solicitar una Función</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de Contenidos</summary>
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
        <li><a href="#prerequisites">Requisitos Previos</a></li>
        <li><a href="#installation">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#usage">Uso</a></li>
    <li><a href="#roadmap">Ruta de Desarrollo</a></li>
    <li><a href="#contributing">Contribuciones</a></li>
    <li><a href="#license">Licencia</a></li>
    <li><a href="#contact">Contacto</a></li>
    <li><a href="#acknowledgments">Agradecimientos</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## Acerca del Proyecto

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca base diseñada para facilitar la creación y gestión de aplicaciones SaaS dentro del ecosistema de Omnipro Solutions. Proporciona un conjunto de funcionalidades comunes que pueden ser reutilizadas en múltiples proyectos, tales como:

- **Gestión de Usuarios**: Autenticación y autorización mediante backends personalizados.
- **Interacción HTTP**: Funciones para realizar solicitudes HTTP y procesar respuestas.
- **Configuración del Proyecto**: Archivos de configuración para diferentes entornos (base, local, producción).
- **Modelos y Serializadores**: Definiciones de modelos básicos y serializadores para la API REST.
- **Admin y Formularios Personalizados**: Interfaces administrativas personalizadas y formularios para la gestión de usuarios.

Este repositorio está construido sobre Django y proporciona una base sólida para desarrollar aplicaciones SaaS, con un enfoque en la reutilización de código y facilidad de extensión.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Construido con

Este proyecto fue construido utilizando las siguientes tecnologías:

* [![Python][python]][python-url]
* [![Django][django]][django-url]
* [![PostgreSQL][postgresql]][postgresql-url]

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- GETTING STARTED -->
## Empezando

A continuación se presentan instrucciones claras y precisas para configurar el proyecto en tu entorno local.

### Requisitos Previos

Para ejecutar este repositorio, asegúrate de tener instalado lo siguiente:

- Python 3.11 o superior
- Django 5.0
- PostgreSQL

### Instalación

1. Clonar el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```
2. Crear un entorno virtual (Opcional):
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: env\Scripts\activate
   ```
3. Instalar dependencias:
   ```sh
   pip install -r requirements.txt
   ```
4. Configurar variables de entorno:
   Crea un archivo `.env` en la raíz del proyecto y define las variables necesarias, como `SECRET_KEY`, `DATABASE_URL`, etc.
5. Generar migraciones:
   ```sh
   python make_migrations.py
   ```
6. Ejecutar el servidor de desarrollo:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- USAGE EXAMPLES -->
## Uso

A continuación, se presenta un ejemplo básico de cómo utilizar la biblioteca.

Para más ejemplos, por favor refiérase a la [Documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- ROADMAP -->
## Ruta de Desarrollo

- [ ] Implementación del sistema de caché
- [ ] Mejoras en la seguridad
- [ ] Monitoreo y logging avanzados
  - [ ] Integración con herramientas de monitoreo
- [ ] Pruebas automatizadas completas

Para ver una lista completa de características propuestas (y problemas conocidos), consulte los [issues abiertos](#).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- CONTRIBUTING -->
## Contribuciones

Las contribuciones son lo que hacen a la comunidad de código abierto un lugar tan increíble para aprender, inspirarse y crear. Cualquier contribución que hagas es **altamente apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un issue con la etiqueta "mejora".
¡No olvides darle al proyecto una estrella! ¡Gracias de nuevo!

1. Fork del Proyecto
2. Crea tu Rama de Característica (`git checkout -b feature/AmazingFeature`)
3. Comita tus Cambios (`git commit -m 'Add some AmazingFeature'`)
4. Empuja a la Rama (`git push origin feature/AmazingFeature`)
5. Abre una 'solicitud de extracción'

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Principales contribuidores:

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. Consulta el archivo `LICENSE.txt` para más información.

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

[pic-python]: https://img.shields.io/badge/python-3.11-blue
[pic-django]: https://img.shields.io/badge/django-5.0-green
[pic-postgresql]: https://img.shields.io/badge/postgresql-14-red

[python-url]: https://www.python.org/
[django-url]: https://www.djangoproject.com/
[postgresql-url]: https://www.postgresql.org/