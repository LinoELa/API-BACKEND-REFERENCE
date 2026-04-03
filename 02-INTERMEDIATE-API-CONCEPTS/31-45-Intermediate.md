# Intermediate API Concepts - Q31 to Q45

## Indice de contenidos

- [31. Authentication vs Authorization](#31-authentication-vs-authorization)
- [32. JWT](#32-jwt)
- [33. JWT Structure](#33-jwt-structure)
- [34. Bearer Token](#34-bearer-token)
- [35. JWT Real-Time Flow](#35-jwt-real-time-flow)
- [36. OAuth](#36-oauth)
- [37. Refresh Token](#37-refresh-token)
- [38. API Rate Limiting](#38-api-rate-limiting)
- [39. Why Rate Limiting Matters](#39-why-rate-limiting-matters)
- [40. Idempotency](#40-idempotency)
- [41. Idempotent HTTP Methods](#41-idempotent-http-methods)
- [42. Pagination](#42-pagination)
- [43. Pagination Examples](#43-pagination-examples)
- [44. Filtering](#44-filtering)
- [45. Sorting](#45-sorting)

## Como leer esta guia

Esta parte conecta la base de APIs con problemas reales de seguridad, acceso, control de trafico y manejo de datos.
La idea es que no solo memorices definiciones, sino que entiendas cuando se usan.

## 31. Authentication vs Authorization

`Authentication` significa comprobar quien eres.
`Authorization` significa comprobar que puedes hacer.

Ejemplo:

- autenticacion: iniciar sesion con usuario y password
- autorizacion: decidir si ese usuario puede borrar un recurso

Idea clave:

- authentication = identidad
- authorization = permisos

## 32. JWT

`JWT` significa `JSON Web Token`.
Es un token compacto que suele usarse para autenticar usuarios entre cliente y servidor.

Se envia normalmente en el header `Authorization` y permite identificar al usuario sin guardar sesion en memoria del servidor.

Ejemplo:

```http
Authorization: Bearer eyJhbGciOi...
```

## 33. JWT Structure

Un JWT tiene tres partes separadas por puntos:

- `header`
- `payload`
- `signature`

Ejemplo:

```text
xxxxx.yyyyy.zzzzz
```

El `header` indica el algoritmo.
El `payload` contiene datos como `userId` o `role`.
La `signature` sirve para verificar que el token no fue alterado.

## 34. Bearer Token

Un `Bearer token` es un token que da acceso al recurso a quien lo posea.
Se manda normalmente asi:

```http
Authorization: Bearer <token>
```

El servidor lee ese token y decide si la peticion es valida.

Idea importante: si alguien roba el token, puede usarlo mientras siga siendo valido.

## 35. JWT Real-Time Flow

Flujo basico en tiempo real:

1. el usuario hace login
2. el servidor valida credenciales
3. el servidor genera un JWT
4. el cliente guarda el token
5. el cliente envia el token en cada request protegida
6. el servidor valida el JWT y responde

Ejemplo:

- login en `/auth/login`
- respuesta con `accessToken`
- luego `GET /profile` usando `Authorization: Bearer ...`

## 36. OAuth

`OAuth` es un protocolo de autorizacion.
Permite que una aplicacion acceda a recursos de un usuario sin pedir directamente su password.

Ejemplo comun:

- iniciar sesion con Google
- iniciar sesion con GitHub

Idea simple: OAuth delega acceso entre sistemas de forma controlada.

## 37. Refresh Token

Un `Refresh Token` sirve para obtener un nuevo `access token` cuando el actual expira.

Uso comun:

- `access token`: dura poco
- `refresh token`: dura mas

Ventaja:
mejora la seguridad sin obligar al usuario a iniciar sesion cada pocos minutos.

## 38. API Rate Limiting

`API Rate Limiting` es una tecnica para limitar cuantas peticiones puede hacer un cliente en un tiempo determinado.

Ejemplo:

- 100 requests por minuto
- 1000 requests por hora

Se usa para proteger la API del abuso o del exceso de trafico.

## 39. Why Rate Limiting Matters

El rate limiting es importante porque ayuda a:

- prevenir abuso
- reducir ataques automatizados
- proteger recursos del servidor
- mantener un servicio estable para todos

Sin limites, un cliente podria saturar toda la API.

## 40. Idempotency

`Idempotency` significa que repetir una misma operacion varias veces produce el mismo resultado final.

Ejemplo:
si borras el usuario `10` una vez o dos veces, el estado final sigue siendo que ese usuario ya no existe.

Es un concepto muy importante cuando hay reintentos o fallos de red.

## 41. Idempotent HTTP Methods

Los metodos HTTP normalmente considerados idempotentes son:

- `GET`
- `PUT`
- `DELETE`
- `HEAD`
- `OPTIONS`

`POST` normalmente no es idempotente, porque repetirlo puede crear varios recursos.

## 42. Pagination

La `pagination` consiste en dividir grandes listas de datos en bloques mas pequenos.

En vez de devolver 10.000 registros de golpe, la API devuelve una parte.

Ventajas:

- menor carga
- respuestas mas rapidas
- mejor experiencia de uso

## 43. Pagination Examples

Ejemplo con `page` y `limit`:

```http
GET /products?page=2&limit=20
```

Ejemplo con cursor:

```http
GET /messages?cursor=abc123
```

Tipos comunes:

- paginacion por pagina
- paginacion por cursor
- paginacion por offset

## 44. Filtering

`Filtering` significa reducir resultados segun una condicion.

Ejemplo:

```http
GET /users?role=admin
```

La API solo devuelve usuarios que cumplan ese criterio.

## 45. Sorting

`Sorting` significa ordenar los resultados.

Ejemplo:

```http
GET /products?sort=price&order=asc
```

Con esto puedes devolver datos ordenados por precio, fecha, nombre u otro campo.

## Resumen rapido

- authentication = quien eres
- authorization = que puedes hacer
- JWT = token compacto de autenticacion
- bearer token = token enviado en el header
- refresh token = renueva acceso sin nuevo login
- rate limiting = limite de peticiones
- idempotency = repetir no cambia el resultado final
- pagination = dividir resultados
- filtering = filtrar datos
- sorting = ordenar datos

## Siguiente paso

La siguiente parte de esta seccion entra en arquitectura, estilos de API, pruebas y rendimiento.
