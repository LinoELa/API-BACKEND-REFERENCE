# Handbook

## Que contiene esta carpeta

La carpeta `00-HandBook/` guarda el material fuente principal del proyecto.

Aqui esta el PDF completo:

- `API-ALL-CONCEPTS.pdf`

Y aqui tambien esta este archivo:

- `handbook.md`

La funcion de esta carpeta es servir como referencia base para revisar el contenido original cuando haga falta.

## De que va el PDF

El PDF reune un recorrido amplio sobre conceptos de APIs y backend.
Esta pensado como material de estudio y de preparacion para entrevistas.

Su contenido cubre desde lo mas basico hasta escenarios mas cercanos a produccion:

- conceptos basicos de API
- autenticacion y autorizacion
- JWT, OAuth y tokens
- paginacion, filtering y sorting
- API Gateway, microservices, REST, SOAP y GraphQL
- seguridad, errores, middleware y monitoring
- webhooks, colas, asincronia y resiliencia
- despliegues, tracing, compatibilidad y debugging

## Como se traduce ese PDF dentro del repositorio

El PDF no se esta usando como archivo final de estudio.
Se esta usando como fuente para construir una version mas ordenada en Markdown.

La idea del repositorio es:

1. tomar el contenido del PDF
2. dividirlo por grandes secciones
3. convertirlo en archivos mas pequenos
4. explicar los conceptos en espanol
5. mantener los nombres tecnicos clave en ingles
6. dejar indices para navegar mejor

## Secciones del material

### Section 1 - Basic API Concepts

Rango:

- `Q1-Q30`

Tema general:

- fundamentos de API, HTTP, REST, endpoints, request/response, status codes, headers, parametros, documentacion, CORS y autenticacion

Ubicacion:

- `../01-BASIC-API-CONCEPT/`

### Section 2 - Intermediate API Concepts

Rango:

- `Q31-Q60`

Tema general:

- autenticacion vs autorizacion, JWT, OAuth, rate limiting, idempotency, pagination, API Gateway, microservices, SOAP, GraphQL, mocking, contract testing y latencia

Ubicacion:

- `../02-INTERMEDIATE-API-CONCEPTS/`

### Section 3 - Advanced and Real-Time Scenarios

Rango:

- `Q61-Q100`

Tema general:

- seguridad, errores, middleware, monitoring, webhooks, eventos, colas, retry, circuit breaker, abuse, timeout, concurrencia, despliegues, tracing y API-first

Ubicacion:

- `../03-ADVANCED-REAL-TIME-SCENARIOS/`

## Como esta estructurado el repositorio

El proyecto sigue esta idea:

```text
API-BACKEND-REFERENCE/
  00-HandBook/
    API-ALL-CONCEPTS.pdf
    handbook.md
  01-BASIC-API-CONCEPT/
    00-indice.md
    01-15-Basics.md
    16-30-Basic.md
  02-INTERMEDIATE-API-CONCEPTS/
    00-indice.md
    31-45-Intermediate.md
    46-60-Intermediate.md
  03-ADVANCED-REAL-TIME-SCENARIOS/
    00-indice.md
    61-75-Advanced.md
    76-90-Advanced.md
    91-100-Advanced.md
  @api-backend.md
  README.md
```

## Que papel cumple cada archivo principal

- `README.md`
  - presenta el proyecto desde fuera
- `@api-backend.md`
  - resume el objetivo y la intencion del repositorio
- `handbook.md`
  - explica la relacion entre el PDF y la estructura creada
- `00-indice.md` en cada seccion
  - permite navegar por preguntas y bloques

## Importante

Este proyecto no debe entenderse como un template tecnico de API.

No trae:

- servidor arrancable
- configuracion de framework
- endpoints implementados
- arquitectura ejecutable

Lo que si ofrece es:

- referencia teorica organizada
- estructura de estudio por niveles
- material resumido para repasar
- apoyo para entrevistas y aprendizaje

## Criterio de construccion del contenido

Cuando se creen nuevos archivos o se retoquen los actuales, conviene mantener este criterio:

- claridad primero
- dividir por bloques pequenos
- actualizar indices
- mantener consistencia de nombres
- usar Markdown como formato principal de estudio
- usar el PDF como fuente de apoyo cuando haga falta contexto

## Uso recomendado

Puedes usar este repositorio de tres formas:

1. como ruta de estudio completa, empezando por `Basic`
2. como handbook de consulta rapida
3. como base para preparar entrevistas sobre APIs y backend

## Nota final

El PDF es el origen.
El valor del repositorio esta en la reorganizacion del contenido para hacerlo mas util, mas legible y mas mantenible en Markdown.
