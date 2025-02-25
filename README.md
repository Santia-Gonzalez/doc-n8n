### Documentación del Software: Librería para Gestión REDIS OMS V3

---

#### 1. Introducción
`saas-lib-redis` es una librería de Python diseñada para facilitar la gestión y el manejo de datos en Redis, un sistema de almacenamiento en memoria NoSQL altamente escalable y rápido. Esta biblioteca proporciona funciones avanzadas para interactuar con Redis, incluyendo operaciones CRUD (Crear, Leer, Actualizar, Borrar) y consultas especializadas.

---

#### 2. Requisitos del Sistema
Para utilizar `saas-lib-redis`, se requieren las siguientes dependencias:

- Python: Versión 3.9 o superior.
- Dependencias de software:
    - hiredis >= 2.2.0, < 3.0.0
    - redis >= 4.0.0, < 5.0.0
    - fakeredis[json] >= 2.0.0, < 3.0.0
    - omni-pro-base >= 0.0.0, <= 2.0.0

---

#### 3. Instalación
Para instalar la librería `saas-lib-redis`, sigue los siguientes pasos:

1. **Clonar el Repositorio:**

   ```bash
   git clone https://github.com/Omnipro-Solutions/saas-lib-redis.git
   cd saas-lib-redis
   ```

2. **Instalar Dependencias:**
   
   ```bash
   pip install -r requirements.txt
   ```

3. **Instalación del Paquete:**

   ```bash
   python setup.py install
   ```

---

#### 4. Uso de la Librería

##### 4.1 Inicialización y Conexión a Redis

Para iniciar una conexión con Redis, se utiliza la clase `RedisManager`:

```python
from omni_pro_redis import RedisManager

redis_manager = RedisManager(host='localhost', port=6379, db=0, redis_ssl=False)
```

##### 4.2 Operaciones CRUD

**Crear (Set):**

Para guardar un objeto JSON en Redis:

```python
data = {"key": "value"}
redis_manager.set_json("my_key", data)
```

**Leer (Get):**

Para obtener un objeto JSON desde Redis:

```python
result = redis_manager.get_json("my_key")
print(result)  # Imprime el contenido del objeto JSON
```

**Actualizar:**
La actualización se realiza al sobrescribir los datos existentes.

**Borrar (Delete):**

Para eliminar una clave de Redis:

```python
redis_manager.delete_hash("my_key")
```

##### 4.3 Manejo de Configuraciones

`saas-lib-redis` proporciona métodos para manejar configuraciones específicas, como AWS S3 y MongoDB.

**Configuración de AWS S3:**

```python
config = redis_manager.get_aws_s3_config(service_id="service1", tenant_code="tenant1")
print(config)  # Imprime la configuración del servicio S3
```

**Configuración de MongoDB:**

```python
mongo_config = redis_manager.get_mongodb_config(service_id="service2", tenant_code="tenant2")
print(mongo_config)  # Imprime la configuración de MongoDB
```

---

#### 5. Clases y Métodos

##### 5.1 RedisConnection

La clase `RedisConnection` proporciona una conexión segura a Redis:

```python
redis_connection = RedisConnection(host='localhost', port=6379, db=0, redis_ssl=False)
with redis_connection as client:
    print(client.ping())  # Verifica la conexión
```

##### 5.2 RedisManager

La clase `RedisManager` proporciona métodos para interactuar con Redis de manera más avanzada:

**Método: get_json**

```python
result = redis_manager.get_json("my_key")
print(result)  # Imprime el contenido del objeto JSON
```

**Método: set_json**

```python
data = {"key": "value"}
redis_manager.set_json("my_key", data)
```

---

#### 6. Ejemplos de Uso

##### Ejemplo 1: Configuración de AWS S3

```python
config = redis_manager.get_aws_s3_config(service_id="service1", tenant_code="tenant1")
print(config["region_name"])  # Imprime la región configurada para el servicio S3
```

##### Ejemplo 2: Obtener Usuarios Administrativos

```python
user_admin = redis_manager.get_user_admin("tenant1")
print(user_admin)  # Imprime los datos del usuario administrativo
```

---

#### 7. Licencia y Atribuciones

`saas-lib-redis` está licenciado bajo la **Licencia MIT**. Para más detalles, consulta el archivo LICENSE en el repositorio.

---

#### 8. Soporte y Contribución

Para reportar problemas o contribuir al proyecto, por favor visita nuestro [repositorio GitHub](https://github.com/Omnipro-Solutions/saas-lib-redis).

---

Esta documentación proporciona una visión general de cómo utilizar la librería `saas-lib-redis` para gestionar datos en Redis. Para más detalles y ejemplos, consulta el código fuente y los comentarios dentro del mismo.

¡Gracias por usar `saas-lib-redis`!