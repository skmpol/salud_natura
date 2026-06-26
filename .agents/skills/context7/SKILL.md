---
name: context7
description: Habilidad para utilizar Context7 (ctx7) para buscar y consultar documentación de librerías y APIs actualizadas en tiempo real sin alucinaciones.
---

# Habilidad de Documentación en Tiempo Real — Context7

Esta habilidad le permite al agente consultar documentación actualizada y exacta de librerías, frameworks y APIs utilizando la CLI de Context7 (`ctx7`), reduciendo la probabilidad de alucinaciones o uso de APIs obsoletas.

## 🛠️ Cuándo usar esta habilidad

Úsala cuando necesites:
1. Buscar la sintaxis exacta de una función, clase o método en una librería (por ejemplo, FastAPI, Pydantic v2, pytest, paramiko, requests).
2. Comprender cómo interactuar con APIs externas cuya documentación haya podido cambiar desde la fecha de entrenamiento del modelo.
3. Resolver errores relacionados con firmas de métodos incorrectas, parámetros obsoletos o deprecaciones de librerías.

## 🚀 Cómo usar Context7 vía CLI

Puedes ejecutar comandos directamente usando la CLI `ctx7` para buscar y leer documentación de la siguiente manera:

### 1. Búsqueda de documentación de una librería específica

```bash
npx ctx7 <library_name> "<search_query>"
```
Ejemplos:
* Buscar cómo validar un tipo de datos en Pydantic v2:
  `npx ctx7 pydantic "BeforeValidator validation examples"`
* Buscar cómo configurar el lifespan de una aplicación en FastAPI:
  `npx ctx7 fastapi "lifespan context manager setup"`
* Buscar firmas de test en Pytest:
  `npx ctx7 pytest "mocking fixtures conftest"`

### 2. Búsqueda general de documentación técnica

```bash
npx ctx7 doc "<query>"
```
Ejemplo:
* `npx ctx7 doc "how to run docker compose build with buildkit disabled"`

## 💡 Flujo de Trabajo Sugerido para el Agente

1. **Identificar la necesidad**: Si el usuario pide implementar una característica usando una librería con cambios frecuentes (ej. FastAPI o Pydantic), y el agente tiene dudas sobre la sintaxis de la versión actual.
2. **Ejecutar el comando**: Invocar el comando de búsqueda usando `npx ctx7` mediante la herramienta `run_command` en el directorio del proyecto.
3. **Analizar la respuesta**: Leer la documentación devuelta por Context7 y utilizarla como la única "fuente de la verdad" para generar el código.
4. **Validar y aplicar**: Implementar la solución y escribir los tests correspondientes.
