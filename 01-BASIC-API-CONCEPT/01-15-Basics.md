# API Basics - Q1 to Q15

## Indice de contenidos

- [API Basics - Q1 to Q15](#api-basics---q1-to-q15)
  - [Indice de contenidos](#indice-de-contenidos)
  - [Como leer esta guia](#como-leer-esta-guia)
- [1. API](#1-api)
- [2. REST API](#2-rest-api)
- [3. HTTP Methods](#3-http-methods)
  - [4. Difference between GET and POST](#4-difference-between-get-and-post)
- [5. Endpoint](#5-endpoint)
- [6. Request and Response](#6-request-and-response)
- [7. JSON](#7-json)
- [8. HTTP Status Code](#8-http-status-code)
  - [9. Common HTTP status codes](#9-common-http-status-codes)
- [10. RESTful API](#10-restful-api)
- [11. Statelessness](#11-statelessness)
- [12. CRUD](#12-crud)
- [13. API Testing](#13-api-testing)
  - [14. Tools for API testing](#14-tools-for-api-testing)
- [15. Payload](#15-payload)
  - [Resumen rapido](#resumen-rapido)
  - [Siguiente paso](#siguiente-paso)

## Como leer esta guia

Esta primera parte esta pensada para entender los conceptos basicos de APIs con palabras simples.
Los titulos se mantienen en ingles porque asi suelen aparecer en entrevistas, cursos y documentacion.

## 1. API

API significa `Application Programming Interface`.
Una API es un conjunto de reglas que permite que dos sistemas se comuniquen entre si.

En simple: una aplicacion pide algo y otra aplicacion responde.

Ejemplo: una app del clima usa una API para pedir la temperatura actual de Madrid.

Idea clave: la API es el puente entre dos partes de software.

## 2. REST API

Una `REST API` es una API que sigue el estilo REST para trabajar con recursos por medio de HTTP.

En una REST API, los datos suelen representarse como recursos:

- `/users`
- `/products`
- `/orders`

Cada recurso se consulta o modifica usando metodos HTTP como `GET`, `POST`, `PUT`, `PATCH` y `DELETE`.

## 3. HTTP Methods

Los `HTTP methods` indican la accion que queremos hacer sobre un recurso.

Los mas comunes son:

- `GET`: obtener datos
- `POST`: crear datos
- `PUT`: reemplazar datos
- `PATCH`: actualizar parte de un dato
- `DELETE`: eliminar datos

Ejemplo:

```http
GET /users
POST /users
DELETE /users/10
```

## 4. Difference between GET and POST

`GET` se usa para pedir informacion.
`POST` se usa para enviar informacion y normalmente crear un nuevo recurso.

Diferencias importantes:

- `GET` suele enviar datos en la URL.
- `POST` suele enviar datos en el body de la peticion.
- `GET` se usa para lectura.
- `POST` se usa para creacion o envio de datos.

Ejemplo:

```http
GET /products
POST /products
```

## 5. Endpoint

Un `endpoint` es una direccion especifica de una API a la que hacemos una solicitud.

Ejemplo:

```http
GET /users/5
```

Aqui, `/users/5` es el endpoint.

Idea simple: si la API fuera una casa, cada endpoint seria una puerta distinta para una accion distinta.

## 6. Request and Response

Una `request` es la peticion que el cliente envia a la API.
Una `response` es la respuesta que la API devuelve al cliente.

Ejemplo basico:

Cliente envia:

```http
GET /users/5
```

Servidor responde:

```json
{
  "id": 5,
  "name": "Ana"
}
```

Idea clave:

- `request` = lo que pedimos
- `response` = lo que recibimos

## 7. JSON

`JSON` significa `JavaScript Object Notation`.
Es un formato de texto muy usado para intercambiar datos entre cliente y servidor.

Ejemplo:

```json
{
  "name": "Carlos",
  "age": 28,
  "active": true
}
```

JSON es popular porque es facil de leer para personas y facil de procesar para programas.

## 8. HTTP Status Code

Un `HTTP status code` es un numero que indica el resultado de una solicitud HTTP.

Le dice al cliente si todo salio bien, si hubo un error o si hace falta algo mas.

Ejemplo:

- `200` significa que la solicitud fue correcta
- `404` significa que el recurso no fue encontrado
- `500` significa error interno del servidor

## 9. Common HTTP status codes

Estos son algunos codigos muy comunes:

- `200 OK`: la solicitud salio bien
- `201 Created`: el recurso fue creado
- `204 No Content`: salio bien pero no hay contenido para devolver
- `400 Bad Request`: la peticion es invalida
- `401 Unauthorized`: falta autenticacion
- `403 Forbidden`: el servidor entiende la peticion pero no la permite
- `404 Not Found`: no existe el recurso
- `500 Internal Server Error`: error del servidor

Buena practica: entender estos codigos ayuda a depurar mas rapido.

## 10. RESTful API

Una `RESTful API` es una API que aplica correctamente los principios de REST.

Normalmente significa:

- usa recursos con URLs claras
- usa metodos HTTP de forma correcta
- trabaja sin estado entre peticiones
- devuelve respuestas consistentes

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

Ejemplo:
si haces `GET /profile`, el token o la informacion necesaria para identificarte debe ir en la peticion actual.

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

## 13. API Testing

`API testing` es el proceso de comprobar que una API funciona correctamente.

Se prueba, por ejemplo:

- si devuelve la informacion esperada
- si responde con el status correcto
- si maneja bien errores
- si valida datos de entrada
- si cumple con seguridad y rendimiento

No se prueba la interfaz visual, se prueba el comportamiento de la API.

## 14. Tools for API testing

Algunas herramientas comunes para probar APIs son:

- `Postman`
- `Insomnia`
- `curl`
- `Swagger UI`
- `Thunder Client`

Para automatizar pruebas tambien se usan herramientas como:

- `Jest`
- `Supertest`
- `Pytest`

## 15. Payload

El `payload` es la informacion principal que se envia en una peticion o en una respuesta.

Muchas veces, cuando hablamos de payload, nos referimos al `body`.

Ejemplo de payload en una peticion `POST`:

```json
{
  "name": "Lucia",
  "email": "lucia@example.com"
}
```

Ese bloque JSON es el payload que se envia a la API.

Idea clave: el payload es el contenido util que viaja dentro del mensaje.

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
