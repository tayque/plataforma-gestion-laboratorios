# Arquitectura Técnica Propuesta

## Modelo General
**Híbrido**: Local (On-Premise) + Nube

## Componentes Principales

- **GitLab** → Código fuente y CI/CD
- **Harbor** → Registro privado de imágenes de contenedores
- **Keycloak** → Gestión de identidad y acceso
- **Proxmox VE** → Virtualización de hardware
- **Kubernetes** → Orquestación de contenedores
- **PostgreSQL + MinIO** → Base de datos y almacenamiento

## Flujo Recomendado
Estudiantes → Descargan imagen → Ejecutan localmente con Docker/Podman → Entorno idéntico al laboratorio.

## Comentario — Tania Luz Ayque Puraca

- **Falta:** Especificar cómo se manejarán las licencias del software dentro de imágenes (propietario vs. libre).
- **Falta:** Política de versionado de imágenes (tags semánticos, branches, ciclo de vida).
- **Falta:** Flujo de actualización/parches de imágenes ya publicadas.
- **Propuesta:** Añadir proceso: solicitud → revisión de licencia → SBOM → escaneo Trivy → firma → publicación Harbor.