# Calidad y verificación

El proyecto privado incluye las siguientes comprobaciones:

| Área | Herramienta o comando configurado | Objetivo |
| --- | --- | --- |
| Backend | `npm run check` | Sintaxis y pruebas con `node:test` |
| Frontend | `npm run check` | ESLint, pruebas y compilación |
| Interfaz | Playwright | Rutas públicas, responsividad y flujos críticos |
| Integración | GitHub Actions + PostgreSQL | Comprobaciones en cambios hacia `main` |

Las capturas de este repositorio se generaron con la aplicación frontend ejecutada localmente. Un script de Playwright sustituyó las respuestas de `/api/public/reportes` por tres reportes ficticios para evitar la exposición de información real. Las capturas son material de presentación y no evidencian un despliegue en vivo.

El código de pruebas y la configuración de CI están en el repositorio privado de la aplicación; por eso estos comandos no se pueden ejecutar desde este repositorio de caso de estudio.
