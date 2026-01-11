---
marp: true
theme: default
class: invert
paginate: true
header: 'Módulo 2 - Sistema de Reservas Cloud Native - 2026'
footer: 'Jimmy Aguero - Arquitectura Cloud'
---

# Sistema de Reservas Cloud Native
### Integración Estratégica con Google Workspace

---

## 1. Contexto y Desafío Técnico
**Solicitud del ejercicio:** Gestionar espacios (salas, oficinas, cafetería) de forma eficiente bajo un modelo Cloud.

- **Necesidad:** Eliminar procesos manuales y errores en la reserva de espacios comunes.
- **Requerimientos:** Alta disponibilidad, seguridad de datos y escalabilidad automática.
- **El Problema:** Evitar "Silos de Información" creando un sistema que conviva con las herramientas corporativas existentes.

---

## 2. Supuestos de Diseño
Para robustecer la arquitectura, se establecieron los siguientes supuestos:

- **Ecosistema Existente:** La organización utiliza **Google Workspace** como herramienta principal de colaboración.
- **Seguridad:** Política de *Zero Trust*, delegando la autenticación a un proveedor de identidad (IdP) experto.
- **Carga de Trabajo:** Proyección de crecimiento elástico para soportar picos de demanda post-pandemia.
- **Conectividad:** Disponibilidad de red constante para sincronización vía API.

---

## 3. Evolución hacia la Solución
El proyecto evolucionó hacia una **Arquitectura de Microservicios** para cumplir con la escalabilidad:

- **Desacoplamiento:** Servicios independientes para Reservas, Auth e Integración.
- **API Gateway:** Punto de entrada único para centralizar seguridad y ruteo.
- **Docker:** Contenedores para garantizar la portabilidad entre entornos.

---

## 4. Arquitectura del Sistema

Respuesta técnica a los requerimientos y supuestos:

![w:850 center](./architecture/Diagrama%20General%20Arquitectura.png)

---

## 5. Integración Estratégica: Google Workspace
> "Eficiencia operativa: Optimizamos la infraestructura existente."

- **Identidad:** **Google Identity (SSO/OAuth 2.0)** para gestión de accesos.
- **Sincronización:** **Google Calendar API** como motor de agenda en tiempo real.
- **Lógica de Negocio:** Reglas personalizadas (ej. cuotas de tiempo por tipo de sala).

---

## 6. Validación de Requerimientos (Pruebas)
Garantía de robustez mediante pruebas de estrés:

- **Simulación:** 500 usuarios concurrentes (JMeter).
- **Latencia promedio:** 185ms.
- **Escalabilidad:** Auto-scaling validado ante picos de demanda.
- **Tasa de éxito:** 99.8% en transacciones.

---

## 7. Acceso al Proyecto

Toda la documentación técnica, código fuente y archivos de configuración están disponibles en el repositorio oficial:

### **Repositorio GitHub:**
[https://github.com/jimmyaguero/sistema-reservas-cloud-workspace](https://github.com/jimmyaguero/sistema-reservas-cloud-workspace)

---

## 8. Conclusiones ✨
- **Eficiencia:** Reducción de tiempos de desarrollo mediante servicios administrados.
- **Seguridad:** Arquitectura robusta sin almacenamiento local de datos sensibles.
- **Impacto:** Sistema alineado 100% con la transformación digital corporativa.

---

# ¡Gracias!
### ¿Consultas sobre el repositorio o la arquitectura?
