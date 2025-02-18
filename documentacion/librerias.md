# Listado de Librerías y Licencias

## Librerías en el Core

### Librería Base

La biblioteca **SaaS-Lib-Base** es un proyecto de software diseñado para ofrecer una base sólida y modular para el desarrollo de sistemas Software as a Service (SAAS) utilizando Python. Este repositorio incorpora múltiples configuraciones, herramientas de desarrollo y componentes de código para facilitar la creación, mantenimiento y despliegue de servicios en la nube. Con énfasis en la calidad del código, seguridad, manejo de excepciones, solicitudes HTTP y configuraciones, la biblioteca provee un conjunto de módulos escritos en Python que cumplen con las mejores prácticas del desarrollo moderno.

| Librería                | Versión                | Autor                  | Repositorio Público         | Tipo de Licencia         |
|-------------------------|------------------------|------------------------|-----------------------------|--------------------------|
| mongoengine             | <=0.27.0,>=0.20.0      | Harry Marr             | mongoengine                 | MIT                      |
| pymongo                 | 4.8.0                  | MongoDB, Inc.          | pymongo                     | Apache 2.0               |
| protobuf                | <5.0.0,>=3.0.0         | Google                 | protobuf                    | BSD                      |
| unicode                 | <=3.0,>=1.0            | Tomaz Solc             | unicode                     | Perl Artistic License    |
| marshmallow             | <4.0.0,>=3.0.0         | Steven Loria           | marshmallow                 | MIT                      |
| SQLAlchemy              | <3.0.0,>=1.3.0         | Michael Bayer          | sqlalchemy                  | MIT                      |
| requests                | 2.31.0                 | Kenneth Reitz          | requests                    | Apache 2.0               |
| requests-oauthlib       | 2.0.0                  | Requests Team          | requests-oauthlib           | Apache 2.0               |
| python-json-logger      | 2.0.7                  | Robert Singer          | python-json-logger          | BSD 3-Clause             |
| pytest                  | 7.4.2                  | Holger Krekel et al.   | pytest                      | MIT                      |

### Librería Redis

La biblioteca **SaaS-Lib-Redis** está diseñada para simplificar y optimizar la interacción con Redis. Proporciona configuraciones predefinidas, manejo eficiente de conexiones, soporte para operaciones asincrónicas y herramientas para la gestión de datos en memoria. Su diseño modular asegura una integración fluida con otros componentes, facilitando el almacenamiento en caché, la gestión de colas y otras funcionalidades clave en sistemas distribuidos.

| Librería                | Versión                | Autor                  | Repositorio Público         | Tipo de Licencia         |
|-------------------------|------------------------|------------------------|-----------------------------|--------------------------|
| hiredis                 | <3.0.0,>=2.2.0         | Redis Developers       | hiredis                     | BSD                      |
| redis                   | <5.0.0,>=4.0.0         | Redis Developers       | redis                       | MIT                      |
| fakeredis[json]         | <3.0.0,>=2.0.0         | James Saryerwinnie     | fakeredis                   | MIT                      |
| omni-pro-base           | <=2.0.0,>=0.0.0        | Omni.pro               | omni-pro-base               | MIT                      |

### Librería gRPC

La biblioteca **SaaS-Lib-GRPC** facilita la comunicación eficiente y segura entre microservicios mediante gRPC en la arquitectura OMS V3. Proporciona herramientas para gestionar contratos proto, serialización de datos, autenticación y registro de errores, optimizando la implementación de servicios distribuidos con un enfoque modular y escalable.

| Librería                | Versión                | Autor                  | Repositorio Público         | Tipo de Licencia         |
|-------------------------|------------------------|------------------------|-----------------------------|--------------------------|
| grpcio                  | 1.56.0                 | Google                 | grpc                        | Apache 2.0               |
| grpcio-tools            | 1.56.0                 | Google                 | grpc                        | Apache 2.0               |
| grpcio-reflection       | 1.56.0                 | Google                 | grpc                        | Apache 2.0               |
| grpcio-health-checking  | 1.56.0                 | Google                 | grpc                        | Apache 2.0               |
| omni-pro-base           | <=2.0.0,>=0.0.0        | omni.pro               | omni-pro-base               | MIT                      |
| omni-pro-redis          | <=2.0.0,>=0.0.0        | omni.pro               | omni-pro-redis              | MIT                      |

### Librería Omni-Pro

**Saas MS Library** es una biblioteca de Python diseñada para ser una utilidad para los microservicios de OMS. Esta biblioteca proporciona una solución fácil de usar y altamente personalizable para reutilizar utilidades y clientes de aplicaciones, lo que permite a los desarrolladores centrarse en crear el microservicio más eficiente y escalable.

Con Saas MS Library, podrá manejar bases de datos y clientes de AWS. Nuestra librería es compatible con Python 3.10 y versiones posteriores, y está en constante desarrollo para mejorar su rendimiento y ampliar su funcionalidad.

**Funciones**
- Controlador de bases de datos (MongoDB, Redis, PostgreSQL, etc.)
- Controlador de clientes de AWS (Cognito, S3, etc.)

| Librería                | Versión                | Autor                  | Repositorio Público         | Tipo de Licencia         |
|-------------------------|------------------------|------------------------|-----------------------------|--------------------------|
| boto3                   | >=1.20.0, <=1.50.0     | Amazon Web Services    | boto3                       | Apache 2.0               |
| sqlalchemy-utils        | 0.41.1                 | Michael Bayer          | pypi-SQLAlchemy-Utils       | BSD                      |
| networkx                | 3.1                    | NetworkX Developers    | networkx                    | BSD                      |
| omni-pro-base           | <=2.0.0,>=0.0.0        | omni.pro               | omni-pro-base               | MIT                      |
| omni-pro-redis          | <=2.0.0,>=0.0.0        | omni.pro               | omni-pro-redis              | MIT                      |
| omni-pro-grpc           | <=2.0.0,>=0.0.0        | omni.pro               | omni-pro-grpc               | MIT                      |
| apache-airflow-client   | 2.8.0                  | Apache Software Foundation | airflow-client       | Apache 2.0               |
| newrelic                | 9.10.0                 | New Relic, Inc.        | newrelic                    | Apache 2.0               |
| alembic                 | 1.11.2                 | Michael Bayer          | alembic                     | MIT                      |
| blinker                 | 1.7.0                  | Jason Kirtland         | blinker                     | MIT                      |
| celery                  | 5.4.0                  | Celery Project         | celery                      | BSD                      |

## Librerías en Django

### Librería Apps Base

La librería **omni-pro-app-base** facilita la integración y comunicación eficiente entre diferentes módulos de una aplicación en la arquitectura que nos ofrece Django Rest Framework. Ofrece herramientas avanzadas para gestionar la configuración del entorno, mejorar la interfaz de administración, y optimizar la