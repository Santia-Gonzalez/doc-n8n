<a id="readme-top"></a>
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<br />
<div align="center">

<a
href="https://github.com/Omnipro-Solutions/saas-app-base.git">
    <img src="https://pngimg.com/uploads/github/github_PNG78.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">saas-app-base</h3>

  <p align="center">
    Biblioteca de módulos base para aplicaciones SaaS conectadas a OMS
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
    <li><a href="#top">Top Contribuyentes</a></li>
    <li><a href="#license">Licencia</a></li>
  </ol>
</details>

<!-- SOBRE EL PROYECTO -->
## Descripción

El repositorio `omnipro-solutions-saas-app-base` es una biblioteca de módulos base diseñada para facilitar el desarrollo de aplicaciones SaaS que se integran con Open Management System (OMS). Proporciona funcionalidades fundamentales y estructuras necesarias, sirviendo como componente clave en la arquitectura de software de Omnipro Solutions. Este repositorio incluye autenticación, modelos extendidos para auditoría, configuraciones base de Django, integración con Django Rest Framework (drf), y gestión eficiente de migraciones.

### Funcionalidades Principales:

- **Autenticación:** Soporte tanto para mecanismos locales como externos a través de backends personalizados.
- **Modelos y Serializadores:** Modelos básicos extendidos con capacidades adicionales para auditoría, junto con serializadores para manejo eficiente en APIs RESTful.
- **Configuraciones de Django:** Configuraciones base que permiten una rápida inicialización y adaptación a diferentes entornos (desarrollo/producción).
- **Integración con Django Rest Framework:** Facilita la creación de APIs robustas mediante serializers y viewsets predefinidos.
- **Gestión de Migraciones:** Scripts para generar automáticamente migraciones, asegurando que las bases de datos estén sincronizadas con los modelos del código.

### Archivos Principales:

- `README.md`: Descripción general del propósito del repositorio.
- `LICENSE`: Licencia MIT permitiendo uso, modificación y redistribución bajo ciertas condiciones.
- `MANIFEST.in`, `make_migrations.py`, `requirements.txt`, `setup.py`: Componentes esenciales para la gestión de dependencias y configuración del paquete Python.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Stack tecnológico

* [![Python][Python]][Python-url]
* [![Django][Django]][Django-url]
* [![Django Rest Framework][DjangoRestFramework]][DjangoRestFramework-url]
* [![PostgreSQL][PostgreSQL]][PostgreSQL-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Iniciar Proyecto

A continuación, se presentan instrucciones claras para configurar el proyecto en un entorno local.

### Prerequisitos

- Python 3.11 o superior
- PostgreSQL (o SQLite para desarrollo)
- Dependencias de Django y Django Rest Framework

### Instalación

1. Clonar el repositorio:
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base/omnipro-solutions-saas-app-base/
   ```
2. Crear un entorno virtual (recomendado):
   ```sh
   python -m venv env
   source env/bin/activate  # En Windows: env\Scripts\activate
   ```
3. Instalar dependencias:
   ```sh
   pip install -r requirements.txt
   ```
4. Configurar variables de entorno creando un archivo `.env` en el directorio raíz con las configuraciones necesarias (por ejemplo, `SECRET_KEY`, `DATABASE_URL`).
5. Ejecutar migraciones:
   ```sh
   python make_migrations.py
   ```
6. Iniciar servidor de desarrollo:
   ```sh
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Para utilizar la biblioteca, primero asegúrate de haber configurado el entorno local como se describe en las instrucciones anteriores. Luego, puedes comenzar a desarrollar aplicaciones SaaS utilizando los modelos y funcionalidades proporcionados.

_Referencia adicional: [Documentación Oficial](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implementar soporte multi-tenencia
- [ ] Ampliar capacidades de integración con otros sistemas externos
- [ ] Mejorar la capa frontend utilizando frameworks modernos como React o Vue.js

Mira las [ISSUES](https://github.com/Omnipro-Solutions/saas-app-base/issues) para una lista completa de mejoras (problemas conocidos).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Las contribuciones son lo que hacen a la comunidad de código abierto un lugar tan maravilloso para aprender, inspirar y crear. Cualquier contribución que hagas es **muy apreciada**.

Si tienes una sugerencia que haría esto mejor, por favor forkea el repositorio y crea una solicitud de extracción. También puedes simplemente abrir un problema con la etiqueta "mejora".
¡No olvides darle a este proyecto una estrella! ¡Gracias de nuevo!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a 'pull request'

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top Contribuyentes:

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENCIA -->
## Licencia

Distribuido bajo la licencia MIT. Consulta `LICENSE.txt` para más información.

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
[Python]: https://img.shields.io/badge/python-3.11-blue
[Python-url]: https://www.python.org/downloads/release/python-3110/
[Django]: https://img.shields.io/badge/django-5.0-green
[Django-url]: https://www.djangoproject.com/download/
[DjangoRestFramework]: https://img.shields.io/badge/DRF-3.14-red
[DjangoRestFramework-url]: https://www.django-rest-framework.org/
[PostgreSQL]: https://img.shields.io/badge/postgresql-15-blueviolet
[PostgreSQL-url]: https://www.postgresql.org/download/