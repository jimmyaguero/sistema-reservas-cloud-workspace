# Sistema de Reservas Corporativas (Cloud Native)

Este proyecto es una solución de arquitectura diseñada para la gestión eficiente de recursos físicos (Salas de reuniones, Oficinas y Cafetería). Se utiliza el supuesto de que la empresa que ha solicitado esta solución, cuenta con Google Workspace, por lo tanto se pone énfasis en el aprovechamiento de la infraestructura de **Google Workspace**.

## Arquitectura del Sistema
- **Frontend:** WebApp interactiva (HTML5/JS).
- **Backend:** Microservicios desacoplados en contenedores Docker.
- **Persistencia:** Google Cloud SQL para reglas de negocio y perfiles.
- **Seguridad:** Autenticación vía Google SSO (OAuth 2.0).

## Características Principales
- **Gestión de Aforos:** Control en tiempo real para la Cafetería.
- **Sincronización:** Integración bidireccional con Google Calendar.
- **Roles de Usuario:** Niveles de acceso (Colaborador, Admin, Super Admin).

---
*Proyecto desarrollado para el portafolio de Arquitectura Cloud - 2026*
