# API Basics - Q16 to Q30

## Indice de contenidos

- [16. Headers](#16-headers)
- [17. Content-Type](#17-content-type)
- [18. Accept Header](#18-accept-header)
- [19. Query Parameter](#19-query-parameter)
- [20. Path Parameter](#20-path-parameter)
- [21. Difference between query and path parameters](#21-difference-between-query-and-path-parameters)
- [22. API Documentation](#22-api-documentation)
- [23. Swagger / OpenAPI](#23-swagger--openapi)
- [24. API Versioning](#24-api-versioning)
- [25. Why versioning is important](#25-why-versioning-is-important)
- [26. REST Constraint](#26-rest-constraint)
- [27. Cache](#27-cache)
- [28. CORS](#28-cors)
- [29. Same-Origin Policy](#29-same-origin-policy)
- [30. API Authentication](#30-api-authentication)

## Como leer esta guia

Esta segunda parte completa la base de API Basics.
Aqui aparecen conceptos muy usados en desarrollo backend, frontend, testing y seguridad.

## 16. Headers

Los `headers` son metadatos que viajan en una solicitud o en una respuesta HTTP.
Sirven para enviar informacion adicional sobre la comunicacion.

Ejemplos comunes:

- `Content-Type`
- `Accept`
- `Authorization`
- `Cache-Control`

Idea simple: los headers no suelen ser el dato principal, pero ayudan a explicar como debe tratarse ese mensaje.

## 17. Content-Type

`Content-Type` es un header que indica el formato del contenido que se esta enviando.

Ejemplos comunes:

- `application/json`
- `text/html`
- `multipart/form-data`

Ejemplo:

```http
Content-Type: application/json
```

Si envias un body en JSON, este header le dice al servidor que debe interpretarlo como JSON.

## 18. Accept Header

El header `Accept` indica que tipo de respuesta espera recibir el cliente.

Ejemplo:

```http
Accept: application/json
```

Esto significa que el cliente prefiere recibir la respuesta en formato JSON.

Diferencia simple:

- `Content-Type` = formato de lo que envio
- `Accept` = formato de lo que quiero recibir

## 19. Query Parameter

Un `query parameter` es un parametro que se envia en la URL despues del signo `?`.

Se usa mucho para:

- filtrar
- buscar
- ordenar
- paginar

Ejemplo:

```http
GET /products?category=books&page=2
```

En este caso:

- `category=books`
- `page=2`

son query parameters.

## 20. Path Parameter

Un `path parameter` es un valor que forma parte directa de la ruta del endpoint.
Normalmente identifica un recurso especifico.

Ejemplo:

```http
GET /users/25
```

Aqui, `25` es un path parameter porque indica el usuario concreto que queremos consultar.

## 21. Difference between query and path parameters

La diferencia principal es el uso.

- `path parameter`: identifica un recurso especifico
- `query parameter`: modifica o afina la consulta

Ejemplo:

```http
GET /users/25
GET /users?role=admin
```

En el primer caso buscas un usuario concreto.
En el segundo caso buscas una lista filtrada de usuarios.

## 22. API Documentation

La `API documentation` es la documentacion que explica como usar una API.

Normalmente incluye:

- endpoints disponibles
- metodos HTTP
- parametros
- headers
- ejemplos de request y response
- codigos de estado
- autenticacion

Una buena documentacion hace que la API sea mas facil de entender, probar e integrar.

## 23. Swagger / OpenAPI

`OpenAPI` es una especificacion para describir APIs de forma estandar.
`Swagger` es un conjunto de herramientas que trabaja con esa especificacion.

Con Swagger u OpenAPI puedes:

- documentar endpoints
- ver ejemplos
- probar solicitudes desde una interfaz
- generar clientes o codigo automaticamente

Idea simple: OpenAPI define la estructura y Swagger ayuda a visualizarla y usarla.

## 24. API Versioning

`Versioning in API` significa manejar versiones distintas de una API para poder introducir cambios sin romper integraciones existentes.

Ejemplo:

```http
/api/v1/users
/api/v2/users
```

Asi diferentes clientes pueden seguir usando la version que soportan.

## 25. Why versioning is important

El versionado es importante porque permite evolucionar una API sin afectar inmediatamente a todos los consumidores.

Sirve para:

- cambiar estructuras de datos
- mejorar endpoints
- eliminar campos antiguos
- corregir disenos anteriores

Sin versionado, un cambio importante puede romper aplicaciones que ya dependen de esa API.

## 26. REST Constraint

Una `REST constraint` es una de las reglas o restricciones del estilo REST.

Las mas conocidas son:

- cliente-servidor
- stateless
- cacheable
- uniform interface
- layered system
- code on demand (opcional)

Estas restricciones ayudan a que una API sea mas consistente, escalable y facil de mantener.

## 27. Cache

La `cache` es un mecanismo para guardar temporalmente respuestas o datos que se usan con frecuencia.

Su objetivo es mejorar el rendimiento y reducir trabajo innecesario del servidor.

Ejemplo:
si una respuesta cambia poco, puede guardarse para no recalcularla en cada peticion.

Beneficios:

- respuestas mas rapidas
- menos carga en el servidor
- mejor experiencia para el usuario

## 28. CORS

`CORS` significa `Cross-Origin Resource Sharing`.
Es un mecanismo de seguridad del navegador que controla si una pagina puede hacer peticiones a un dominio diferente.

Ejemplo:
una app en `http://localhost:3000` quiere acceder a una API en `http://localhost:5000`.
Eso es otro origen, y el servidor debe permitirlo con CORS.

## 29. Same-Origin Policy

La `same-origin policy` es una politica de seguridad del navegador.
Impide que una pagina web acceda libremente a recursos de otro origen distinto.

Un origen cambia si cambia:

- protocolo
- dominio
- puerto

Ejemplo:
`https://app.com` y `https://api.app.com` no son exactamente el mismo origen.

CORS existe precisamente para relajar esa restriccion de forma controlada.

## 30. API Authentication

`API authentication` es el proceso de verificar quien esta haciendo la solicitud.

Sirve para saber si el cliente tiene permiso para acceder a una API o a ciertos recursos.

Metodos comunes:

- API Key
- Bearer Token
- JWT
- OAuth
- Basic Auth

Idea clave: autenticacion responde a la pregunta "quien eres?".
Despues suele venir la autorizacion, que responde "que puedes hacer?".

## Resumen rapido

- headers = informacion adicional del mensaje
- Content-Type = formato del contenido enviado
- Accept = formato esperado en la respuesta
- query parameter = filtra o modifica la consulta
- path parameter = identifica un recurso concreto
- API documentation = guia para usar la API
- Swagger/OpenAPI = estandar y herramientas para documentar APIs
- versioning = manejo de versiones sin romper clientes
- cache = guardar respuestas para mejorar rendimiento
- CORS = control de acceso entre origenes distintos
- same-origin policy = regla de seguridad del navegador
- API authentication = verificar identidad del cliente

## Cierre de seccion

Con `Q1-Q30` ya queda completa la base de `API Basics`.
A partir de aqui ya se puede pasar a temas mas practicos como autenticacion, testing avanzado, diseno de endpoints y seguridad.
