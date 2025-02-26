### <a id="readme-top">Repositorio `omnipro-solutions-saas-app-base`</a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<h3 align="center">omnipro-solutions-saas-app-base</h3>

  <p align="center">
    Este repositorio proporciona una base para aplicaciones Django que se conectan a OMS (On-Demand Management System). Es un módulo reutilizable que incluye funcionalidades comunes y configuraciones necesarias para proyectos de este tipo, como autenticación, serialización de datos, manejo de usuarios, etc.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Explora la documentación »</strong></a>
    <br />
    <br />
    &middot;
    <a href="#">Reportar un error</a>
    &middot;
    <a href="#">Solicitar una nueva funcionalidad</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de contenidos</summary>
  <ol>
    <li>
      <a href="#sobre-el-proyecto">Sobre el proyecto</a>
      <ul>
        <li><a href="#construido-con">Construido con</a></li>
      </ul>
    </li>
    <li>
      <a href="#cómo-empezar">Cómo empezar</a>
      <ul>
        <li><a href="#requisitos-previos">Requisitos previos</a></li>
        <li><a href="#instalación">Instalación</a></li>
      </ul>
    </li>
    <li><a href="#uso">Uso</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contribuyendo">Contribuyendo</a></li>
    <li><a href="#licencia">Licencia</a></li>
    <li><a href="#contacto">Contacto</a></li>
    <li><a href="#agradecimientos">Agradecimientos</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## Sobre el proyecto

Este repositorio proporciona una base para aplicaciones Django que se conectan a OMS (On-Demand Management System). Es un módulo reutilizable que incluye funcionalidades comunes y configuraciones necesarias para proyectos de este tipo, como autenticación, serialización de datos, manejo de usuarios, etc.

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

### Construido con

* [Django](https://www.djangoproject.com/)
* [Django REST Framework](http://www.django-rest-framework.org/)

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

<!-- GETTING STARTED -->
## Cómo empezar

Para obtener una copia local del proyecto y ponerlo en marcha, sigue estos pasos:

### Requisitos previos

Este es un ejemplo de cómo listar las dependencias necesarias para usar el software y cómo instalarlas.

### Instalación

1. Clona el repositorio
   ```sh
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   ```
2. Navega al directorio clonado
   ```sh
   cd saas-app-base
   ```
3. Instala las dependencias necesarias
   ```sh
   pip install -r requirements.txt
   ```
4. Configura el entorno de desarrollo copiando `omni_pro_base/settings/local.py` y ajustándolo según sea necesario.
5. Aplica migraciones iniciales
   ```sh
   python make_migrations.py
   python manage.py migrate
   ```

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

<!-- USAGE EXAMPLES -->
## Uso

Este es un ejemplo de cómo usar el proyecto. Puedes encontrar más ejemplos y documentación en la [documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

<!-- ROADMAP -->
## Roadmap

* Mejorar la documentación y los comentarios del código.
* Implementar más pruebas unitarias para asegurar la integridad del sistema.
* Añadir más configuraciones personalizables en `settings/local.py` y `settings/production.py`.
* Mejorar la seguridad, por ejemplo, mejorando el manejo de credenciales sensibles y limitando los permisos de usuario.

Véase [aquí](#) para una lista completa de las propuestas de funcionalidades (y conocidos problemas).

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

Contribuciones son lo que hacen la comunidad open source un lugar tan asombroso para aprender, inspirarse y crear. Cualquier aporte que hagas es **muy apreciado**.

Si tienes una sugerencia que mejore este proyecto, por favor forkea el repositorio e implementa tu sugerencia en un pull request. También puedes simplemente abrir un issue con la etiqueta "enhancement".
No olvides dar al proyecto una estrella! Gracias de antemano!

1. Forkea el Proyecto
2. Crea tu ramificación (`git checkout -b feature/AmazingFeature`)
3. Comitea tus cambios (`git commit -m 'Añade alguna AmazingFeature'`)
4. Empuja a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

### Top contribuyentes:

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia [MIT License](LICENSE.txt). Para más información consulta el archivo `LICENSE`.

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Agradecimientos

* []()
* []()
* []()

<p align="right">(<a href="#readme-top">volver al inicio</a>)</p>