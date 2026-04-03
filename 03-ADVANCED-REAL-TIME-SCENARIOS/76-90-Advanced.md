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

Esta parte mezcla patrones de resiliencia, asincronia, seguridad y despliegue.
Son temas muy utiles cuando una API ya esta funcionando en entornos reales.

## 76. Event-Driven API

Una `Event-Driven API` reacciona a eventos en lugar de depender solo de peticiones directas.

Ejemplo:

- usuario registrado
- pedido creado
- pago completado

En lugar de consultar constantemente, los sistemas reaccionan cuando algo ocurre.

## 77. Message Queue

Una `Message Queue` es una cola donde un sistema deja mensajes para que otro los procese despues.

Sirve para desacoplar servicios y procesar tareas asincronas.

Ejemplo:
la API recibe un pedido y envia un mensaje para generar la factura mas tarde.

## 78. Message Queue Tools

Herramientas comunes:

- `RabbitMQ`
- `Kafka`
- `Amazon SQS`
- `Redis Streams`

Cada una sirve para distintos niveles de escala y patrones de mensajeria.

## 79. Sync vs Async APIs

`Sync` significa que el cliente espera la respuesta en ese momento.
`Async` significa que la tarea puede seguir despues y la respuesta final llegar mas tarde.

Ejemplo:

- sync: consultar perfil
- async: procesar video o enviar miles de emails

## 80. Retry Mechanism

Un `Retry Mechanism` repite una operacion cuando falla por una causa temporal.

Ejemplo:
si otro servicio tarda demasiado o da error momentaneo, el sistema reintenta.

Buena practica:

- limitar numero de reintentos
- usar esperas progresivas

## 81. Circuit Breaker Pattern

El `Circuit Breaker Pattern` evita llamar repetidamente a un servicio que ya esta fallando.

Idea simple:

- si un servicio falla mucho, se corta temporalmente el paso
- luego se prueba otra vez mas tarde

Esto evita cascadas de fallos.

## 82. Preventing Duplicate API Requests

Para prevenir duplicados se puede usar:

- `idempotency keys`
- bloqueo temporal
- control de reintentos
- validacion por request id

Ejemplo comun:
evitar cobrar dos veces una misma compra.

## 83. API Schema Evolution

`API Schema Evolution` es el cambio progresivo de esquemas sin romper clientes existentes.

Buenas practicas:

- agregar campos opcionales
- deprecar antes de eliminar
- versionar cambios grandes

La evolucion debe ser controlada.

## 84. Logging API Calls

Registrar llamadas a la API ayuda a:

- auditar actividad
- detectar errores
- analizar trafico
- depurar problemas

Se suelen registrar datos como ruta, metodo, status, duracion y request id.

## 85. API Abuse

`API Abuse` es el uso malicioso o excesivo de una API.

Ejemplos:

- scraping agresivo
- ataques automatizados
- brute force
- envio masivo de requests

Por eso se combinan rate limiting, auth y monitoreo.

## 86. Preventing SQL Injection via API

Para prevenir `SQL Injection` se recomienda:

- usar queries parametrizadas
- validar entrada
- evitar concatenar SQL manualmente
- usar ORM o query builders seguros

Nunca debes confiar ciegamente en los datos de entrada.

## 87. API Timeout

Un `API Timeout` es el limite de tiempo para esperar una respuesta.

Si se supera ese tiempo, la peticion falla o se cancela.

Esto evita que procesos lentos bloqueen indefinidamente al cliente o al servidor.

## 88. Handling Concurrent API Requests

Cuando muchas peticiones llegan al mismo tiempo, hay que manejar concurrencia con cuidado.

Tecnicas comunes:

- bloqueos
- colas
- transacciones
- control de version

Esto ayuda a evitar datos inconsistentes.

## 89. Blue-Green Deployment

`Blue-Green Deployment` usa dos entornos casi identicos:

- `blue`: version actual
- `green`: nueva version

Cuando la nueva esta lista, se cambia el trafico de una a otra.

Ventaja:
rollback rapido si algo sale mal.

## 90. Canary Release

En un `Canary Release`, la nueva version se libera primero a un pequeno porcentaje de usuarios.

Si todo va bien, se aumenta el trafico poco a poco.

Ventaja:
reduce el riesgo de fallos masivos.

## Resumen rapido

- event-driven = reaccionar a eventos
- message queue = procesar despues
- sync vs async = respuesta inmediata o diferida
- retry = reintentar fallos temporales
- circuit breaker = cortar llamadas a servicios caidos
- logging = registrar actividad
- blue-green y canary = despliegues mas seguros

## Siguiente paso

La ultima parte de esta seccion cierra con testing, compatibilidad, tracing y diseno de entrevista.
