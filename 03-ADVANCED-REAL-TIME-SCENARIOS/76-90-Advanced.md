# Advanced and Real-Time Scenarios - Q76 to Q90

## Indice de contenidos

- [76. Event-Driven API](#76-event-driven-api)
- [77. Message Queue](#77-message-queue)
- [78. Message Queue Tools](#78-message-queue-tools)
- [79. Sync vs Async APIs](#79-sync-vs-async-apis)
- [80. Retry Mechanism](#80-retry-mechanism)
- [81. Circuit Breaker Pattern](#81-circuit-breaker-pattern)
- [82. Preventing Duplicate API Requests](#82-preventing-duplicate-api-requests)
- [83. API Schema Evolution](#83-api-schema-evolution)
- [84. Logging API Calls](#84-logging-api-calls)
- [85. API Abuse](#85-api-abuse)
- [86. Preventing SQL Injection via API](#86-preventing-sql-injection-via-api)
- [87. API Timeout](#87-api-timeout)
- [88. Handling Concurrent API Requests](#88-handling-concurrent-api-requests)
- [89. Blue-Green Deployment](#89-blue-green-deployment)
- [90. Canary Release](#90-canary-release)

## Como leer esta guia

Esta parte agrupa patrones de resiliencia, asincronia, logging, seguridad y despliegue.
Son temas muy de produccion y muy utiles en entrevistas de backend.

## 76. Event-Driven API

**Definition:** Una `Event-Driven API` se activa por eventos en lugar de depender solo de requests directas.

**Examples:**

- pedido creado
- usuario registrado
- pago completado

Se usa mucho en microservicios.

## 77. Message Queue

**Definition:** Una `message queue` es una cola que guarda mensajes para procesarlos de forma asincrona.

**Why used:**

- mejora escalabilidad
- evita bloquear procesos
- absorbe picos de trafico

## 78. Message Queue Tools

- RabbitMQ
- Kafka
- AWS SQS
- Redis Queue

**Real-time Example:** Procesamiento de pedidos en Amazon.

## 79. Sync vs Async APIs

| Synchronous | Asynchronous |
| --- | --- |
| el cliente espera | el cliente puede continuar |
| blocking | non-blocking |
| peor para tareas pesadas | mejor para escalar |

**Examples:**

- `Sync` = obtener perfil de usuario
- `Async` = enviar email o generar un reporte

## 80. Retry Mechanism

**Definition:** Consiste en reintentar automaticamente requests fallidas.

**Real-time Scenario:** Si falla la red al crear un pedido, el sistema puede reintentar de forma segura.

## 81. Circuit Breaker Pattern

**Definition:** El `circuit breaker` detiene llamadas a un servicio que esta fallando para evitar que todo el sistema colapse.

**Real-time Example:** Si falla el payment gateway, se paran temporalmente las llamadas y se usa un fallback.

## 82. Preventing Duplicate API Requests

**Techniques:**

- idempotency keys
- request hashing
- unique transaction IDs

**Example:** Evitar doble pago cuando el usuario pulsa `Pay` dos veces.

## 83. API Schema Evolution

**Definition:** Gestionar cambios de esquema sin romper a los clientes existentes.

**Techniques:**

- versioning
- backward compatibility
- optional fields

## 84. Logging API Calls

**Logging Includes:**

- timestamp
- endpoint
- status code
- response time
- user ID
- errors

**Why important:**

- debugging
- auditing
- monitoring

## 85. API Abuse

**Definition:** Uso indebido de la API, intencional o no.

**Examples:**

- brute force
- scraping
- DDoS
- exceso de requests

**Prevention:**

- rate limiting
- captcha
- authentication

## 86. Preventing SQL Injection via API

**Techniques:**

- input validation
- prepared statements
- ORM
- escaping inputs

**Bad Example:**

```text
SELECT * FROM users WHERE id= + userInput
```

## 87. API Timeout

**Definition:** Tiempo maximo que un cliente espera una respuesta.

**Real-time Example:** Una API de pagos puede cortar por timeout a los 30 segundos.

## 88. Handling Concurrent API Requests

**Techniques:**

- async processing
- thread pools
- queues
- locks
- optimistic concurrency control

**Real-time Example:** Muchos usuarios intentando reservar el mismo asiento de tren.

## 89. Blue-Green Deployment

**Definition:** Desplegar una nueva version sin downtime usando dos entornos.

**Flow:**

- `Blue` = version anterior
- `Green` = version nueva
- luego se cambia el trafico

## 90. Canary Release

**Definition:** Liberar una nueva version poco a poco a un pequeno porcentaje de usuarios.

**Benefit:** Detectar bugs antes del rollout completo.

## Resumen rapido

- event-driven = reaccionar a eventos
- message queue = desacoplar y procesar despues
- sync vs async = esperar o no esperar
- retry = reintentar fallos temporales
- circuit breaker = cortar dependencia fallida
- logging = registrar actividad
- blue-green y canary = despliegues mas seguros

## Siguiente paso

La ultima parte cierra con testing automatico, compatibilidad, tracing y diseno orientado a contrato.
