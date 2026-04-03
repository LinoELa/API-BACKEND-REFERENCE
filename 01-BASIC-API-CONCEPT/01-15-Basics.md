# API Basics - Q1 to Q15

## Indice de contenidos

- [1. API](#1-api)
- [2. REST API](#2-rest-api)
- [3. HTTP Methods](#3-http-methods)
- [4. Difference between GET and POST](#4-difference-between-get-and-post)
- [5. Endpoint](#5-endpoint)
- [6. Request and Response](#6-request-and-response)
- [7. JSON](#7-json)
- [8. HTTP Status Code](#8-http-status-code)
- [9. Common HTTP Status Codes](#9-common-http-status-codes)
- [10. RESTful API](#10-restful-api)
- [11. Statelessness](#11-statelessness)
- [12. CRUD](#12-crud)
- [13. API Testing](#13-api-testing)
- [14. Tools for API Testing](#14-tools-for-api-testing)
- [15. Payload](#15-payload)

## Como leer esta guia

Esta version de `Basic` esta mas alineada con el PDF original.
Ahora cada punto incluye definicion, ejemplo real y, cuando aplica, una pista util para entrevistas.

## 1. API

**Definition:** Una API (`Application Programming Interface`) es un conjunto de reglas y protocolos que permite que distintas aplicaciones se comuniquen entre si.

**Real-time Scenario:** Cuando usas una app del tiempo en el movil, la app no guarda el clima dentro de ella. Llama a una API del clima, envia tu ubicacion y recibe los datos actuales para mostrarlos.

**Interview Tip:** Una API se puede explicar como un puente o mensajero entre sistemas.

## 2. REST API

**Definition:** `REST` (`Representational State Transfer`) es un estilo arquitectonico para disenar aplicaciones en red usando metodos HTTP para operar sobre recursos.

**Real-time Scenario:** Una app de reparto de comida puede usar una REST API asi:

```http
GET /restaurants
POST /orders
GET /orders/{id}
DELETE /orders/{id}
```

Lectura rapida:

- `GET /restaurants` = ver restaurantes disponibles
- `POST /orders` = crear un pedido nuevo
- `GET /orders/{id}` = revisar el estado del pedido
- `DELETE /orders/{id}` = cancelar un pedido

## 3. HTTP Methods

**Definition:** Son operaciones estandar del protocolo HTTP para la comunicacion web.

**Real-time Usage:** En un e-commerce:

```http
GET /api/products
POST /api/cart
PUT /api/users/123
DELETE /api/comments/5
PATCH /api/orders/10
```

Lectura rapida:

- `GET` = obtener datos
- `POST` = crear o enviar datos
- `PUT` = reemplazar datos
- `PATCH` = actualizar una parte
- `DELETE` = eliminar

## 4. Difference between GET and POST

**GET**

- se usa para recuperar datos
- los parametros suelen ir en la URL
- se puede guardar en marcadores
- tiene menos capacidad para enviar datos

**POST**

- se usa para enviar datos
- los datos van en el body
- no esta pensado para guardar en marcadores
- soporta mas informacion

**Real-time Examples:**

- `GET`: buscar productos en Amazon, por ejemplo `amazon.com/search?q=laptop`
- `POST`: enviar un formulario de login con usuario y password

## 5. Endpoint

**Definition:** Es una URL especifica donde una API expone una operacion.

**Real-time Example:** En una app bancaria:

```http
GET /api/accounts
GET /api/accounts/{id}
POST /api/transfers
GET /api/transactions
```

Lectura rapida:

- listar cuentas
- ver una cuenta concreta
- iniciar una transferencia
- consultar movimientos

## 6. Request and Response

**Request:** Es lo que el cliente envia al servidor.

```http
POST /api/login HTTP/1.1
Content-Type: application/json

{"username": "john", "password": "pass123"}
```

**Response:** Es lo que el servidor devuelve al cliente.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"token": "abc123", "user": {"id": 1, "name": "John"}}
```

**Idea clave:**

- request = lo que pides o envias
- response = lo que recibes

## 7. JSON

**Definition:** `JSON` (`JavaScript Object Notation`) es un formato ligero para intercambiar datos entre sistemas.

**Real-time Scenario:** Cuando rellenas un formulario de registro, los datos pueden viajar como JSON:

```json
{
  "firstName": "Sarah",
  "lastName": "Chen",
  "email": "sarah@email.com",
  "phone": "+1234567890",
  "address": {
    "street": "123 Main St",
    "city": "San Francisco",
    "zipcode": "94107"
  }
}
```

**Interview Tip:** JSON es popular porque es facil de leer para humanos y de procesar para programas.

## 8. HTTP Status Code

**Definition:** Es un codigo de 3 digitos que indica el resultado de una request HTTP.

**Real-time Examples:**

- `200 OK` = la solicitud salio bien
- `404 Not Found` = la pagina o recurso no existe
- `500 Internal Server Error` = el servidor tiene un fallo
- `403 Forbidden` = no tienes permiso para acceder

## 9. Common HTTP Status Codes

**Success**

- `200 OK` = request correcta
- `201 Created` = recurso creado correctamente
- `204 No Content` = exito sin contenido de respuesta

**Client Errors**

- `400 Bad Request` = datos invalidos
- `401 Unauthorized` = falta autenticacion
- `403 Forbidden` = autenticado, pero sin permiso
- `404 Not Found` = recurso inexistente
- `429 Too Many Requests` = se supero el limite de peticiones

**Server Errors**

- `500 Internal Server Error` = problema interno
- `502 Bad Gateway` = fallo de un servicio aguas arriba
- `503 Service Unavailable` = servicio caido o en mantenimiento

## 10. RESTful API

**Definition:** Es una API que sigue los principios de REST, como `statelessness`, `cacheability` y el uso correcto de metodos HTTP.

**Real-time Scenario - E-commerce API:**

```http
GET /products
POST /products
GET /products/{id}
PUT /products/{id}
PATCH /products/{id}
DELETE /products/{id}
```

Lectura rapida:

- listar productos
- crear producto
- ver detalle
- actualizar completo
- actualizar parcial
- eliminar

## 11. Statelessness

**Definition:** Cada request debe incluir toda la informacion necesaria para que el servidor la entienda y procese. El servidor no debe depender del contexto guardado de requests anteriores.

**Real-time Example:** En una tienda como Amazon:

- Request 1: `GET /products`
- Request 2: `GET /cart` con token
- Request 3: `GET /products/123`

Cada request debe poder entenderse por si sola.

## 12. CRUD

**Definition:** `CRUD` significa `Create`, `Read`, `Update`, `Delete`.

**Real-time Blog System:**

```http
POST /articles
GET /articles/{id}
PUT /articles/{id}
DELETE /articles/{id}
```

Relacion rapida:

- Create = crear
- Read = leer
- Update = actualizar
- Delete = eliminar

## 13. API Testing

**Definition:** Probar una API significa verificar su funcionalidad, rendimiento, seguridad y fiabilidad.

**Real-time Scenario:** En una API de pagos conviene probar:

- respuesta correcta cuando el pago sale bien
- respuesta de error cuando falla
- comportamiento bajo carga
- edge cases

**Interview Tip:** API testing no prueba la UI; prueba el comportamiento de la API.

## 14. Tools for API Testing

Herramientas muy comunes en el PDF:

- `Postman`
- `Swagger / OpenAPI`
- `SoapUI`

Uso rapido:

- `Postman` para lanzar requests manuales
- `Swagger UI` para probar endpoints desde la documentacion
- `SoapUI` muy usado en integraciones y servicios mas formales

## 15. Payload

**Definition:** El `payload` es la informacion que se envia en el body de una request o una response.

**Example:**

```json
{
  "content": "Just launched my new app!",
  "privacy": "public"
}
```

En este caso, ese bloque JSON es el contenido principal que viaja dentro del mensaje.

## Resumen rapido

- API = puente entre aplicaciones
- REST API = estilo para trabajar con recursos usando HTTP
- HTTP methods = acciones sobre recursos
- endpoint = URL especifica de una operacion
- request/response = entrada y salida de la comunicacion
- JSON = formato de intercambio de datos
- status code = resultado de la request
- CRUD = operaciones basicas sobre datos
- payload = datos principales del body

## Siguiente paso

La segunda parte de `Basic` completa `Q16-Q30` con headers, parametros, documentacion, versionado, CORS y autenticacion.
