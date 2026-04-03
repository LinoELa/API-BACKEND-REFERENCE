# API Basics - Q16 to Q30

## Indice de contenidos

- [16. Headers](#16-headers)
- [17. Content-Type](#17-content-type)
- [18. Accept Header](#18-accept-header)
- [19. Query Parameter](#19-query-parameter)
- [20. Path Parameter](#20-path-parameter)
- [21. Difference between Query and Path Parameters](#21-difference-between-query-and-path-parameters)
- [22. API Documentation](#22-api-documentation)
- [23. Swagger / OpenAPI](#23-swagger--openapi)
- [24. API Versioning](#24-api-versioning)
- [25. Why Versioning Matters](#25-why-versioning-matters)
- [26. REST Constraint](#26-rest-constraint)
- [27. Cache](#27-cache)
- [28. CORS](#28-cors)
- [29. Same-Origin Policy](#29-same-origin-policy)
- [30. API Authentication](#30-api-authentication)

## Como leer esta guia

Esta segunda parte mantiene el estilo del PDF original: definicion, ejemplo real y pista de entrevista cuando aporta valor.
Aqui ya aparecen temas muy comunes en proyectos reales y entrevistas.

## 16. Headers

**Definition:** Los `headers` son pares `key-value` que viajan en una request o response HTTP y contienen metadatos sobre esa comunicacion.

No suelen ser el dato principal, pero le dicen al servidor o al cliente como tratar la informacion.

**Real-time Example:** Despues de hacer login, una app puede pedir el perfil asi:

```http
GET /api/user/profile
Authorization: Bearer eyJhbGciOiJIUzI1Ni...
Content-Type: application/json
Accept: application/json
```

Lectura rapida:

- `Authorization` = quien es el usuario
- `Content-Type` = formato de los datos enviados
- `Accept` = formato esperado de la respuesta

**Interview Tip:** Los headers se usan mucho para autenticacion, tipo de contenido, cache y datos del cliente.

## 17. Content-Type

**Definition:** `Content-Type` indica el formato del body que se esta enviando o devolviendo.

**Real-time Examples:**

1. Envio de JSON

```http
Content-Type: application/json
```

```json
{
  "email": "user@gmail.com",
  "password": "123456"
}
```

2. Subida de archivos

```http
Content-Type: multipart/form-data
```

**Why it matters:** Si mandas JSON y el `Content-Type` falta o es incorrecto, la request puede fallar.

**Interview Tip:** Ajustalo bien en `POST`, `PUT` y `PATCH`.

## 18. Accept Header

**Definition:** `Accept` indica al servidor que formato de respuesta espera el cliente.

**Real-time Example - Mobile App:**

```http
GET /api/products
Accept: application/json
```

Respuesta:

```json
{
  "id": 101,
  "name": "Laptop",
  "price": 50000
}
```

**Real-time Example - Browser:**

```http
Accept: text/html
```

En ese caso, el servidor podria responder con HTML.

**Interview Tip:**

- `Accept` = formato esperado de respuesta
- `Content-Type` = formato de datos enviados

## 19. Query Parameter

**Definition:** Los `query parameters` son pares `key-value` que se agregan a la URL despues de `?` y se usan para filtrar, ordenar, buscar o paginar.

**Real-time Example - E-commerce Website:**

```http
GET /api/products?category=mobile&price=low&page=2
```

Lectura rapida:

- `category=mobile` = filtro
- `price=low` = criterio de orden o seleccion
- `page=2` = paginacion

**Interview Tip:** Normalmente son opcionales y sirven para modificar la consulta.

## 20. Path Parameter

**Definition:** Los `path parameters` son variables dentro de la propia ruta y suelen identificar un recurso concreto.

**Real-time Examples:**

```http
GET /api/users/25
DELETE /api/orders/789
```

Lectura rapida:

- obtener el usuario `25`
- borrar el pedido `789`

**Interview Tip:** Normalmente son obligatorios y representan identificadores unicos.

## 21. Difference between Query and Path Parameters

| Feature | Path Parameter | Query Parameter |
| --- | --- | --- |
| Purpose | Identificar recurso | Filtrar o modificar respuesta |
| Mandatory | Yes | No |
| Position | Dentro de la ruta | Despues de `?` |
| Example | `/users/10` | `/users?role=admin` |

**Real-time Example:**

```http
GET /api/users/10?active=true
```

Lectura rapida:

- `10` = path param
- `active=true` = query param

## 22. API Documentation

**Definition:** La documentacion de API explica como usar una API: endpoints, formatos de request, formatos de response y errores.

**Real-time Examples:**

- `Stripe API docs` = pagos
- `Google Maps API docs` = ubicacion y mapas
- `Twitter API docs` = tweets y timelines

**Interview Tip:** Una buena documentacion reduce confusion y acelera integraciones.

## 23. Swagger / OpenAPI

**Definition:** `Swagger` u `OpenAPI` es una especificacion estandar para documentar APIs REST de forma clara e interactiva.

**Real-time Scenario:** Un desarrollador frontend abre Swagger UI y:

- ve todos los endpoints
- prueba APIs sin Postman
- entiende formatos de request y response

**Benefits:**

- testing interactivo
- documentacion generada automaticamente
- generacion de SDKs o clientes

## 24. API Versioning

**Definition:** El versionado de API consiste en mantener varias versiones para introducir cambios sin romper a los clientes existentes.

**Real-time Example:**

```http
/api/v1/users
/api/v2/users
```

Lectura rapida:

- `v1` = apps antiguas
- `v2` = apps nuevas

**Interview Tip:** El versionado facilita cambios graduales y compatibilidad hacia atras.

## 25. Why Versioning Matters

**Definition:** El versionado permite que aplicaciones existentes sigan funcionando aunque la API cambie.

**Real-time Problem:**

Version antigua:

```json
{"name": "John"}
```

Version nueva:

```json
{"fullName": "John Doe"}
```

Sin versionado, las apps viejas se rompen.
Con versionado, la migracion es segura.

## 26. REST Constraint

**Definition:** Las `REST constraints` son reglas que definen como debe comportarse una API REST.

**Key Constraints:**

1. `Client-Server`
2. `Stateless`
3. `Cacheable`
4. `Uniform Interface`
5. `Layered System`

**Real-time Example:**

```text
Frontend React app -> Backend Node API -> Database
```

Cada capa cumple una funcion y puede evolucionar de forma mas independiente.

## 27. Cache

**Definition:** La `cache` es almacenamiento temporal de datos usados con frecuencia para mejorar el rendimiento y reducir carga del servidor.

**Real-time Example - Weather App:**

- primera request = llamada real a la API, mas lenta
- siguientes requests = datos cacheados, mas rapidos

**Interview Tip:** Cache mejora velocidad, escalabilidad y experiencia de usuario.

## 28. CORS

**Definition:** `CORS` (`Cross-Origin Resource Sharing`) permite que un servidor indique que dominios pueden acceder a sus recursos.

**Real-time Scenario:**

Frontend:

```text
https://myapp.com
```

Backend:

```text
https://api.myapp.com
```

Header enviado por el servidor:

```http
Access-Control-Allow-Origin: https://myapp.com
```

**Interview Tip:** CORS es una restriccion del navegador, no una regla de negocio del backend.

## 29. Same-Origin Policy

**Definition:** Es una regla de seguridad del navegador que impide que una pagina acceda libremente a datos de otro origen.

**Origin =**

- protocolo
- dominio
- puerto

**Real-time Example:**

Bloqueado:

```text
https://siteA.com -> https://siteB.com
```

Permitido:

```text
https://siteA.com -> https://siteA.com/api
```

## 30. API Authentication

**Definition:** La autenticacion de API verifica quien esta haciendo la request antes de permitir acceso.

**Common Methods and Real-time Examples**

1. API Keys

```http
GET /api/data?api_key=abc123
```

Uso comun: APIs publicas como mapas o clima.

2. JWT Tokens

```http
Authorization: Bearer eyJhbGciOiJIUzI1Ni...
```

Uso comun: sistemas con login.

3. OAuth

Ejemplo: login con Google o Facebook.

4. Basic Authentication

```http
Authorization: Basic base64(username:password)
```

Uso comun: sistemas internos o legacy.

**Interview Tip:**

- authentication = identidad
- authorization = permisos

## Resumen rapido

- headers = metadatos de la comunicacion
- `Content-Type` = formato del contenido enviado
- `Accept` = formato esperado en la respuesta
- query params = filtros y modificadores
- path params = identificadores de recursos
- API docs = guia de uso de la API
- Swagger / OpenAPI = documentacion y testing interactivo
- versioning = evolucionar sin romper clientes
- cache = mejorar rendimiento
- CORS = acceso entre origenes controlado
- same-origin policy = regla de seguridad del navegador
- API authentication = verificar identidad

## Cierre de seccion

Con `Q1-Q30` queda una version de `Basic` mucho mas alineada con el PDF, incluyendo ejemplos y escenarios de uso reales.
