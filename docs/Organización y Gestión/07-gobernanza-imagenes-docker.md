# Gobernanza de imágenes Docker

## Introducción

Las imágenes Docker permiten distribuir entornos idénticos entre el laboratorio y las computadoras personales de los estudiantes. Para que esto funcione bien, las imágenes deben construirse y publicarse con control, trazabilidad y revisión de licencias.

## Problemática

- Algunas imágenes pueden crearse sin saber exactamente qué software contienen.
- No siempre se verifica si las licencias permiten el uso académico o la redistribución.
- Si no existe un SBOM, es difícil saber qué componentes integran una imagen.
- Sin revisión previa, una imagen con vulnerabilidades puede llegar a los usuarios.
- Si no hay responsable, no se sabe quién aprobó, modificó o publicó la versión.

## Objetivo general

Definir un proceso simple y claro para gobernar imágenes Docker usadas en los laboratorios, asegurando seguridad, licencias correctas y trazabilidad.

## Objetivos específicos

- Identificar quién solicita y quién administra cada imagen.
- Revisar licencias antes de publicar o compartir una imagen.
- Generar SBOM para registrar componentes y dependencias.
- Escanear vulnerabilidades antes de aprobar una versión.
- Registrar versión, responsable y fecha de publicación.

## Roles

| Rol | Responsabilidad principal | Nivel de autoridad | Herramientas que usa |
|---|---|---|---|
| Docente solicitante | Inicia la solicitud indicando curso, versión de software y uso previsto. | Propone | Formulario de solicitud, correo institucional |
| Responsable de licencias | Verifica que cada componente de la imagen tenga licencia compatible con uso académico y redistribución. | Aprueba/Rechaza licencia | Registro de licencias, SBOM |
| Responsable de imágenes | Construye, prueba, etiqueta con versión semántica y publica la imagen en Harbor. | Ejecuta | Docker, Harbor, Git |
| Responsable técnico | Realiza el escaneo de vulnerabilidades, evalúa resultados y determina si la imagen es apta. | Aprueba/Rechaza seguridad | Trivy, Harbor Scanner |
| Comité o coordinador | Resuelve casos de licencia ambigua o imágenes de alto impacto; da aprobación final. | Aprobación final | Actas de reunión, registro centralizado |

## Proceso detallado de gobernanza

El proceso se divide en cuatro etapas: **solicitud**, **revisión de licencias**, **revisión técnica** y **publicación**. Cada etapa tiene un responsable y un punto de decisión que puede resultar en aprobación o rechazo.

### Etapa 1 — Solicitud

| Paso | Acción | Responsable |
|---|---|---|
| 1.1 | El docente completa el formulario de solicitud: nombre de imagen, software requerido, versión y curso destino. | Docente solicitante |
| 1.2 | El coordinador recibe la solicitud y verifica que esté completa. | Comité / coordinador |
| 1.3 | Se asigna un código de seguimiento (`IMG-XXX`) y se registra en el sistema. | Comité / coordinador |

### Etapa 2 — Revisión de licencias

| Paso | Acción | Responsable |
|---|---|---|
| 2.1 | El responsable de licencias revisa cada componente declarado en la solicitud. | Responsable de licencias |
| 2.2 | Se consulta el registro de licencias institucional y fuentes oficiales (SPDX). | Responsable de licencias |
| 2.3 | **Si hay componentes con licencia incompatible:** se notifica al docente con justificación escrita y la solicitud queda en estado `Rechazada-Licencia`. El docente puede reformular. | Responsable de licencias |
| 2.4 | **Si todas las licencias son compatibles:** se registra el resultado y se avanza a la etapa 3. | Responsable de licencias |

### Etapa 3 — Construcción y revisión técnica

| Paso | Acción | Responsable | Herramienta |
|---|---|---|---|
| 3.1 | Se construye la imagen en entorno aislado usando un `Dockerfile` versionado en Git. | Responsable de imágenes | Docker, Git |
| 3.2 | Se genera el SBOM (Software Bill of Materials) de la imagen construida. | Responsable de imágenes | Syft (formato CycloneDX o SPDX) |
| 3.3 | Se escanea la imagen en busca de vulnerabilidades conocidas (CVEs). | Responsable técnico | Trivy |
| 3.4 | **Si el escaneo detecta vulnerabilidades CRITICAL o HIGH:** la imagen no puede publicarse. Se notifica al responsable de imágenes para corregir y volver al paso 3.1. | Responsable técnico | Trivy |
| 3.5 | **Si el escaneo es satisfactorio (solo MEDIUM/LOW/NONE):** se firma la imagen digitalmente. | Responsable técnico | Cosign |
| 3.6 | Se sube la imagen firmada al repositorio Harbor con su tag semántico y el SBOM adjunto. | Responsable de imágenes | Harbor |

### Etapa 4 — Aprobación y publicación

| Paso | Acción | Responsable |
|---|---|---|
| 4.1 | El comité revisa el registro completo: licencias, SBOM, resultado de escaneo y firma. | Comité / coordinador |
| 4.2 | Se registra en el catálogo institucional: código, nombre, versión, responsable, fecha, estado `Aprobada`. | Comité / coordinador |
| 4.3 | Se notifica al docente solicitante que la imagen está disponible en Harbor. | Comité / coordinador |
| 4.4 | Los estudiantes pueden descargar la imagen desde Harbor usando `docker pull`. | Estudiantes |

## Reglas básicas

- Toda imagen debe tener un responsable asignado.
- Toda imagen debe publicarse con un tag claro de versión.
- No se publica una imagen sin revisión de licencia.
- No se publica una imagen sin escaneo de seguridad.
- Las imágenes antiguas deben marcarse como retiradas (`deprecated`) antes de eliminarse.
- Ninguna imagen con vulnerabilidades de severidad **CRITICAL** o **HIGH** puede publicarse.

## Política de versionado semántico

Cada imagen publicada debe etiquetarse siguiendo el estándar **SemVer** (`MAYOR.MENOR.PARCHE`):

| Tipo de cambio | Versión que cambia | Ejemplo | Cuándo ocurre |
|---|---|---|---|
| Cambio de SO base o stack principal | MAYOR | `v2.0.0` | Cambio de `ubuntu:20.04` a `ubuntu:22.04` |
| Adición de herramientas o actualización mayor | MENOR | `v1.3.0` | Se añade `nodejs 20` a imagen de desarrollo |
| Parche de seguridad o corrección puntual | PARCHE | `v1.3.1` | Actualización de librería con CVE corregida |

**Reglas adicionales de etiquetado:**

- La etiqueta `latest` apunta siempre a la versión más reciente aprobada.
- Las versiones anteriores permanecen disponibles en Harbor mínimo **1 semestre** antes de marcarse como `deprecated`.
- Nunca se reutiliza un mismo tag para contenido diferente (inmutabilidad de versiones).

## Registro de control de imágenes

Cada imagen aprobada debe tener un registro completo con los siguientes campos mínimos:

| Campo | Descripción | Ejemplo |
|---|---|---|
| Código | Identificador único de la imagen | `IMG-001` |
| Nombre | Nombre descriptivo con curso o proyecto | `python3-laboratorio-bd` |
| Versión | Tag semántico publicado en Harbor | `v1.2.0` |
| Imagen base | Imagen de origen en el `FROM` del Dockerfile | `ubuntu:22.04` |
| Responsable | Nombre del responsable de imágenes | Tania Luz Ayque Puraca |
| Licencias revisadas | Resultado de la revisión (Compatible / Incompatible) | Compatible |
| Resultado Trivy | Nivel máximo de vulnerabilidad encontrada | MEDIUM |
| SBOM | Archivo adjunto en Harbor | `sbom-img-001.json` |
| Firmada | Si la imagen tiene firma digital Cosign | Sí |
| Estado | Estado actual del ciclo de vida | `Aprobada` |
| Fecha de aprobación | Fecha en que el comité aprobó la publicación | 2026-07-23 |
| Fecha de revisión | Próxima fecha de revisión obligatoria | 2027-01-23 |

## Ciclo de vida de una imagen

Una imagen no es permanente. Debe revisarse periódicamente y retirarse cuando quede obsoleta o insegura.

| Estado | Significado | Quién lo cambia | Acción sobre la imagen |
|---|---|---|---|
| `En revisión` | La solicitud está siendo evaluada (licencias o seguridad). | Coordinador | No disponible para estudiantes. |
| `Aprobada` | La imagen pasó todas las revisiones y está publicada. | Comité | Disponible en Harbor con tag `latest`. |
| `Deprecated` | La imagen sigue disponible pero tiene una versión más nueva. | Responsable de imágenes | Harbor la muestra con aviso. Los estudiantes deben migrar. |
| `Rechazada` | La imagen no cumplió requisitos de licencia o seguridad. | Responsable de licencias / técnico | No se publica. Se notifica al solicitante con causa. |
| `Retirada` | La imagen fue eliminada del repositorio activo. | Comité | Solo accesible en archivo histórico por 1 año. |

**Criterios para iniciar el proceso de retiro:**

- Han pasado más de 2 semestres desde la última actualización.
- El escaneo periódico detecta nuevas vulnerabilidades CRITICAL.
- El curso o proyecto para el que se creó ya no existe.
- La imagen base (`FROM`) alcanzó su fecha de fin de soporte oficial.

## Recomendaciones

| # | Recomendación | Herramienta sugerida | Prioridad |
|---|---|---|---|
| 1 | Usar un repositorio privado institucional para publicar imágenes | Harbor | Alta |
| 2 | Escanear vulnerabilidades antes de aprobar cualquier imagen | Trivy | Alta |
| 3 | Generar SBOM en formato estándar para cada imagen | Syft (CycloneDX / SPDX) | Alta |
| 4 | Usar versionado semántico en todos los tags | SemVer | Alta |
| 5 | Firmar digitalmente las imágenes aprobadas | Cosign | Media |
| 6 | Revisar imágenes activas al inicio de cada semestre | — | Media |
| 7 | Automatizar el escaneo periódico con integración CI/CD | GitLab CI + Trivy | Media |
| 8 | Capacitar a docentes en el proceso de solicitud | — | Baja |
