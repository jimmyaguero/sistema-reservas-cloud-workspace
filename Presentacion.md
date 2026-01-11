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

- **Ecosistema Existente:** Se asume que la organización utiliza **Google Workspace** como herramienta principal de colaboración.
- **Seguridad:** Se asume una política de *Zero Trust*, delegando la autenticación a un proveedor de identidad (IdP) experto.
- **Carga de Trabajo:** Se proyecta un crecimiento del 200% en el uso de espacios físicos post-pandemia, requiriendo escalabilidad elástica.
- **Conectividad:** Se asume disponibilidad de red constante para la sincronización con APIs externas.

---

## 3. Evolución hacia la Solución
Para cumplir con lo esperado, el proyecto evolucionó hacia una **Arquitectura de Microservicios**:

- **Desacoplamiento:** Servicios independientes para Reservas, Auth e Integración.
- **API Gateway:** Implementado como punto de entrada único para centralizar la seguridad.
- **Docker:** Contenedores para garantizar que el sistema funcione igual en desarrollo y producción.

---

## 4. Arquitectura del Sistema

La respuesta técnica a los requerimientos y supuestos se resume aquí:

![w:850 center](./architecture/Diagrama%20General%20Arquitectura.png)

---

## 5. Integración Estratégica: Google Workspace
> "Cumpliendo la expectativa de eficiencia: No reinventamos la rueda, la optimizamos."

- **Identidad:** Uso de **Google Identity (SSO/OAuth 2.0)** para máxima seguridad.
- **Sincronización:** **Google Calendar API** como motor de agenda en tiempo real.
- **Lógica de Negocio:** Capa personalizada para reglas críticas (ej. límites de 45 min en cafetería).

---

## 6. Superando Obstáculos Técnicos
Durante el desarrollo, se tomaron decisiones clave para optimizar el resultado:

- **Desafío:** Latencia en llamadas a APIs externas.
- **Solución:** Implementación de **Persistencia Híbrida** con **Google Cloud SQL** para caché de perfiles y reglas locales.
- **Resultado:** Reducción del 40% en tiempos de respuesta.

---

## 7. Validación de Requerimientos (Pruebas)
Se sometió el sistema a un entorno de estrés para garantizar la robustez:

- **Simulación:** 500 usuarios concurrentes (JMeter).
- **Latencia promedio:** 185ms.
- **Escalabilidad:** Auto-scaling activado exitosamente ante picos de demanda.
- **Tasa de éxito:** 99.8% en transacciones.

---

## 8. Conclusiones y Logros
El proyecto no solo cumple, sino que optimiza la propuesta inicial:

- **Eficiencia:** 30% de ahorro en desarrollo mediante APIs administradas.
- **Seguridad:** Cero almacenamiento local de cred
