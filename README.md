# Mi Municipio Vivo · caso de estudio

![React](https://img.shields.io/badge/React-19-149ECA?logo=react&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)
![Express](https://img.shields.io/badge/Express-5-000000?logo=express&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?logo=postgresql&logoColor=white)

**Plataforma web de participación ciudadana para reportar y gestionar incidencias urbanas.** El piloto se centra en el barrio López de Mesa, Robledo, Medellín. Este repositorio presenta el producto, las decisiones técnicas y la interfaz pública; el código de la aplicación permanece en un repositorio privado.

> **Sobre las capturas:** se tomaron de la interfaz real ejecutada localmente, con respuestas de API y reportes ficticios preparados para esta presentación. No muestran personas, reportes ni métricas reales. No hay una demo pública activa.

## Interfaz pública

### Inicio y resumen de reportes

![Página de inicio de Mi Municipio Vivo con mapa y métricas de ejemplo](assets/landing-demo.png)

### Mapa ciudadano y filtros

![Mapa público con tres reportes ficticios y controles de filtrado](assets/mapa-demo.png)

Mapas y datos cartográficos: [© OpenStreetMap contributors](https://www.openstreetmap.org/copyright). Los puntos y las cifras en estas capturas son ficticios.

## Problema y enfoque

Los incidentes del barrio suelen quedar dispersos entre mensajes y canales informales. Mi Municipio Vivo propone un lugar común para registrar reportes, ver su estado y dar seguimiento a la gestión, con una vista pública que protege los detalles sensibles.

| Necesidad | Función de la plataforma |
| --- | --- |
| Ubicar y consultar incidentes | Mapa público con reportes georreferenciados de forma anonimizada |
| Registrar y seguir un caso | Reportes con evidencias, historial, estados y notificaciones |
| Coordinar la respuesta | Asignaciones, paneles institucionales y auditoría |
| Participar en la conversación | Chats vinculados a reportes, grupos y comunidades |
| Usar la aplicación desde móvil | Interfaz adaptable y PWA instalable |

## Arquitectura resumida

```mermaid
flowchart LR
    C[Ciudadanía y personal institucional] --> W[React + Vite<br/>PWA y Leaflet]
    W -->|REST /api| A[Express + Node.js]
    A -->|Sequelize| P[(PostgreSQL)]
    A -->|SMTP| E[Correo y notificaciones]
    A -->|local o S3| F[Evidencias]
    A -->|datos anonimizados| W
```

La aplicación separa la vista pública de las funciones autenticadas. La API utiliza JWT, roles y permisos por recurso; las migraciones administran el esquema de PostgreSQL. Consulta [las decisiones de arquitectura](docs/architecture.md) y [el enfoque de calidad](docs/quality.md).

## Mi trabajo en este proyecto

- Construcción de una interfaz React con mapa, filtros, paneles y estados de carga.
- Diseño de una API REST en Express con modelos Sequelize y PostgreSQL.
- Separación de datos públicos y privados, autenticación y control de acceso.
- Pruebas automatizadas para frontend, backend y flujos críticos de interfaz.
- Preparación de ejecución con Docker Compose y documentación de despliegue.

## Alcance de esta publicación

Este repositorio contiene **documentación y capturas**, no datos de producción ni el código fuente privado. Las plantillas de AWS del proyecto describen una ruta de despliegue; no significan que exista un servicio público activo.

**Autor:** [Yifer Andrés Perea Blandón](https://github.com/ImDogBvs) · estudiante de Ingeniería de Software en Medellín.
