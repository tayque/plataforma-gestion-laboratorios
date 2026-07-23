# Gestión de Imágenes y Trazabilidad

## Flujo Principal

1. Solicitud de imagen (Proyecto o Curso)
2. Búsqueda automática en Harbor
3. Si no existe → Responsable revisa y aprueba creación
4. Escaneo de vulnerabilidades (Trivy)
5. Firma de imagen
6. Publicación con metadatos de trazabilidad
7. Estudiantes pueden descargar la imagen oficial

**Beneficio clave:** Los alumnos trabajan con el **mismo entorno** dentro y fuera del laboratorio.

## Comentario — Camila Alarico Pacheco 

### Sobre "Gestión de Imágenes y Trazabilidad"

1. **Falta el rechazo en el flujo.** El paso 3 dice "Responsable revisa y aprueba creación", pero no contempla qué pasa si se **rechaza** la solicitud, ni quién notifica al solicitante ni con qué justificación.

2. **El escaneo de vulnerabilidades tiene criterio de corte.** Se menciona el escaneo como paso 4, pero no se define qué nivel de severidad bloquea la publicación. Sin esto, el escaneo es informativo, no un control real.

3. **No se especifica qué son los "metadatos de trazabilidad".** El paso 6 los menciona pero no detalla qué incluyen (autor, fecha, hash de la imagen, versión base, resultado del escaneo). Esto es clave para que la trazabilidad sea auditable.

**Sugerencia:** agregar un paso de notificación de rechazo, definir el umbral de severidad que bloquea el escaneo y especificar el contenido mínimo de los metadatos de trazabilidad.
