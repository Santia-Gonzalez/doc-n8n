# Especificaciones Técnicas

## Detalles Técnicos sobre la Solución OMS

El sistema de gestión de órdenes (OMS) propuesto es una solución SaaS diseñada bajo una arquitectura basada en principios SOLID y una orientación a servicios (SOA). La arquitectura está centrada en microservicios altamente atomizados y de bajo acoplamiento, garantizando una estructura flexible, escalable y mantenible. La infraestructura se gestiona y despliega completamente mediante Terraform en la nube de AWS, asegurando consistencia y automatización en el entorno.

La solución se organiza en un cluster de servicios en ECS, donde se manejan microservicios especializados como:

- **saas-ms-users**: Gestión de usuarios.
- **saas-ms-catalog**: Administración de catálogos.
- **saas-ms-client**: Manejo de datos de clientes.
- **saas-ms-stock**: Control de inventario.
- **saas-ms-sale**: Gestión de ventas.
- **saas-ms-rules**: Gestión de reglas de negocio.
- **saas-ms-task**: Administración de tareas.
- **saas-ms-utilities**: Proporciona funcionalidades auxiliares y de soporte.

Estos microservicios se comunican utilizando el protocolo gRPC. Además, se cuenta con el microservicio **saas-ms-atlas**, que se encarga de transformar las solicitudes de REST API provenientes de API Gateway de AWS a gRPC, permitiendo la interacción interna optimizada entre los microservicios.

Para la integración con terceros y la extensibilidad del sistema, se utiliza un algoritmo de webhooks que reenvía la información derivada de eventos, ofreciendo notificaciones y sincronización en tiempo real. Las integraciones adicionales con ERP, WMS, eCommerce, Marketplaces y Puntos de Venta se gestionan mediante Apps Python utilizando Django y/o FastAPI, las cuales permiten un manejo flexible y personalizado según las necesidades del cliente.

La arquitectura propuesta es composable y headless, permitiendo la integración con múltiples plataformas de comercio como Adobe Commerce, así como aplicaciones específicas para ERP, WMS, POS, TMS y Paqueteras. Estas aplicaciones se construyen en Python con Django o FastAPI y se despliegan como contenedores en ECS, utilizando bases de datos PostgreSQL y Redis, que en conjunto con Celery para la gestión de colas, garantizan la alta disponibilidad y escalabilidad del sistema.

## Seguridad, Escalabilidad y Rendimiento

### Seguridad
- Los puntos de acceso a la infraestructura están limitados a dos: el API Gateway de AWS y un balanceador de carga de AWS. Ambos puntos cuentan con firewalls configurados para proteger los endpoints visibles desde Internet.
- Se utiliza OAuth2 para autenticar las peticiones a los endpoints, asegurando que sólo usuarios autorizados puedan acceder a los recursos.
- Se implementa un sistema de monitoreo y detección de amenazas utilizando tecnologías como New Relic y AWS CloudWatch, ofreciendo visibilidad y control proactivo.
- Se cumplen los estándares de seguridad de la norma ISO/IEC 27001 y se realizan análisis de código automatizados con Bandit en nuestros pipelines de despliegue para asegurar la calidad y la protección de los datos.

### Escalabilidad
- La arquitectura basada en microservicios permite escalar horizontalmente los componentes clave según la demanda.
- La infraestructura soporta múltiples zonas de disponibilidad, garantizando la alta disponibilidad y resistencia ante fallos.
- La solución está optimizada para API Gateway de AWS, permitiendo una gestión eficiente del tráfico de solicitudes y maximizando el rendimiento.

### Rendimiento
- Se utiliza el protocolo gRPC para la comunicación entre microservicios, lo que mejora significativamente los tiempos de respuesta.
- La arquitectura permite la gestión dinámica de recursos, soportando escalado automático en función de la carga.
- La solución incluye un proceso de despliegue blue/green y pipelines automatizados en GitHub Actions, que aseguran una entrega continua y sin interrupciones.

Además, el monitoreo y la trazabilidad se gestionan con herramientas como New Relic y AWS CloudWatch, proporcionando una supervisión en tiempo real de toda la infraestructura. La flexibilidad de las reglas de negocio se asegura mediante la personalización de las aplicaciones intermedias y el uso de inteligencia artificial para la optimización de procesos internos, como la asignación de operarios y la gestión de inventarios.

Finalmente, toda la documentación del producto se encuentra disponible en un dominio privado, y se ofrece un sitio dedicado para la gestión de versiones y el roadmap, garantizando que el cliente tenga acceso a la información más actualizada sobre las mejoras y nuevos lanzamientos.
