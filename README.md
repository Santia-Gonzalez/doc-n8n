A continuación, se presenta un `README.md` detallado para el proyecto `saas-lib-redis`. Este archivo proporciona una descripción clara y concisa del propósito del software, instrucciones de instalación, configuración inicial y explicaciones sobre la estructura del proyecto. Se incluye toda su funcionalidad y las herramientas adicionales utilizadas dentro del mismo.

---

# saas-lib-redis

**Librería para gestión REDIS OMS V3**

## Objetivos
La librería `saas-lib-redis` proporciona una capa de abstracción sobre Redis que facilita la gestión y manipulación de datos en un entorno empresarial SaaS (Software as a Service).

### Características Principales:
- **Interfaz para gestionar conexiones Redis.**
- **Administrador de recursos JSON en Redis.**
- **Configuraciones específicas para servicios AWS como Cognito, S3 y otros.**
- **Acceso seguro a datos sensibles usando Redis.**

## Instalación

1. Asegúrate de tener Python 3.9 o superior instalado en tu entorno.
2. Clona el repositorio:
   ```bash
   git clone https://github.com/Omnipro-Solutions/saas-lib-redis.git
   cd saas-lib-redis
   ```
3. Instala las dependencias del proyecto mediante pip:
   ```bash
   pip install -r requirements.txt
   ```

## Inicialización y Uso

### Configuración Básica:

1. Importa el módulo principal `omni_pro_redis.redis` en tu script o aplicación.
2. Crea una instancia de `RedisManager`, proporcionando la configuración necesaria para conectarte a Redis.

```python
from omni_pro_redis import redis

# Ejemplo de inicialización con Redis local
redis_manager = redis.RedisManager(
    host="localhost",
    port=6379,
    db=0,
    redis_ssl=False  # Indica si la conexión a Redis es segura (SSL)
)

# Usar la instancia para obtener y establecer datos en Redis.
```

### Uso de Métodos:

- **Obtener Datos JSON:** `get_json(key, *args, no_escape=False)`

```python
data = redis_manager.get_json('my_key')
print(data)
```

- **Establecer Datos JSON:** `set_json(key, json_obj)`
   
```python
redis_manager.set_json('new_key', {'field': 'value'})
```

- **Cambiar Base de Datos:** `change_db(new_db)`

```python
redis_manager.change_db(1)
print(redis_manager.get_connection().db)
```

### Configuraciones Específicas:

Para servicios como AWS Cognito, S3 y MongoDB, puedes obtener configuraciones específicas utilizando métodos proporcionados.

#### Ejemplo: Obtener Configuración de AWS Cognito

```python
cognito_config = redis_manager.get_aws_cognito_config('service_id', 'tenant_code')
print(cognito_config)
```

## Estructura del Proyecto

- **`README.md`:** Documentación principal del proyecto.
- **`LICENSE`:** Licencia MIT del software.
- **`requirements.txt`:** Dependencias necesarias para el funcionamiento del proyecto.
- **`setup.py`:** Script de instalación y configuración del paquete.
- **`omni_pro_redis/redis.py`:** Contiene la implementación principal de `RedisManager`.
  - **Clases:**
    - `RedisConnection:` Maneja conexiones a Redis.
    - `FakeRedisServer:` Implementa un servidor falso para pruebas unitarias.
    - `RedisManager:` Proporciona métodos y funciones para gestionar datos en Redis.

## Herramientas Adicionales

- **Hiredis:** Un cliente de Redis escrito en C++ para mejorar el rendimiento de las operaciones de bajo nivel.
- **Fakeredis:** Una simulación de Redis escrita en Python, útil para pruebas unitarias y desarrollo local sin depender de un servidor Redis real.
- **Omni-pro-base:** Un conjunto de utilidades y funciones básicas utilizadas por `saas-lib-redis`.

## Contribución

No se aceptan contribuciones al proyecto desde este archivo README. Si necesitas colaborar, por favor contáctate con los desarrolladores del equipo OMNI.PRO.

---

Este README.md proporciona una descripción completa de la funcionalidad y estructura del proyecto `saas-lib-redis`, asegurando que el usuario pueda entender fácilmente cómo funciona la librería y qué herramientas adicionales son necesarias para su uso.