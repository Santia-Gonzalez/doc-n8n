
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Issues][issues-shield]][issues-url]
[![project_license][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">
    <a href="https://github.com/Omnipro-Solutions/saas-app-base.git">
        <img src="https://th.bing.com/th/id/OIP.ddlVF3lJNr9URRtdchRLcQHaHa?rs=1&pid=ImgDetMain" alt="Logo" width="80" height="80">
    </a>

    <h3 align="center">saas-app-base</h3>

    <p align="center">
        Librería base para aplicaciones SaaS que se integran con el sistema de gestión Omnipro (OMS).
        <br />
        <a href="https://doc-oms.omni.pro/docs/reglas"><strong>Documentación »</strong></a>
        <br />
        <br />
        &middot;
        <a href="https://github.com/Omnipro-Solutions/saas-app-base/issues">Reportar Bug</a>
        &middot;
        <a href="https://github.com/Omnipro-Solutions/saas-app-base/pulls">Solicitar Característica</a>
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
      <a href="#getting-started">Cómo Iniciar</a>
      <ul>
        <li><a href="#prerequisites">Requisitos Previos</a></li>
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

`saas-app-base` es una librería diseñada para construir aplicaciones SaaS que se integran con el sistema de gestión Omnipro (OMS). Proporciona funcionalidades básicas reutilizables como:

- Autenticación personalizada para usuarios y roles.
- Migraciones automáticas de base de datos.
- Serialización de modelos en formato JSON.
- Verificación de restricciones de CIDR.
- Auditoría y control de permisos.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Construido con

* [![Django][Django.js]][Django-url]
* [![Django REST Framework][DRF.js]][DRF-url]
* [![environs][environs.js]][environs-url]
* [![jazzmin][jazzmin.js]][jazzmin-url]
* [![oauth2_provider][oauth2_provider.js]][oauth2_provider-url]
* [![allow_cidr][allow_cidr.js]][allow_cidr-url]
* [![health_check][health_check.js]][health_check-url]
* [![python-dotenv][python-dotenv.js]][python-dotenv-url]
* [![Redis][Redis.js]][Redis-url]
* [![psycopg2-binary][psycopg2-binary.js]][psycopg2-binary-url]

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- GETTING STARTED -->
## Cómo Iniciar

Estas instrucciones te guiarán en la configuración del proyecto en tu entorno local.

### Requisitos Previos

- Python 3.11 o superior
- pip instalado

### Instalación

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base
   ```

2. Instalar las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

3. Configurar variables de entorno:
   Copia el archivo `.env.example` y configura tus propias credenciales.

4. Ejecutar migraciones:
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

5. Iniciar el servidor:
   ```bash
   python manage.py runserver
   ```

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- USAGE -->
## Uso

`saas-app-base` se puede utilizar como módulo en proyectos Django. Aquí tienes un ejemplo básico:

```python
from omni_pro_base.models import User, OmniModel

# Crear un usuario
user = User.objects.create_user(email='usuario@example.com', password='secreto')

# Utilizar el modelo base
model_instance = OmniModel(titulo='Ejemplo')
model_instance.save()
```

Para más ejemplos y tutoriales, consulta la [Documentación](https://doc-oms.omni.pro/docs/dev/imgs/saas-img-core).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- ROADMAP -->
## Ruta de Desarrollo

- [ ] Mejorar la documentación
- [ ] Implementar pruebas unitarias y de integración
- [ ] Añadir más backend de autenticación OAuth2
- [ ] Integración con AWS S3 para almacenamiento
- [ ] Optimizaciones de rendimiento en migraciones

Para ver una lista completa de características y problemas conocidos, consulta los [Issues](#).

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- CONTRIBUTING -->
## Contribuyendo

¡Contribuciones son bienvenidas! Si tienes sugerencias o correcciones, por favor:

1. Fork el proyecto
2. Crea una rama para tu función (`git checkout -b feature/nombre_funcion`)
3. Realiza tus cambios y commits
4. Envía un pull request

Para reportar problemas, abre un issue con la etiqueta "bug".

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

### Top contribuyentes:

<a href="https://github.com/Omnipro-Solutions/saas-app-base/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Omnipro-Solutions/saas-app-base" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## Licencia

Distribuido bajo la licencia MIT. Consulta `LICENSE.txt` para más información.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- CONTACT -->
## Contacto

Para cualquier pregunta o asistencia, contacta con:

- [LinkedIn](https://www.linkedin.com/company/omni.pro/)
- Correo electrónico: soporte@omni.pro

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Agradecimientos

Agradezco a todas las personas y proyectos que han contribuido al desarrollo de este repositorio.

<p align="right">(<a href="#readme-top">volver arriba</a>)</p>
```

LA PLANTILLA DEBE SER EN ESPAÑOL, PROFESIONAL, CLARA Y EXTENSA. Dame todo el texto plano (sin delimitaciones '''markdown'''). Rellena las URL con los datos necesarios del contexto

Dame una documentación rellenando y mejorando la información contextual previamente con el siguiente formato:

---

# Documentación del Repositorio `saas-app-base`

## 1. Propósito Principal y Funcionalidades

El repositorio `saas-app-base` es una librería base diseñada para construir aplicaciones SaaS que se integran con el sistema de gestión Omnipro (OMS). Su propósito principal es proporcionar una infraestructura sólida y reusable para desarrollos Django, incluyendo:

- **Autenticación:** Implementa mecanismos personalizados para autenticar usuarios.
- **Migraciones:** Facilita la creación y aplicación de migraciones de base de datos.
- **Serialización:** Proporciona clases para serializar modelos en formato JSON.
- **Verificación de CIDR:** Integra middleware para restricciones de red.
- **Seguridad:** Incluye controles de permisos y auditoría.

## 2. Archivos y Carpetas Principales

Aquí tienes una descripción detallada de los archivos y carpetas más importantes:

### **Archivos**
- **`README.md`:** Documentación inicial del proyecto.
- **`LICENSE`:** Licencia MIT que regula el uso del software.
- **`MANIFEST.in`:** Lista de archivos incluidos en la distribución.
- **`make_migrations.py`:** Script para generar migraciones.
- **`requirements.txt`:** Lista de dependencias necesarias.
- **`setup.py`:** Archivo para instalar el paquete como módulo Python.

### **Carpetas**
- **`omni_pro_base/`:** Contiene la implementación principal de la librería.
  - **`admin/`:** Configuraciones del admin.ModelAdmin.
  - **`forms/`:** Formularios personalizados para usuarios.
  - **`migrations/`:** Migraciones de base de datos.
  - **`models/`:** Definiciones de modelos Django.
  - **`serializers/`:** Serializadores para API REST.
  - **`settings/`:** Configuraciones del proyecto.
  - **`static/`:** Archivos estáticos como CSS y JS.
  - **`tests/`:** Pruebas unitarias y de integración.
  - **`views/`:** Vistas para la API.

## 3. Estructura del Código

La arquitectura del código sigue un diseño modular clásico de Django, con la siguiente estructura:

- **Nivel superior:** Contiene los archivos principales como `setup.py`, `requirements.txt`, y el script `make_migrations.py`.
- **`omni_pro_base/`:** Aplicación principal que implementa la librería base.
  - **Modelos (`models/`):** Define la clase base `OmniModel` y el modelo de usuario personalizado `User`.
  - **Vistas (`views/`):** Implementan las API endpoints para usuarios y grupos.
  - **Serializadores (`serializers/`):** Definen cómo los modelos se convierten en datos JSON.
  - **Administración (`admin/`):** Configuran cómo los modelos aparecen en el panel de admin de Django.

## 4. Dependencias y Requerimientos

Para ejecutar el proyecto, se necesitan las siguientes dependencias:

- **Django:** Para el framework web.
- **Django REST Framework (DRF):** Para construir APIs REST.
- **environs:** Para manejar variables de entorno.
- **jazzmin:** Tema moderno para Django admin.
- **oauth2_provider:** Para autenticación OAuth2.
- **allow_cidr:** Middleware para restricciones de red.
- **health_check:** Para monitorear la salud del servidor.
- **Y más...** Consulta el `requirements.txt` para una lista completa.

## 5. Instalación y Configuración

Para instalar y configurar el entorno de desarrollo, sigue estos pasos:

### **Instalación**

1. **Requisitos Previos:**
   - Python >=3.11
   - pip instalado

2. **Clonar Repositorio:**
   ```bash
   git clone https://github.com/Omnipro-Solutions/saas-app-base.git
   cd saas-app-base
   ```

3. **Instalar Dependencias:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configurar Variables de Entorno:**
   Copia el archivo `.env.example` (si existe) o crea un nuevo archivo `.env` con tus configuraciones.

5. **Ejecutar Migraciones:**
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

6. **Iniciar el Servidor:**
   ```bash
   python manage.py runserver
   ```

### **Configuración**

- Configura las variables de entorno necesarias en `.env`:
  - `SECRET_KEY`
  - `DATABASE_URL`
  - `ADMIN_LOGIN`, `ADMIN_PASSWORD`, etc.

## 6. Mejoras y Extensiones Futuras

Posibles áreas para mejorar o extender el proyecto:

1. **Documentación:**
   - Añadir más ejemplos y tutoriales.
2. **Testing:**
   - Implementar pruebas de integración.
3. **Personalización:**
   - Agregar más backend de autenticación.
4. **Integración:**
   - Conectar con más servicios externos (AWS, Google Cloud).
5. **Optimizaciones:**
   - Mejorar el rendimiento de las migraciones y consultas.

## 7. Funcionamiento como Librería

La librería `saas-app-base` actúa como un módulo reusable que puedes importar en otros proyectos Django. Sus módulos principales son:

### **Módulos Principales**

- **`apps.py`:** Configuración de la aplicación.
- **`backends.py`:** Implementación de los backend de autenticación personalizados.
- **`models/`:** Clases base y específicas para el modelo de usuario.
- **`serializers/`:** Serializadores para exposición en API REST.
- **`views/`:** Vistas basadas en clases para la API.

### **Uso**

1. **Importar la Librería:**
   ```python
   from omni_pro_base.models import User, OmniModel
   ```

2. **Configurar en `settings.py`:**
   - Añadir `omni_pro_base` a `INSTALLED_APPS`.
   - Configurar los backends de autenticación.

3. **Utilizar en Aplicaciones:**
   - Hereda de `OmniModel` para crear nuevos modelos.
   - Usa las vistas y serializadores proporcionados para construir APIs.

---

Espero que esta documentación te sea útil para entender y trabajar con el repositorio. Si tienes más preguntas, no dudes en preguntar. 😊
