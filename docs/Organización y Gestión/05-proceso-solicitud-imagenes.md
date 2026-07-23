# Proceso de Solicitud de Imágenes

## 1. Introducción

Uno de los pilares de la plataforma híbrida de gestión de laboratorios es la disponibilidad de entornos de trabajo estandarizados y reproducibles para estudiantes y docentes. Estos entornos se distribuyen mediante **imágenes de contenedores** (Docker/Podman), las cuales deben solicitarse, revisarse y publicarse siguiendo un proceso formal que garantice seguridad, trazabilidad y consistencia entre los distintos cursos y proyectos.

Esta sección desarrolla el **proceso de solicitud de imágenes**: cómo un docente o estudiante solicita un entorno, cómo se valida su existencia previa en el catálogo, y cómo se gestiona la creación, escaneo, firma y publicación de una nueva imagen cuando no existe una alternativa aprobada.

Este proceso se relaciona directamente con la gobernanza de imágenes Docker y con la gestión de software y licencias, dado que toda imagen publicada contiene software, dependencias y componentes que deben ser trazables.

---

## 2. Problemática identificada

La falta de un proceso formal de solicitud de imágenes puede generar los siguientes problemas:

- Duplicación de imágenes similares por falta de un catálogo centralizado.
- Entornos distintos entre estudiantes de un mismo curso.
- Publicación de imágenes sin escaneo de vulnerabilidades.
- Ausencia de un responsable que apruebe o rechace las solicitudes.
- Falta de trazabilidad sobre quién solicitó, aprobó o publicó una imagen.
- Tiempos de espera prolongados o indefinidos ante una solicitud.
- Uso de imágenes no oficiales o sin firma digital.

### 2.1 Relación entre problema, riesgo y propuesta

| Problema identificado | Riesgo generado | Propuesta de solución |
|---|---|---|
| No existe catálogo centralizado | Duplicación de imágenes y esfuerzo redundante | Búsqueda automática en Harbor antes de crear una nueva imagen |
| Falta de criterio para aprobar/crear | Decisiones inconsistentes entre solicitudes | Definir criterios claros para "usar existente vs. crear nueva" |
| Imágenes sin escaneo | Vulnerabilidades desconocidas en producción | Escaneo obligatorio con Trivy antes de publicar |
| Ausencia de firma digital | Imágenes alteradas o no verificables | Firma digital obligatoria previa a publicación |
| Falta de plazos definidos | Solicitudes sin resolver por tiempo indefinido | SLA de tiempo máximo de respuesta |
| Falta de registro de rechazo | Solicitante no sabe por qué fue rechazada su solicitud | Notificación formal con motivo de rechazo |

---

## 3. Objetivo general

Establecer un proceso claro, seguro y trazable para la solicitud, evaluación, aprobación y publicación de imágenes de contenedores utilizadas en los laboratorios, cursos y proyectos.

---

## 4. Objetivos específicos

- Permitir que docentes y estudiantes soliciten imágenes mediante un procedimiento formal.
- Verificar automáticamente si existe una imagen oficial que cubra la necesidad antes de crear una nueva.
- Garantizar que toda imagen publicada haya sido escaneada por vulnerabilidades y firmada digitalmente.
- Definir responsables claros para cada etapa del proceso.
- Establecer tiempos máximos de respuesta (SLA).
- Registrar el motivo de rechazo cuando una solicitud no sea aprobada.
- Mantener trazabilidad completa desde la solicitud hasta la publicación.

---

## 5. Alcance

La propuesta aplica a:

- Solicitudes realizadas por docentes (para un curso) o por responsables de proyecto.
- Imágenes oficiales publicadas en el registro privado (Harbor).
- Imágenes base y derivadas utilizadas en laboratorios físicos y entornos personales (Docker/Podman).
- El proceso completo desde la solicitud hasta la entrega del enlace de descarga.

No incluye el proceso de actualización de versiones ya publicadas, el cual corresponde a un proceso independiente (Actualización y Mantenimiento de Imágenes).

---

## 6. Roles y responsabilidades

| Rol | Responsabilidad principal |
|---|---|
| Docente / Responsable de proyecto | Solicita la imagen y justifica la necesidad académica o técnica |
| Estudiante | Puede solicitar una imagen cuando el docente lo autorice |
| Responsable de Imágenes | Evalúa la solicitud, decide entre imagen existente o creación, coordina el escaneo y la firma |
| Administrador de Laboratorio | Supervisa el proceso general y resuelve escalamientos |
| Responsable de Seguridad | Revisa los resultados del escaneo de vulnerabilidades |
| Comité de Gestión | Resuelve excepciones o solicitudes de alto impacto |

---

## 7. Matriz RACI

| Actividad | Docente/Solicitante | Responsable de Imágenes | Seguridad | Administrador Lab | Comité |
|---|---:|---:|---:|---:|---:|
| Registrar solicitud | R | I | I | I | I |
| Buscar imagen existente en Harbor | I | R/A | I | I | I |
| Analizar oficial vs. crear | C | A/R | C | I | I |
| Escanear vulnerabilidades | I | C | R | I | I |
| Firmar imagen | I | R | C | I | I |
| Aprobar publicación | I | A | C | C | I |
| Publicar en Harbor | I | R | I | I | I |
| Rechazar solicitud | I | R | C | I | I |
| Resolver excepción | I | C | C | C | A/R |

---

## 8. Descripción detallada del proceso

1. El docente o solicitante registra la solicitud indicando curso/proyecto, necesidad y justificación.
2. El Responsable de Imágenes realiza una **búsqueda automática en Harbor**.
3. Si existe una imagen oficial y actualizada que cubre la necesidad, se entrega el enlace de descarga y el proceso finaliza.
4. Si no existe, se analiza si conviene usar una imagen base oficial (por ejemplo, de Docker Hub verificado) o crear una imagen nueva desde cero.
5. Se construye o adapta la imagen según corresponda.
6. Se ejecuta el **escaneo de vulnerabilidades con Trivy**.
7. Si el escaneo detecta vulnerabilidades críticas o altas, la imagen se corrige y se reescanea antes de continuar.
8. Se aplica la **firma digital** a la imagen.
9. El Responsable de Imágenes aprueba la publicación.
10. La imagen se publica en Harbor junto con sus **metadatos de trazabilidad**.
11. Se notifica al solicitante con el enlace de descarga.

---

## 9. Flujo del proceso

```mermaid
flowchart TD
    A[Solicitud de imagen] --> B[Busqueda automatica en Harbor]
    B --> C{Existe imagen oficial y actualizada?}
    C -- Si --> D[Entrega de enlace de descarga]
    D --> Z[Fin]
    C -- No --> E[Analisis: usar base oficial o crear nueva]
    E --> F[Construccion o adaptacion de la imagen]
    F --> G[Escaneo de vulnerabilidades - Trivy]
    G --> H{Vulnerabilidades criticas o altas?}
    H -- Si --> I[Corregir y reescanear]
    I --> G
    H -- No --> J[Firma digital de la imagen]
    J --> K{Aprobacion del Responsable de Imagenes?}
    K -- No --> L[Rechazo con motivo registrado]
    L --> M[Notificacion al solicitante]
    K -- Si --> N[Publicacion en Harbor con metadatos]
    N --> O[Notificacion al solicitante con enlace]
```

---

## 10. Estados de una solicitud

| Estado | Descripción |
|---|---|
| Registrada | La solicitud fue ingresada por el docente o solicitante |
| En búsqueda | Se verifica si existe imagen oficial equivalente |
| Asignada | Se entregó una imagen existente sin necesidad de crear una nueva |
| En construcción | Se está creando o adaptando una nueva imagen |
| En escaneo | Se evalúan vulnerabilidades con Trivy |
| Observada | El escaneo detectó vulnerabilidades que deben corregirse |
| Firmada | La imagen fue firmada digitalmente |
| Aprobada | Lista para publicación |
| Rechazada | No cumplió los requisitos de seguridad o licencia |
| Publicada | Disponible en Harbor para descarga |

---

## 11. Metadatos de trazabilidad de la imagen

Toda imagen publicada deberá registrar como mínimo:

| Campo | Descripción |
|---|---|
| Identificador de imagen | Nombre y etiqueta (tag) en Harbor |
| Solicitante | Docente o responsable que originó la solicitud |
| Curso o proyecto | Espacio académico donde se utilizará |
| Fecha de solicitud | Momento en que se registró la solicitud |
| Fecha de publicación | Momento en que la imagen quedó disponible |
| Responsable técnico | Persona que construyó o adaptó la imagen |
| Resultado del escaneo | Nivel de vulnerabilidades detectadas y su resolución |
| Firma digital | Identificador de la firma
