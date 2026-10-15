# Arquitectura y decisiones técnicas

## Componentes

- **Frontend:** React 19, Vite 7, React Router, Leaflet y Recharts. La aplicación pública incluye una página de inicio y un mapa ciudadano; las rutas de gestión requieren sesión.
- **API:** Node.js 22+, Express 5 y endpoints REST bajo `/api`. La ruta `/api/public` sirve la información anonimizada que usa la vista pública.
- **Persistencia:** PostgreSQL y Sequelize. El esquema se administra mediante migraciones.
- **Evidencias:** almacenamiento local en desarrollo, con integración opcional a S3 preparada en el proyecto privado.
- **Correo:** Nodemailer y SMTP para códigos, recuperación y notificaciones.
- **Operación:** Docker Compose para entorno local y documentación de una posible infraestructura en AWS.

## Flujo de un reporte

1. Una persona autenticada registra un incidente y, si corresponde, adjunta evidencias.
2. La API valida la solicitud, aplica permisos por recurso y persiste el reporte.
3. La vista pública recibe una representación anonimizada para el mapa y los indicadores.
4. Los roles de gestión pueden asignar responsables y cambiar el estado. El historial y la auditoría permiten seguir el proceso.
5. Los participantes reciben actualizaciones mediante las funciones de notificación y chat del sistema.

## Privacidad y seguridad

La interfaz pública no debe mostrar identidad, contacto, dirección exacta, evidencias ni conversaciones. La autenticación usa JWT; la autorización distingue consulta, edición, asignación y administración. El backend configura límites de solicitudes, cabeceras de seguridad y validación de archivos. La PWA evita almacenar respuestas de `/api` en el Service Worker.

Este documento explica las decisiones observables en el código privado. No constituye una auditoría de seguridad ni una afirmación sobre un despliegue de producción.
