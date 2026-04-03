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

Esta ultima parte junta testing, documentacion, compatibilidad y debugging.
Son temas muy utiles para pensar una API como producto y no solo como codigo.

## 91. Automated API Testing

`Automated API Testing` consiste en probar la API con tests que corren solos.

Se puede validar:

- respuestas
- status codes
- errores
- contratos
- seguridad basica

Esto reduce regresiones cuando el sistema cambia.

## 92. Schema Registry

Un `Schema Registry` es un lugar central donde se almacenan y versionan esquemas de mensajes o eventos.

Se usa mucho en arquitecturas con eventos.

Ventaja:
permite controlar cambios y compatibilidad entre productores y consumidores.

## 93. Documenting APIs for Frontend Teams

Para equipos frontend, la documentacion debe ser clara y practica.

Conviene incluir:

- endpoints
- ejemplos reales
- errores posibles
- autenticacion
- limites
- casos edge

Buena documentacion reduce dudas y bloqueos.

## 94. Backward Compatibility

`Backward Compatibility` significa que cambios nuevos no rompen clientes antiguos.

Ejemplos de cambios mas seguros:

- agregar campos opcionales
- mantener endpoints viejos por un tiempo
- deprecar antes de eliminar

Es clave en APIs usadas por otros equipos o apps en produccion.

## 95. API Sandbox

Un `API Sandbox` es un entorno seguro de prueba.

Sirve para:

- probar integraciones
- hacer experimentos sin afectar produccion
- dar acceso a terceros de forma controlada

Es muy comun en APIs de pagos y servicios externos.

## 96. Rate Limit Exceeded Error

Este error aparece cuando un cliente supera el limite permitido de peticiones.

Suele responder con:

```http
429 Too Many Requests
```

Buena practica:
informar cuanto tiempo debe esperar el cliente antes de reintentar.

## 97. Debugging Production API Issues

Depurar problemas en produccion suele requerir:

- logs
- metricas
- traces
- correlation ids
- revision de despliegues recientes

La idea es encontrar rapidamente donde esta fallando el flujo real.

## 98. Distributed Tracing

`Distributed Tracing` permite seguir una request a traves de varios servicios.

Ejemplo:
una solicitud pasa por gateway, auth, orders y payments.

El tracing ayuda a ver:

- donde fallo
- cuanto tardo cada paso
- que servicio fue el cuello de botella

## 99. API-First Approach

`API-First Approach` significa disenar primero la API antes de implementar el codigo.

Normalmente se define antes:

- contrato
- endpoints
- esquemas
- errores
- documentacion

Esto mejora alineacion entre backend, frontend y QA.

## 100. Designing a Login API

Si te piden disenar una Login API en entrevista, conviene pensar en:

- `POST /auth/login`
- validacion de credenciales
- respuesta con tokens
- manejo de errores
- rate limiting
- logs
- refresh token
- seguridad de password

Ejemplo de respuesta:

```json
{
  "accessToken": "token",
  "refreshToken": "token"
}
```

No es solo hacer login, sino disenar un flujo seguro y mantenible.

## Resumen rapido

- automated testing = pruebas automaticas
- schema registry = control central de esquemas
- backward compatibility = no romper clientes antiguos
- sandbox = entorno de pruebas
- 429 = limite excedido
- distributed tracing = seguir requests entre servicios
- API-first = definir contrato antes de implementar

## Cierre de seccion

Con `Q61-Q100` queda completada la parte avanzada del material.
Desde aqui ya tienes una base bastante solida para estudiar APIs desde lo basico hasta escenarios de produccion.
