[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![PR][pull-request-shield]][pull-request-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">

<a href="https://github.com/omnipro-solutions/saas-doc-oms.git">
    <img src="https://pngimg.com/uploads/github/github_PNG78.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">CORE OMS Documentation</h3>

  <p align="center">
    Official documentation for the CORE OMS system, providing comprehensive guides and tutorials.
    <br />
    <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Documentación oficial »</strong></a>
    <br />
    <br />
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-doc-oms/issues/bug">Reportar errores</a>
    &middot;
    <a href="https://github.com/omnipro-solutions/saas-doc-oms/issues/features">Solicitar mejoras</a>
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

CORE OMS (Optimized Management System) es una plataforma integral diseñada para gestionar eficazmente los recursos de inventario, usuarios y configuraciones dentro de las organizaciones. Este repositorio alberga la documentación oficial que incluye guías de usuario detalladas, tutoriales interactivos, introducciones en varios idiomas y configuraciones de personalización avanzadas. Con una estructura clara y navegación intuitiva, esta documentación facilita la comprensión y el despliegue del sistema CORE OMS.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Stack tecnológico

El proyecto utiliza diversas tecnologías para asegurar que su documentación sea rica en recursos, interactiva y fácil de mantener:

* [![React][React.js]][React-url]
* [![Docusaurus][Docusaurus.org]][Docusaurus-url]

Además, el sistema CORE OMS puede integrarse con bases de datos como PostgreSQL y Redis para mejorar sus capacidades de gestión.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONFIGURACIÓN LOCAL -->
## Comenzando

Para configurar este proyecto localmente, sigue estas instrucciones paso a paso:

### Prerequisitos

Antes de comenzar, asegúrate de tener instalados los siguientes componentes en tu entorno de desarrollo:
- Node.js (versión 14 o superior)
- npm (o yarn)
- git
- Editor de código como Visual Studio Code

### Instalacion

1. Clone el repositorio
   ```sh
   git clone https://github.com/omnipro-solutions/saas-doc-oms.git
   ```
2. Instala los paquetes NPM
   ```sh
   npm install
   ```
3. Configura tu API en `config.js`
   ```js
   const API_KEY = 'TU_API_AQUI';
   ```
4. Cambia la URL remota de git para evitar push accidentales al proyecto base
   ```sh
   git remote set-url origin omnipro-solutions/saas-doc-oms
   git remote -v # confirma los cambios
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- Ejemplos de uso -->
## Uso

Para utilizar esta documentación, navega a través de las secciones de guías y tutoriales en el sitio web generado. Para una experiencia más personalizada:

- Ajusta los estilos CSS según sea necesario.
- Implementa componentes React para elementos interactivos.

_For more examples, please refer to the [Documentation](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implementar características avanzadas de seguimiento de inventario
- [x] Mejorar la documentación en español
- [ ] Integración con sistemas externos como Salesforce
    - [ ] Crear API RESTful para integraciones

Mira las [ISSUES](https://github.com/omnipro-solutions/saas-doc-oms/issues) para una lista completa de mejoras (problemas conocidos).

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

<a href="https://github.com/omnipro-solutions/saas-doc-oms/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=omnipro-solutions/saas-doc-oms" alt="contrib.rocks image" />
</a>

<!-- LICENCIA -->
## Licencia

Distribuido bajo la licencia MIT. Ve a `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/omnipro-solutions/saas-doc-oms.svg?style=for-the-badge
[contributors-url]: https://github.com/omnipro-solutions/saas-doc-oms/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/omnipro-solutions/saas-doc-oms.svg?style=for-the-badge
[forks-url]: https://github.com/omnipro-solutions/saas-doc-oms/network/members
[issues-shield]: https://img.shields.io/github/issues/omnipro-solutions/saas-doc-oms.svg?style=for-the-badge
[issues-url]: https://github.com/omnipro-solutions/saas-doc-oms/issues
[pull-request-shield]: https://img.shields.io/badge/pull%20requests-0-orange.svg?style=flat&logo=gitpod
[pull-request-url]: https://github.com/omnipro-solutions/saas-doc-oms/pulls
[license-shield]: https://img.shields.io/github/license/omnipro-solutions/saas-doc-oms.svg?style=for-the-badge/
[license-url]: https://github.com/omnipro-solutions/saas-doc-oms/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/company/omni.pro/
[React.js]: https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB
[React-url]: https://reactjs.org/
[Docusaurus.org]: https://img.shields.io/badge/docusaurus-0200FF?style=for-the-badge&logo=docusaurus&logoColor=white
[Docusaurus-url]: https://docusaurus.io/
