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

Esta parte mantiene el estilo del PDF: definicion, uso real, y puntos clave utiles en entrevista.
Aqui ya entramos en autenticacion, control de trafico y manejo mas serio de datos.

## 31. Authentication vs Authorization

Authentication responde a la pregunta: `Who are you?`

Sirve para verificar la identidad de un usuario o sistema.

Authorization responde a la pregunta: `What are you allowed to do?`

Sirve para determinar permisos despues de autenticar.

Real-time Scenario - Company HR System:

1. el empleado inicia sesion
2. la autenticacion se valida
3. intenta acceder a datos de nomina
4. si es HR Manager, entra
5. si es intern, recibe `403 Forbidden`

## 32. JWT

`JWT` (`JSON Web Token`) es un token compacto y seguro para transmitir informacion entre cliente y servidor.

Why JWT is used:

- autenticacion stateless
- no necesita guardar sesion en servidor
- escala bien en microservicios

Real-time Scenario: Un usuario inicia sesion en una tienda online, recibe un JWT y luego lo usa para acceder a pedidos, carrito y perfil.

## 33. JWT Structure

Un JWT tiene tres partes separadas por puntos:

```text
Header.Payload.Signature
```

Details:

- `Header` = tipo de token y algoritmo
- `Payload` = claims o datos del usuario
- `Signature` = verifica que el token no fue alterado

Example Payload:

```json
{
  "userId": 123,
  "role": "admin",
  "exp": 1700000000
}
```

## 34. Bearer Token

Un `Bearer token` es un access token que se envia en headers HTTP para autenticar requests.

Real-time Usage:

```http
GET /api/orders
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

Why "Bearer"?

Quien tenga el token puede usar el recurso, asi que debe protegerse bien.

## 35. JWT Real-Time Flow

Step-by-step Login Flow:

1. el usuario manda credenciales con `POST /login`
2. el servidor las valida
3. el servidor genera el JWT
4. el token vuelve al frontend
5. el frontend lo guarda en `localStorage` o cookies
6. el token se envia en cada request protegida

Why this matters in interviews: Demuestra que entiendes el flujo de autenticacion stateless.

## 36. OAuth

`OAuth` es un framework de autorizacion que permite a apps de terceros acceder a datos del usuario sin exponer passwords.

Real-time Scenario - Login with Google:

- la app nunca ve tu password de Google
- Google emite un access token
- la app accede a perfil y email con permiso

## 37. Refresh Token

Un `refresh token` sirve para obtener un nuevo access token sin que el usuario tenga que volver a iniciar sesion.

Real-time Scenario:

- el access token expira en 15 minutos
- el refresh token dura 7 dias
- el usuario sigue trabajando sin reloguearse cada poco tiempo

## 38. API Rate Limiting

Restringe cuantas requests puede hacer un cliente en una ventana de tiempo concreta.

Real-time Example:

```text
100 requests per minute per user
```

Why needed:

- prevenir abuso
- proteger recursos del servidor
- garantizar uso justo

## 39. Why Rate Limiting Matters

Real-time Problem: Una API publica sin limites puede sufrir:

- ataques de bots
- intentos de DDoS
- caidas del servidor

Common Solution:

```http
429 Too Many Requests
```

## 40. Idempotency

Una operacion es idempotente si ejecutarla varias veces produce el mismo resultado final.

Real-time Example - Payments:

```http
POST /payments
```

con una `idempotency-key`

Si la request se reintenta por un fallo de red, el pago solo se procesa una vez.

## 41. Idempotent HTTP Methods

Idempotent Methods:

- `GET`
- `PUT`
- `DELETE`

Not Idempotent:

- `POST`, porque puede crear recursos nuevos cada vez

## 42. Pagination

La paginacion divide datasets grandes en partes pequenas para mejorar rendimiento.

Real-time Scenario - Instagram Feed:

- carga 10 posts al principio
- al hacer scroll, carga la siguiente pagina

## 43. Pagination Examples

Example:

```http
GET /api/posts?page=2&limit=20
```

Alternative Approaches:

- paginacion por offset
- paginacion por cursor, mejor para grandes volumenes

## 44. Filtering

`Filtering` restringe las respuestas segun una condicion.

Real-time Example:

```http
GET /orders?status=delivered&payment=completed
```

## 45. Sorting

`Sorting` organiza la respuesta en un orden especifico.

Real-time Example:

```http
GET /products?sort=price&order=asc
```

## Resumen rapido

- authentication = verificar identidad
- authorization = verificar permisos
- JWT = token compacto y stateless
- bearer token = token en headers
- refresh token = renovar acceso
- rate limiting = limitar trafico
- idempotency = no duplicar efectos
- pagination = dividir resultados
- filtering = filtrar
- sorting = ordenar

## Siguiente paso

La segunda parte de `Intermediate` entra en arquitectura, estilos de API, mocking, contratos y latencia.

