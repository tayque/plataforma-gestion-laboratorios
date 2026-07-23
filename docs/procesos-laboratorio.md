# Procesos y Organización del Laboratorio

**Documento Integral de Organización y Métodos**  
**Proyecto:** Plataforma Híbrida de Gestión de Laboratorios  
**Asignatura:** Organización y Métodos  
**Versión:** 1.0  
**Fecha:** Julio 2026

---

## 1. Introducción

Este documento presenta la **organización completa** y los **procesos clave** del laboratorio de computación. Su propósito es estandarizar el funcionamiento, reducir tiempos improductivos, garantizar trazabilidad y servir como referencia para la asignatura de **Organización y Métodos**.

Se incluyen descripciones detalladas, diagramas BPMN textuales, matriz RACI, indicadores y propuestas de mejora.

---

## 2. Estructura Organizacional Mínima

### Roles Principales

- **Administrador de Laboratorio**: Responsable general de la operación física y digital.
- **Responsable de Imágenes**: Gestor del catálogo de contenedores (Docker).
- **Chapter de Organización y Procesos**: Profesor líder (encargado de definir, documentar y mejorar procesos).
- **Docente / Product Owner**: Solicita y valida recursos por curso/proyecto.
- **Estudiante / Desarrollador**: Usuario final.
- **Chapter Leads Técnicos**: Profesores por especialidad (DevOps, Seguridad, etc.).

```diff
- Comentario por Ticona Saure Jose Maria: 
- A favor: La separación de roles entre docentes y personal técnico está bien
- definida conceptualmente.
- Observación y mejora:Falta especificar el nivel de permisos que tendrá cada
- rol dentro de la plataforma (por ejemplo: permisos de lectura, ejecución,
- despliegue o administración de contenedores). Además, no se aclara qué
- sucede cuando un estudiante requiere paquetes adicionales no incluidos en
- la imagen base enviada por el docente.
```

### Propuesta de Organización

Se recomienda un **Chapter de Organización y Procesos** (transversal) en lugar de un squad completo. Este Chapter trabajará junto con un **Rol de "Process Owner"** dentro de cada Squad técnico.

**Justificación**: Permite mantener los squads enfocados en desarrollo mientras se garantiza que los procesos sean prácticos y bien documentados.

---

## 3. Procesos Principales (con Descripción Detallada)

### 3.1 Proceso: Solicitud y Asignación de Recursos de Hardware

**Objetivo:** Gestionar de forma eficiente las computadoras, servidores e impresoras.

**Flujo BPMN (Textual):**

Start → Solicitud por Portal → Verificación Automática de Disponibilidad 
→ ¿Disponible? 
   → Sí → Aprobación Automática / Manual → Asignación + Notificación → Check-in (QR) → Uso → Check-out → Liberación → End
   → No → Notificación de Espera → Cola de Prioridad → Revisión Manual



**Descripción Detallada:**
1. El usuario inicia sesión y selecciona el recurso.
2. El sistema verifica disponibilidad en tiempo real.
3. Se registra el préstamo con fecha/hora de devolución.
4. Al llegar al laboratorio se realiza Check-in.

```diff
- Comentario por Huaynacho Mango, Jerry Anderson:
- A favor: El flujo cubre el ciclo completo del préstamo (solicitud, verificación
- en tiempo real, check-in con QR, check-out y liberación), lo que da trazabilidad
- de quién usó cada equipo y cuándo.
- Observación y mejora: No se definen los criterios de la "Cola de Prioridad"
- cuando no hay disponibilidad (¿tiene prioridad un curso con evaluación, un
- proyecto de investigación, el orden de llegada?). Tampoco se especifica en qué
- casos la aprobación es automática y en cuáles pasa a revisión manual. Además,
- falta el escenario de no-show: si el usuario reserva y nunca hace check-in, el
- flujo no indica en cuánto tiempo se libera el recurso ni si hay penalidad, y lo
- mismo ocurre si no realiza el check-out o excede la hora de devolución.
```

---

### 3.2 Proceso: Gestión del Catálogo de Imágenes de Contenedores (Core)

**Objetivo:** Proporcionar entornos estandarizados y trazables.

**Flujo BPMN (Textual):**

Start → Solicitud de Imagen (Estudiante/Docente)
→ Búsqueda Automática en Harbor
→ ¿Imagen Disponible y Actualizada?
   → Sí → Entrega de Enlace de Descarga → Uso Local / Laboratorio → End
   → No → Notificación al Responsable de Imágenes
      → Análisis (Oficial vs Crear)
      → Descarga / Creación de Imagen
      → Escaneo de Vulnerabilidades
      → Firma Digital
      → Aprobación
      → Publicación en Harbor
      → Notificación a Solicitante



**Descripción Detallada:**
- Toda imagen debe estar **escaneada y firmada**.
- Los estudiantes pueden descargar la imagen oficial y ejecutarla en su computadora personal con Docker o Podman.
- Se mantiene un historial completo de versiones.

```diff
- Comentario por Alarico Pacheco Camila Fernanda:
- A favor: El flujo está bien pensado en cuanto a trazabilidad: incluye escaneo de vulnerabilidades, firma
- digital y aprobación antes de publicar.
- Observacion y mejora: El flujo depende totalmente de "Búsqueda Automática en Harbor", pero no contempla
- qué pasa si el servicio está caído o inaccesible, por lo que se requiere definir un procedimiento alterno
- (manual o caché local) ante caída de Harbor. Tambien no se especifica quién decide ni bajo qué parámetros se
- determina si conviene usar una imagen oficial existente o crear una nueva por lo que se tiene que establecer
- criterios para decidir entre ellos. Ademas falta el escenario de rechazo de la imagen por lo que se
- sugiere agregar un paso de notificacion de rechazo.
```

---

### 3.3 Proceso: Actualización y Mantenimiento de Imágenes

**Flujo BPMN:**

Start → Detección Automática de Nueva Versión
→ Pipeline de Rebuild
→ Escaneo de Seguridad
→ ¿Requiere Aprobación Manual?
   → Sí → Revisión por Responsable → Aprobación/Rechazo
   → No → Actualización Automática
→ Publicación → Notificación a Usuarios Activos → End



---

### 3.4 Proceso: Reserva y Uso de Laboratorio

**Flujo BPMN:**

Start → Login → Seleccionar Horario y Equipo
→ Validación de Disponibilidad
→ Reserva Confirmada → Recordatorio 15 min antes
→ Check-in en Laboratorio → Uso → Check-out → Liberación Automática

```diff
- Comentario por Huaynacho Mango, Jerry Anderson:
- A favor: El proceso es simple y está bien automatizado: recordatorio previo,
- check-in/check-out y liberación automática reducen la intervención manual del
- administrador.
- Observación y mejora: Este proceso se superpone con el 3.1, ya que ambos
- terminan reservando/asignando equipos; convendría unificarlos o aclarar que 3.1
- es préstamo de hardware puntual y 3.4 es reserva programada de horario. Faltan
- también tres escenarios habituales: (1) cancelación o modificación de una
- reserva, (2) ventana de tolerancia para el check-in y liberación por no-show,
- y (3) la reserva grupal, cuando un docente reserva el laboratorio completo para
- una clase (la matriz RACI le asigna rol C, pero el flujo no lo incluye).
- Sugiero además agregar un KPI de no-show y de ocupación real del laboratorio,
- ya que el único indicador actual (tiempo de reserva ≤ 5 min) no mide si las
- reservas se cumplen.
```

---

## 4. Matriz RACI General

| Actividad / Proceso                    | Administrador Lab | Responsable Imágenes | Docente | Estudiante | Chapter Organización |
|---------------------------------------|-------------------|----------------------|---------|----------|----------------------|
| Solicitud de Recursos Hardware        | A                 | I                    | C       | R        | C                    |
| Solicitud y Aprobación de Imágenes    | A                 | R                    | C       | R        | C                    |
| Creación de Nueva Imagen              | C                 | R/A                  | C       | I        | C                    |
| Reserva de Equipos                    | A                 | I                    | C       | R        | I                    |
| Actualización de Imágenes             | I                 | R                    | C       | I        | C                    |
| Definición y Mejora de Procesos       | C                 | C                    | C       | I        | R/A                  |

---

## 5. Indicadores de Desempeño (KPIs)

- Tiempo promedio de aprobación de nueva imagen: **≤ 48 horas**
- Porcentaje de solicitudes resueltas automáticamente: **≥ 70%**
- Tiempo promedio de configuración de entorno por estudiante: **≤ 15 minutos**
- Tasa de utilización de imágenes oficiales: **≥ 75%**
- Nivel de satisfacción de usuarios (Encuesta): **≥ 85%**
- Tiempo promedio de reserva de equipo: **≤ 5 minutos**

---

## 6. Mejora Continua y Recomendaciones

- Realizar **revisiones mensuales** de procesos con el Chapter de Organización.
- Utilizar herramientas como **Draw.io, Bizagi o Camunda** para mantener diagramas BPMN actualizados.
- Implementar **automatización progresiva** de decisiones mediante reglas de negocio.
- Crear un **manual de usuario** y **guías rápidas** para estudiantes.
- Establecer un **comité de procesos** (Administrador + Chapter Leads + Estudiantes representantes).

**Próximos Pasos:**
1. Modelar todos los diagramas BPMN en herramienta gráfica.
2. Validación del documento con docentes y administradores.
3. Integración de flujos automatizados en la plataforma.

---

**Este documento integra toda la parte de Organización y Procesos del Laboratorio.**  
Está diseñado para ser entregado como **trabajo de curso de Organización y Métodos**.

---

¿Deseas que agregue más procesos (ej. Gestión de Incidentes, Onboarding de Nuevos Usuarios, Cierre de Semestre, etc.) o que prepare una versión con PlantUML para generar diagramas reales?

