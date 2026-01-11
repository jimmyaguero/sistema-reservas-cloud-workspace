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
´´´mermaid
graph TD
    subgraph Cliente
    A[WebApp Prototipo HTML/JS]
    end

    subgraph "Capa de Aplicación (Docker en GCP)"
    B[API Gateway / Auth]
    C[Microservicio de Reservas]
    D[Microservicio Integration Workspace]
    end

    subgraph "Persistencia Cloud (Cloud SQL / Firestore)"
    H[(DB: Perfiles, Reglas y Metadatos)]
    end

    subgraph "Servicios Google Workspace"
    E((Google Identity SSO))
    F[(Google Calendar API)]
    G[(Google Directory API)]
    end

    A -->|1. Login| B
    B -->|2. Autentica Identity| E
    B -->|3. Consulta Perfil/Rol| H
    A -->|4. Solicita Reserva según Rol| C
    C -->|5. Valida Aforos y Reglas| H
    C -->|6. Procesa| D
    D -->|7. Bloquea Recurso: Sala/Oficina/Cafetería| F
    D -->|8. Sincroniza Directorio| G
´´´
