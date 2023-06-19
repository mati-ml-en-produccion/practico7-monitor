# **Model serving**


- Fastapi 
- TF Serving
- Azure services 
  - Container apps, instances.
- Azure ml-studio 
  - model
  - endpoint


## Fast API 

**Documentation:** https://fastapi.tiangolo.com/
**Source Code:** https://github.com/tiangolo/fastapi

FastAPI es un moderno y rápido  (de alto rendimiento) framework para construir APIs con Python 3.6+ basado en las anotaciones de tipo estándar de Python.

### Las características principales de FastAPI incluyen:

**Rápido:** Es muy rápido, casi tan rápido como NodeJS y Go, gracias a Starlette para la parte web y Pydantic para la manipulación de datos.

**Rápido de codificar:** Aumenta la velocidad del desarrollo en aproximadamente un 200% a 300% * (según pruebas internas de los desarrolladores). Gracias a que reduce mucho el tiempo de depuración, gracias a la generación automática de código por el editor, gracias a tener menos errores en producción, etc.

**Automático:** Generación automática de documentación interactiva de la API (con Swagger UI y Redoc) y esquemas JSON para la definición de la API.

**Basado en estándares:** Basado en (y completamente compatible con) los estándares abiertos para APIs: OpenAPI (anteriormente conocido como Swagger) y JSON Schema.

**Basado en anotaciones de tipo Python:** Esto significa que con solo el lenguaje estándar de Python, se declaran una vez los tipos de parámetros, respuesta del cuerpo, etc. Esto tiene un doble propósito, para realizar la validación de datos y para las anotaciones.

**Autenticación y autorización fácil de usar:** Incluye soporte para autenticación con token OAuth2 con contraseña y soporte para roles de usuario con dependencias.

Soporte integrado para pruebas unitarias basadas en PyTest.


# Que vamos a hacer?

**Crear una API usando FastAPI:** Aquí es donde definirás los endpoints de tu API, incluyendo uno para realizar inferencias con tu modelo.

**Dockerizar la aplicación:** Este paso involucra la creación de un Dockerfile y la construcción de una imagen Docker.

**Desplegar en Azure:** Finalmente, deberás cargar tu imagen Docker en un registro de contenedores y desplegarla en Azure.


Paso 1: Crear una API usando FastAPI

Paso 2: Vamos a crear un archivo main.py:

Paso 3: Creamos el Dockerfile


## Build: construye tu imagen Docker

docker build -t model-keras:latest .

MAC:docker build --platform linux/arm64/v8 -t model-keras:latest .

#### Probar el modelo en local
Corremos la imagen: docker run -d -p 8080:80 model-keras:latest

Para eso creamos la notebook test.ipynb para usar la libreria request.

### Deploy en Azure - Custom

Vamos a crear una VM a partir de la ImageGallery utilizada en el práctico 2 ya que ya contiene **Docker y Git dentro.**

Importante, dejarle el puerto 8080 en una inbound rule, ya que este sera el puerto por el cual vamos a acceder a la API.

Accedemos por SSH.

- Clonamos el repo (git clone)
- Buildeamos la imagen (docker build)
- Corremos el contenedor (docker run)
- Probamos internamente si todo esta ok (curl http://0.0.0.0:8080/health)
- Testeamos desde afuera pegandole al IP de la maquina (http://{IP}:8080/health)


