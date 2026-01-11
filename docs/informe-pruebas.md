
# Informe de Pruebas: Sistema de Reservas Cloud

Fecha: 10 de enero de 2026
Version: 1.0
Entorno de Pruebas: Google Cloud Run / Docker (Entorno Simulado)

## 1. Resumen Ejecutivo
Este documento detalla los resultados de las pruebas realizadas sobre el sistema de gestion de recursos. El objetivo fue validar la estabilidad de la arquitectura de microservicios, la integracion con Google Workspace y la resiliencia del sistema bajo carga moderada.

---

## 2. Pruebas Unitarias y de Logica de Negocio
Se validaron los componentes criticos del backend para asegurar el cumplimiento de las reglas de negocio establecidas.

- Prueba UT-01: Validacion de tiempo maximo en cafeteria.
  - Escenario: Usuario intenta reservar por 60 minutos.
  - Resultado esperado: El sistema debe truncar o rechazar la reserva segun la politica de 45 minutos.
  - Resultado final: Rechazada correctamente.
  - Estado: Pasó.

- Prueba UT-02: Control de Acceso Basado en Roles (RBAC).
  - Escenario: Usuario con rol "Colaborador" intenta acceder a la API de administracion de recursos.
  - Resultado esperado: Error 403 (Acceso Denegado).
  - Resultado final: Bloqueo exitoso.
  - Estado: Pasó.

---

## 3. Pruebas de Carga (Simuladas con JMeter)
Se ejecuto una simulacion de estres para observar el comportamiento del auto-scaling y la latencia de la base de datos Cloud SQL.

- Parametros de carga: 500 usuarios concurrentes.
- Tiempo de rampa: 60 segundos.
- Resultados:
  - Latencia promedio: 185ms.
  - Tasa de exito: 99.8%.
  - Respuesta del Sistema: Se activo el escalado horizontal de contenedores en la nube al superar el umbral del 70% de CPU.

---

## 4. Pruebas de Integracion con Google Workspace
Validacion de la comunicacion con las APIs de Google mediante OAuth 2.0.

- Sincronizacion de Calendario: Se confirmo que las reservas creadas en el sistema se reflejan en tiempo real en Google Calendar sin duplicidades.
- Disponibilidad de Recursos: Se verifico que si una sala se marca como "Fuera de Servicio" en el Admin SDK, el sistema de reservas la deshabilita automaticamente.

---

## 5. Analisis de Errores y Mitigacion
Durante las pruebas, se identifico que la latencia aumentaba cuando el Microservicio de Integracion consultaba el Directorio de Google mas de 100 veces por minuto.

- Solucion: Se implemento una cache temporal en la Persistencia Cloud para almacenar los nombres y departamentos de los usuarios, reduciendo las llamadas externas innecesarias.

---

## 6. Conclusiones
El sistema es apto para su paso a produccion. La infraestructura Cloud-Native garantiza que el servicio sea escalable y que la experiencia del usuario sea fluida gracias a la integracion transparente con las cuentas corporativas de Google.

---
Informe generado para el Portafolio de Arquitectura Cloud - 2026
