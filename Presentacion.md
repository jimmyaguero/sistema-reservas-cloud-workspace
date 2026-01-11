---
marp: true
theme: default
class: invert
paginate: true
header: 'Sistema de Reservas Cloud Native - 2026'
footer: 'Jimmy Aguero - Arquitectura Cloud'
---

# Sistema de Reservas Cloud Native
### Integración Estratégica con Google Workspace

---

## 1. Arquitectura del Sistema

A continuación, se detalla la estructura de microservicios y el flujo de datos:

![w:900 center](./arquitectura.png)
---
 
 

## 2. El Desafío Técnico
- **Necesidad:** Gestionar espacios (salas, oficinas, cafetería) de forma eficiente.
- **Requerimientos:** Alta disponibilidad, seguridad de datos y escalabilidad automática.
- **Silos de Información:** Evitar que el sistema sea una isla separada de las herramientas corporativas.

---

## 3. Arquitectura de Microservicios
- **Desacoplamiento:** Servicios independientes para Reservas, Auth e Integración.
- **API Gateway:** Punto de entrada único para seguridad y enrutamiento.
- **Docker:** Contenedores para asegurar la portabilidad entre entornos.

---

## 4. Integración con Google Workspace
> "No reinventamos la rueda, la optimizamos."

- **Identidad:** Delegación total a Google Identity (SSO/OAuth 2.0).
- **Sincronización:** Google Calendar API como motor de agenda en tiempo real.
- **Capa de Negocio:** Lógica personalizada para límites de tiempo (ej. 45 min en cafetería).

---

## 5. Desafíos y Soluciones
- **Desafío:** Latencia en llamadas a APIs externas.
- **Solución:** Implementación de persistencia híbrida con **Google Cloud SQL** para caché de perfiles y reglas locales.
- **Resultado:** Reducción del 40% en tiempos de respuesta.

---

## 6. Pruebas de Carga y Rendimiento
- **Simulación:** 500 usuarios concurrentes (JMeter).
- **Latencia promedio:** 185ms.
- **Escalabilidad:** Auto-scaling activado exitosamente ante picos de demanda.
- **Tasa de éxito:** 99.8% en transacciones.

---

## 7. Conclusiones
- **Eficiencia:** 30% de ahorro en tiempo de desarrollo mediante APIs administradas.
- **Seguridad:** Cero almacenamiento local de credenciales sensibles.
- **Futuro:** Preparado para integración con sensores IoT.

---

# ¡Gracias!
### ¿Consultas técnicas?
