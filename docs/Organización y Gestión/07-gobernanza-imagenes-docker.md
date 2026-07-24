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

## Proceso mínimo

1. Se recibe la solicitud con nombre de la imagen, versión y uso previsto.
2. Se revisan licencias y restricciones de redistribución.
3. Se construye la imagen en un entorno controlado.
4. Se genera el SBOM de la imagen.
5. Se escanea la imagen con una herramienta de vulnerabilidades.
6. Se corrigen observaciones si las hay.
7. Se aprueba y se publica en el repositorio institucional.
8. Se registra responsable, versión, fecha y estado.

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

## Ejemplos de control

| Campo | Ejemplo |
|---|---|
| Código | IMG-001 |
| Nombre | imagen-curso-python |
| Versión | v1.0.0 |
| Responsable | Tania Luz Ayque Puraca |
| Licencia | MIT |
| SBOM | sbom-img-001.json |
| Estado | Aprobada |
| Fecha | 2026-07-23 |

## Recomendaciones

- Repositorio privado institucional para publicar imágenes.
- Escaneo con Trivy antes de aprobar.
- SBOM en formato CycloneDX o SPDX.
- Etiquetas semánticas para cada versión.
