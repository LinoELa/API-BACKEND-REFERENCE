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

Esta primera parte esta pensada para entender los conceptos basicos de APIs con palabras simples.
Los titulos se mantienen en ingles porque asi suelen aparecer en entrevistas, cursos y documentacion.

## 1. API

API significa `Application Programming Interface`.
Una API es un conjunto de reglas que permite que dos sistemas se comuniquen entre si.

En simple: una aplicacion pide algo y otra aplicacion responde.

Real-time Scenario: Cuando usas una app del clima en el movil, la app no tiene el clima guardado dentro. Llama a una API del tiempo, envia tu ubicacion y recibe la informacion actual para mostrarla.

Idea clave: una API es el puente entre dos partes de software.

## 2. REST API

Una `REST API` es una API que sigue el estilo REST para trabajar con recursos por medio de HTTP.

En una REST API, los datos suelen representarse como recursos:

- `/users`
- `/products`
- `/orders`

Cada recurso se consulta o modifica usando metodos HTTP como `GET`, `POST`, `PUT`, `PATCH` y `DELETE`.

Real-time Scenario: Una app de reparto de comida puede usar una REST API asi:

```http
GET /restaurants
POST /orders
GET /orders/{id}
DELETE /orders/{id}
```

En ese escenario, las operaciones habituales son:

- `GET /restaurants`: ver restaurantes disponibles
- `POST /orders`: crear un pedido nuevo
- `GET /orders/{id}`: revisar el estado del pedido
- `DELETE /orders/{id}`: cancelar un pedido

## 3. HTTP Methods

Los `HTTP methods` indican la accion que queremos hacer sobre un recurso.

Los mas comunes son:

- `GET`: obtener datos
- `POST`: crear datos
- `PUT`: reemplazar datos
- `PATCH`: actualizar parte de un dato
- `DELETE`: eliminar datos

Real-time Usage: En un e-commerce:

```http
GET /api/products
POST /api/cart
PUT /api/users/123
DELETE /api/comments/5
PATCH /api/orders/10
```

Ejemplo:

```http
GET /users
POST /users
DELETE /users/10
```

## 4. Difference between GET and POST

`GET` y `POST` son dos metodos HTTP muy usados, pero no sirven para lo mismo.
`GET` se usa para pedir informacion y `POST` se usa para enviar informacion, normalmente para crear un recurso nuevo.

Diferencias importantes:

- `GET` suele enviar datos en la URL
- `POST` suele enviar datos en el body de la peticion
- `GET` se usa para lectura
- `POST` se usa para creacion o envio de datos

Real-time Examples:

- `GET`: buscar productos en Amazon, por ejemplo `amazon.com/search?q=laptop`
- `POST`: enviar un formulario de login con usuario y password

Ejemplo:

```http
GET /products
POST /products
```

## 5. Endpoint

Un `endpoint` es una direccion especifica de una API a la que hacemos una solicitud.

Ejemplo simple:

```http
GET /users/5
```

Aqui, `/users/5` es el endpoint.

Real-time Example: En una aplicacion bancaria, algunos endpoints comunes pueden ser:

```http
GET /api/accounts
GET /api/accounts/{id}
POST /api/transfers
GET /api/transactions
```

Idea simple: si la API fuera una casa, cada endpoint seria una puerta distinta para una accion distinta.

## 6. Request and Response

Una `request` es la peticion que el cliente envia a la API.
Una `response` es la respuesta que la API devuelve al cliente.

Ejemplo real de login:

Request:

```http
POST /api/login HTTP/1.1
Content-Type: application/json

{"username": "john", "password": "pass123"}
```

Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"token": "abc123", "user": {"id": 1, "name": "John"}}
```

Idea clave:

- `request` = lo que pedimos o enviamos
- `response` = lo que recibimos

## 7. JSON

`JSON` significa `JavaScript Object Notation`.
Es un formato de texto muy usado para intercambiar datos entre cliente y servidor.

Real-time Scenario: Cuando rellenas un formulario de registro, los datos pueden convertirse a JSON asi:

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

JSON es popular porque es facil de leer para personas y facil de procesar para programas.

## 8. HTTP Status Code

Un `HTTP status code` es un numero que indica el resultado de una solicitud HTTP.

Le dice al cliente si todo salio bien, si hubo un error o si hace falta algo mas.

Real-time Examples:

- `200 OK`: la solicitud salio bien
- `404 Not Found`: el recurso no fue encontrado
- `500 Internal Server Error`: error interno del servidor
- `403 Forbidden`: no tienes permiso para acceder

## 9. Common HTTP Status Codes

Los `HTTP status codes` mas comunes aparecen una y otra vez en APIs reales y conviene reconocerlos rapido.

Success:

- `200 OK`: la solicitud salio bien
- `201 Created`: el recurso fue creado correctamente
- `204 No Content`: exito, pero sin contenido de respuesta

Client Errors:

- `400 Bad Request`: la peticion es invalida
- `401 Unauthorized`: falta autenticacion
- `403 Forbidden`: autenticado, pero sin permiso
- `404 Not Found`: el recurso no existe
- `429 Too Many Requests`: se supero el limite de peticiones

Server Errors:

- `500 Internal Server Error`: error del servidor
- `502 Bad Gateway`: fallo de un servicio aguas arriba
- `503 Service Unavailable`: servicio caido o en mantenimiento

Buena practica: entender estos codigos ayuda a depurar mas rapido.

## 10. RESTful API

Una `RESTful API` es una API que aplica correctamente los principios de REST.

Normalmente significa:

- usa recursos con URLs claras
- usa metodos HTTP de forma correcta
- trabaja sin estado entre peticiones
- devuelve respuestas consistentes

Real-time Scenario - E-commerce API:

```http
GET /products
POST /products
GET /products/{id}
PUT /products/{id}
PATCH /products/{id}
DELETE /products/{id}
```

Ejemplo mas RESTful:

```http
GET /users
GET /users/7
POST /users
PATCH /users/7
DELETE /users/7
```

## 11. Statelessness

`Statelessness` significa que cada peticion debe contener toda la informacion necesaria para ser entendida.

El servidor no deberia depender de recordar peticiones anteriores para procesar la actual.

Real-time Example: Cuando navegas productos en Amazon:

- Request 1: `GET /products`
- Request 2: `GET /cart` con token
- Request 3: `GET /products/123`

Idea clave: cada request se entiende por si sola.

## 12. CRUD

`CRUD` representa las cuatro operaciones basicas sobre datos:

- `Create`: crear
- `Read`: leer
- `Update`: actualizar
- `Delete`: eliminar

Relacion comun con HTTP:

| CRUD   | HTTP Method |
| ------ | ----------- |
| Create | POST        |
| Read   | GET         |
| Update | PUT/PATCH   |
| Delete | DELETE      |

Real-time Blog System:

```http
POST /articles
GET /articles/{id}
PUT /articles/{id}
DELETE /articles/{id}
```

## 13. API Testing

`API testing` es el proceso de comprobar que una API funciona correctamente.

Se prueba, por ejemplo:

- si devuelve la informacion esperada
- si responde con el status correcto
- si maneja bien errores
- si valida datos de entrada
- si cumple con seguridad y rendimiento

Real-time Scenario: En una API de pagos conviene probar casos de exito, fallo, carga y edge cases.

No se prueba la interfaz visual, se prueba el comportamiento de la API.

## 14. Tools for API Testing

Las herramientas de API testing ayudan a probar APIs de forma manual o automatizada.

Algunas herramientas comunes para probar APIs son:

- `Postman`
- `Swagger / OpenAPI`
- `SoapUI`

Otras herramientas utiles en proyectos modernos son:

- `Insomnia`
- `curl`
- `Thunder Client`

## 15. Payload

El `payload` es la informacion principal que se envia en una peticion o en una respuesta.

Muchas veces, cuando hablamos de payload, nos referimos al `body`.

Real-time Example: En una red social o app de contenido, un payload podria verse asi:

```json
{
  "content": "Just launched my new app!",
  "privacy": "public"
}
```

Ese bloque JSON es el contenido util que viaja dentro del mensaje.

## Resumen rapido

- API = puente entre sistemas
- REST = estilo para organizar APIs con recursos
- HTTP methods = acciones
- endpoint = ruta especifica
- request/response = peticion y respuesta
- JSON = formato de datos
- status code = resultado de la solicitud
- CRUD = operaciones basicas sobre datos
- payload = informacion que se envia o recibe

## Siguiente paso

La siguiente parte natural de esta seccion es `Q16-Q30`, donde entran headers, parametros, documentacion, versionado, CORS y autenticacion.
