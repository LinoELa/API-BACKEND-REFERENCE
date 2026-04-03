# Advanced and Real-Time Scenarios - Q91 to Q100

## Indice de contenidos

- [91. Automated API Testing](#91-automated-api-testing)
- [92. Schema Registry](#92-schema-registry)
- [93. Documenting APIs for Frontend Teams](#93-documenting-apis-for-frontend-teams)
- [94. Backward Compatibility](#94-backward-compatibility)
- [95. API Sandbox](#95-api-sandbox)
- [96. Rate Limit Exceeded Error](#96-rate-limit-exceeded-error)
- [97. Debugging Production API Issues](#97-debugging-production-api-issues)
- [98. Distributed Tracing](#98-distributed-tracing)
- [99. API-First Approach](#99-api-first-approach)
- [100. Designing a Login API](#100-designing-a-login-api)

## Como leer esta guia

Esta ultima parte recoge testing, contratos, sandbox, debugging y diseno de entrevista.
Es el cierre natural del recorrido del PDF.

## 91. Automated API Testing

**Tools:**

- Postman automation
- Jest
- Mocha
- Newman
- RestAssured

**Types:**

- unit tests
- integration tests
- load tests

## 92. Schema Registry

**Definition:** Un `schema registry` es un repositorio central para esquemas de API o eventos.

**Used in:**

- microservices
- sistemas event-driven

Sirve para mantener estructuras consistentes.

## 93. Documenting APIs for Frontend Teams

**Best Practices:**

- Swagger / OpenAPI
- examples
- sample requests y responses
- error scenarios
- authentication guide

## 94. Backward Compatibility

**Strategies:**

- no eliminar campos existentes
- agregar campos opcionales
- versioning
- politica de deprecacion

## 95. API Sandbox

**Definition:** Un entorno de pruebas donde los desarrolladores pueden experimentar sin riesgo.

**Real-time Example:**

- PayPal Sandbox
- Stripe Test Mode

## 96. Rate Limit Exceeded Error

**Definition:** Ocurre cuando el usuario supera el limite permitido de requests.

**HTTP Code:**

```http
429 Too Many Requests
```

## 97. Debugging Production API Issues

**Techniques:**

- logs
- monitoring
- distributed tracing
- alerts
- error tracking como Sentry

## 98. Distributed Tracing

**Definition:** Seguimiento de una request a traves de varios servicios.

**Real-time Example:**

```text
Client -> API Gateway -> Auth Service -> Order Service -> Payment Service
```

Se usa mucho para debugging en microservicios.

## 99. API-First Approach

**Definition:** Disenar la API antes de construir frontend y backend.

**Benefits:**

- mejor colaboracion
- contratos claros
- desarrollo paralelo
- mejor escalabilidad

## 100. Designing a Login API

**Interview Task Steps:**

1. definir endpoint `POST /login`
2. validar input
3. autenticar usuario
4. generar JWT
5. devolver token
6. almacenamiento seguro
7. error handling
8. logging
9. rate limiting

**Sample Response:**

```json
{
  "token": "eyJhbGciOiJIUzI1NiIs...",
  "expiresIn": 900,
  "user": {
    "id": 101,
    "name": "Mounika"
  }
}
```

## Resumen rapido

- automated testing = comprobar sin hacerlo manualmente
- schema registry = control central de esquemas
- backward compatibility = no romper clientes antiguos
- sandbox = entorno seguro de pruebas
- 429 = limite de trafico superado
- distributed tracing = seguir una request entre servicios
- API-first = disenar el contrato antes del codigo

## Cierre de seccion

Con `Q61-Q100` la parte avanzada queda tambien mucho mas alineada con el PDF, incluyendo ejemplos y escenarios reales.
