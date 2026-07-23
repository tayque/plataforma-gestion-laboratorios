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

| Rol | Responsabilidad |
|---|---|
| Docente solicitante | Pide la imagen y explica para qué curso o proyecto se necesita. |
| Responsable de licencias | Revisa que el software incluido pueda usarse y compartirse. |
| Responsable de imágenes | Construye, prueba, etiqueta y publica la imagen. |
| Responsable técnico | Verifica compatibilidad, seguridad y mantenimiento. |
| Comité o coordinador | Resuelve casos especiales o de alto impacto. |

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
- Las imágenes antiguas deben marcarse como retiradas.

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
