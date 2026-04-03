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

Esta parte reune conceptos de arquitectura, estilos de comunicacion y rendimiento.
Son temas muy comunes cuando una API deja de ser pequena y empieza a crecer.

## 46. HATEOAS

`HATEOAS` significa `Hypermedia As The Engine Of Application State`.
Es una idea de REST donde la respuesta incluye enlaces a acciones relacionadas.

Ejemplo:

```json
{
  "id": 10,
  "name": "Ana",
  "links": {
    "self": "/users/10",
    "orders": "/users/10/orders"
  }
}
```

La API no solo devuelve datos, tambien devuelve caminos posibles.

## 47. API Gateway

Un `API Gateway` es una puerta de entrada unica para varios servicios.

Puede encargarse de:

- autenticacion
- routing
- rate limiting
- logging
- cache

Idea simple: centraliza tareas comunes antes de llegar a los microservicios.

## 48. Microservices Architecture

La `Microservices Architecture` divide una aplicacion en varios servicios pequenos e independientes.

Ejemplo:

- servicio de usuarios
- servicio de pagos
- servicio de notificaciones

Cada servicio puede desplegarse y escalar de forma separada.

## 49. API Gateway Real-Time Use Case

Caso real:

1. el frontend llama a un solo endpoint publico
2. el API Gateway valida el token
3. decide a que microservicio enviar la peticion
4. agrega headers comunes
5. registra logs y metricas
6. devuelve una respuesta unificada

Esto simplifica mucho al cliente.

## 50. REST vs SOAP

`REST` y `SOAP` son dos estilos distintos para construir servicios.

Diferencias generales:

- REST suele ser mas ligero
- SOAP es mas formal y estricto
- REST usa mucho JSON
- SOAP usa XML

REST es muy comun en APIs web modernas.
SOAP sigue apareciendo en entornos corporativos y sistemas legacy.

## 51. SOAP

`SOAP` significa `Simple Object Access Protocol`.
Es un protocolo de comunicacion basado normalmente en XML.

Se caracteriza por:

- mensajes estructurados
- contratos estrictos
- fuerte enfoque empresarial

Suele usarse donde importan mucho las reglas, contratos y estandares formales.

## 52. WSDL

`WSDL` significa `Web Services Description Language`.
Es un archivo XML que describe un servicio SOAP.

Define:

- operaciones disponibles
- parametros
- tipos de datos
- ubicacion del servicio

En SOAP, WSDL funciona como un contrato tecnico formal.

## 53. GraphQL

`GraphQL` es un lenguaje de consultas para APIs.
Permite al cliente pedir exactamente los campos que necesita.

Ejemplo:

```graphql
query {
  user(id: 5) {
    name
    email
  }
}
```

Esto reduce respuestas demasiado grandes o demasiado pequenas.

## 54. REST vs GraphQL

Comparacion simple:

- REST usa multiples endpoints
- GraphQL suele usar un endpoint principal
- REST devuelve respuestas mas fijas
- GraphQL deja elegir campos al cliente

REST es mas simple de adoptar.
GraphQL da mucha flexibilidad, pero tambien introduce mas complejidad.

## 55. API Throttling

`API Throttling` es una tecnica para reducir o controlar la velocidad de peticiones cuando un cliente consume demasiado.

Se parece al rate limiting, pero suele enfocarse mas en ralentizar o regular el trafico que en bloquearlo por completo.

Sirve para proteger el sistema en momentos de carga.

## 56. Load Balancing

`Load Balancing` significa repartir trafico entre varios servidores o instancias.

Beneficios:

- evita sobrecarga en un solo servidor
- mejora disponibilidad
- permite escalar mejor

Ejemplo:
un balanceador reparte requests entre tres instancias de la misma API.

## 57. API Mocking

`API Mocking` consiste en simular una API real.

Se usa mucho para:

- desarrollo frontend
- pruebas tempranas
- testing sin depender del backend real

Ejemplo:
devolver respuestas falsas pero con la misma estructura esperada.

## 58. Contract Testing

`Contract Testing` verifica que dos sistemas respeten el contrato acordado entre ellos.

Ejemplo:
si frontend espera un campo `email`, el backend no deberia quitarlo sin avisar.

Este tipo de prueba ayuda a detectar roturas entre productor y consumidor.

## 59. API Latency

`API Latency` es el tiempo que tarda una API en responder.

Puede verse afectada por:

- consultas lentas
- red
- procesamiento pesado
- llamadas a otros servicios

Menor latencia significa respuestas mas rapidas.

## 60. Reducing API Latency

Algunas formas de reducir latencia son:

- usar cache
- optimizar consultas a base de datos
- reducir payloads
- usar paginacion
- evitar llamadas innecesarias
- comprimir respuestas
- usar load balancing

La mejora suele venir de quitar cuellos de botella.

## Resumen rapido

- HATEOAS = enlaces dentro de la respuesta
- API Gateway = entrada unica para varios servicios
- microservices = servicios pequenos e independientes
- REST y SOAP = estilos distintos
- GraphQL = consulta flexible de datos
- throttling = control de velocidad
- load balancing = reparto de trafico
- mocking = API simulada
- contract testing = validar contrato entre sistemas
- latency = tiempo de respuesta

## Cierre de seccion

Con `Q31-Q60` queda completa la parte intermedia.
La siguiente seccion entra ya en seguridad, errores, observabilidad y escenarios mas cercanos a produccion.
