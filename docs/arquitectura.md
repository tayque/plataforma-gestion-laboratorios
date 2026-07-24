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

**A favor:**
- La elección de **Harbor** es acertada: es el estándar para registros privados de imágenes, con control de acceso, escaneo integrado y firma digital. Evita depender de Docker Hub, que tiene límites de descarga y no garantiza disponibilidad offline.

**Observaciones:**
- **Falta:** Política de licencias del software dentro de las imágenes (propietario vs. libre). Sin ella, una imagen podría distribuirse con software comercial sin autorización, generando riesgo legal.
- **Falta:** Política de versionado (SemVer). Sin tags claros, dos versiones distintas pueden tener el mismo tag `latest`, rompiendo la reproducibilidad que es el objetivo central del proyecto.
- **Falta:** Flujo de actualización y parches de imágenes ya publicadas. Si se detecta una vulnerabilidad nueva, no hay proceso para notificar usuarios ni retirar la versión afectada.
- **Falta:** Seguridad de red entre componentes. Se listan GitLab, Harbor, Keycloak, PostgreSQL y MinIO pero no se describe cómo se comunican de forma segura (TLS, redes internas, secretos).
- **Propuesta:** Añadir flujo explícito: solicitud → revisión de licencia → construcción aislada → SBOM → escaneo Trivy → firma Cosign → publicación en Harbor.