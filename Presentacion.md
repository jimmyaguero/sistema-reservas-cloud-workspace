
# Presentacion Ejecutiva: Sistema de Reservas Cloud Native

## 1. Resumen del Proyecto
Esta solucion optimiza la gestion de espacios corporativos (Oficinas, Salas y Cafeteria) mediante una arquitectura de microservicios integrada profundamente con Google Workspace.

---

## 2. Diagrama de Arquitectura Conceptual
A continuacion se presenta la interaccion entre los componentes Cloud y los servicios de Google:

```mermaid
graph LR
    User[Usuario] --> Web[Interfaz Web]
    Web --> API[API Gateway]
    
    subgraph "Nucleo de la Solucion"
    API --> Micro[Microservicio Reservas]
    Micro --> DB[(Cloud SQL)]
    end
    
    subgraph "Ecosistema Google"
    Micro --> GCal[Google Calendar]
    API --> GAuth[Google Identity]
    end
