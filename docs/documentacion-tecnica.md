
# Documentacion Tecnica: Sistema de Reservas Cloud

## 1. Introduccion
Este documento detalla la arquitectura tecnica del sistema de gestion de espacios (Oficinas, Salas y Cafeteria). La solucion se basa en un modelo de Microservicios Cloud-Native diseñado para integrarse de forma transparente con el ecosistema de Google Workspace.

---

## 2. El Rol Estrategico de Google Workspace

### 2.1. El Supuesto de Existencia
La arquitectura parte de la base de que la organizacion ya utiliza Google Workspace (Enterprise) como su ecosistema principal de productividad. Esto implica:
* Identidad digital unica para cada empleado (@empresa.com).
* Existencia de salas de reuniones como recursos en el panel de administracion.
* Infraestructura de seguridad (SSO y 2FA) plenamente operativa.

### 2.2. Bondades y Capacidades de la Integracion
* Sincronizacion de Disponibilidad: Uso de Google Calendar API para evitar duplicidad de reservas.
* Gestion de Identidad: Uso de Google Identity Services para un acceso sin fricciones (Single Sign-On).
* Capa de Inteligencia: El sistema añade reglas de negocio (como limites de tiempo y aforos) que complementan las capacidades nativas de Google.

---

## 3. Componentes del Sistema

### 3.1. Capa de Aplicacion (Microservicios)
* API Gateway: Punto de entrada unico que gestiona el trafico y la seguridad.
* Microservicio de Reservas: Motor de logica de negocio encargado de validar reglas y aforos.
* Microservicio de Integracion: Modulo dedicado a la comunicacion bidireccional con las APIs de Google.

### 3.2. Capa de Persistencia Cloud
Se utiliza Google Cloud SQL (PostgreSQL) para gestionar datos que no residen en Workspace:
* Roles de Usuario (RBAC): Control de permisos para Colaboradores, Admins y Super Admins.
* Metadata de Espacios: Informacion sobre capacidad, equipamiento y politicas especificas.

---

## 4. Pilares de la Arquitectura
La solucion se rige por los estandares de AWS Well-Architected y Google SRE:
* Escalabilidad: Despliegue en contenedores Docker para adaptacion automatica a la demanda.
* Seguridad: Cifrado de datos en transito mediante TLS 1.3 y autenticacion centralizada.
* Disponibilidad: Diseño desacoplado que asegura la continuidad de los servicios criticos.

---

## 5. Diseño de Base de Datos
Entidades principales para la persistencia de datos:
* Usuarios: Relacion de IDs de Google con roles locales y departamentos.
* Recursos: Catalogacion de espacios fisicos y sus restricciones.
* Reglas de Negocio: Configuracion dinamica de limites de uso para cada tipo de recurso.

---
Documento generado para el Portafolio de Arquitectura Cloud - 2026
