# Intermediate API Concepts - Q46 to Q60

## Indice de contenidos

- [46. HATEOAS](#46-hateoas)
- [47. API Gateway](#47-api-gateway)
- [48. Microservices Architecture](#48-microservices-architecture)
- [49. API Gateway Real-Time Use Case](#49-api-gateway-real-time-use-case)
- [50. REST vs SOAP](#50-rest-vs-soap)
- [51. SOAP](#51-soap)
- [52. WSDL](#52-wsdl)
- [53. GraphQL](#53-graphql)
- [54. REST vs GraphQL](#54-rest-vs-graphql)
- [55. API Throttling](#55-api-throttling)
- [56. Load Balancing](#56-load-balancing)
- [57. API Mocking](#57-api-mocking)
- [58. Contract Testing](#58-contract-testing)
- [59. API Latency](#59-api-latency)
- [60. Reducing API Latency](#60-reducing-api-latency)

## Como leer esta guia

Aqui ya aparecen temas de arquitectura, contratos y rendimiento.
Son conceptos muy comunes cuando una API empieza a crecer de verdad.

## 46. HATEOAS

**Definition:** `HATEOAS` (`Hypermedia As The Engine Of Application State`) significa que las respuestas de la API incluyen enlaces hacia acciones relacionadas.

**Real-time Example:**

```json
{
  "orderId": 123,
  "status": "shipped",
  "links": {
    "track": "/orders/123/track",
    "cancel": "/orders/123/cancel"
  }
}
```

## 47. API Gateway

**Definition:** Un `API Gateway` es un punto de entrada unico que gestiona requests hacia varios servicios backend.

**Responsibilities:**

- authentication
- rate limiting
- routing
- logging

## 48. Microservices Architecture

**Definition:** Es una arquitectura donde una aplicacion se divide en servicios pequenos e independientes.

**Real-time Example - E-commerce:**

- User Service
- Order Service
- Payment Service
- Inventory Service

Cada uno tiene su propia API.

## 49. API Gateway Real-Time Use Case

**Flow:**

```text
Client -> API Gateway -> Appropriate Microservice
```

**Benefits:**

- simplifica la logica del frontend
- centraliza seguridad
- facilita monitoring

## 50. REST vs SOAP

| Feature | REST | SOAP |
| --- | --- | --- |
| Protocol | HTTP | XML-based |
| Format | JSON | XML |
| Speed | Fast | Slower |
| Complexity | Simple | Complex |
| Usage | Modern web apps | Legacy systems |

## 51. SOAP

**Definition:** `SOAP` (`Simple Object Access Protocol`) es un protocolo de mensajeria basado en XML.

**Real-time Use:**

- sistemas bancarios
- sistemas empresariales legacy

## 52. WSDL

**Definition:** `WSDL` describe la estructura, operaciones y endpoints de un servicio SOAP.

**Analogy:**

- `WSDL` = contrato
- `API` = implementacion

## 53. GraphQL

**Definition:** `GraphQL` es un lenguaje de consulta que permite al cliente pedir exactamente los datos que necesita.

**Real-time Example:**

```graphql
{
  user(id: 1) {
    name
    email
  }
}
```

## 54. REST vs GraphQL

**REST Issue:** over-fetching o under-fetching

**GraphQL Solution:** peticiones mas precisas

Lectura rapida:

- REST suele devolver respuestas mas fijas
- GraphQL permite elegir solo los campos necesarios

## 55. API Throttling

**Definition:** `API Throttling` es el control temporal de la velocidad de requests cuando la carga del servidor es alta.

**Real-time Example:** Durante un pico de ventas tipo Amazon, se limita trafico para evitar caidas.

## 56. Load Balancing

**Definition:** Reparte requests entrantes entre varios servidores.

**Real-time Scenario:** Trafico tipo Netflix distribuido entre muchos servidores alrededor del mundo.

## 57. API Mocking

**Definition:** `API Mocking` significa simular respuestas de una API sin backend real.

**Real-time Usage:** El equipo frontend puede avanzar antes de que el backend este terminado.

## 58. Contract Testing

**Definition:** Comprueba que proveedor y consumidor respetan el mismo contrato de API.

**Real-time Example:** Si frontend espera un campo `email`, backend no deberia eliminarlo sin coordinarlo.

## 59. API Latency

**Definition:** Es el tiempo desde que se envia una request hasta que se recibe la response.

**Impact:** Alta latencia significa mala experiencia de usuario.

## 60. Reducing API Latency

**Techniques:**

- caching
- database indexing
- CDN
- async processing

## Resumen rapido

- HATEOAS = enlaces accionables en la respuesta
- API Gateway = entrada unica
- microservices = servicios independientes
- SOAP = protocolo XML
- WSDL = contrato de SOAP
- GraphQL = datos exactos
- throttling = control temporal de velocidad
- load balancing = reparto de trafico
- mocking = simular backend
- contract testing = validar contrato
- latency = tiempo de respuesta

## Cierre de seccion

Con `Q31-Q60` queda la parte intermedia mucho mas alineada con el PDF, incluyendo ejemplos y escenarios de uso reales.
