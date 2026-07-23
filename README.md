# Plataforma Híbrida de Gestión de Laboratorios de Computación

**Proyecto Académico-Empresarial**  
**Carrera de Sistemas / Ingeniería de Software**  
**Universidad [Nombre de la Universidad]**  
**Versión:** 1.0 (Propuesta)  
**Fecha:** Julio 2026

---

## 📋 Tabla de Contenidos

- [Introducción](#introducción)
- [Problemática Común](#problemática-común)
- [Objetivos](#objetivos)
- [Justificación y Beneficios](#justificación-y-beneficios)
- [Enfoque Metodológico](#enfoque-metodológico)
- [Modelo Organizacional Ágil (Spotify Adaptado)](#modelo-organizacional-ágil-spotify-adaptado)
- [Requisitos de Conocimientos y Habilidades](#requisitos-de-conocimientos-y-habilidades)
- [Arquitectura Técnica Propuesta](#arquitectura-técnica-propuesta)
- [Gestión de Imágenes y Trazabilidad](#gestión-de-imágenes-y-trazabilidad)
- [Fases de Implementación](#fases-de-implementación)
- [Conclusiones y Recomendaciones](#conclusiones-y-recomendaciones)
- [Anexos](#anexos)

---

## Introducción

Este proyecto propone el desarrollo de una **Plataforma Híbrida** para la gestión integral de laboratorios de computación, aplicable tanto en entornos universitarios como en empresas de software.

La solución combina gestión de hardware (computadoras, servidores, impresoras), usuarios, proyectos/cursos, repositorios de código (GitLab) y un catálogo centralizado de imágenes de contenedores (Docker), garantizando **estandarización, trazabilidad y reproducibilidad** de entornos.

```diff
- COMENTARIO – CORNEJO HURTADO, DARIO:
- La introducción no delimita el alcance real del proyecto: no se indica
- cuántos laboratorios existen actualmente, a qué facultad o carreras
- pertenecen, ni cuántos estudiantes y docentes se verían involucrados.
- Sin esta delimitación, es difícil dimensionar correctamente los roles,
- procesos y políticas que se van a proponer en el documento de
- Organización y Gestión, ya que no se sabe si está pensado para un
- laboratorio piloto o para todos los de la universidad.
```

---

## Problemática Común

Los laboratorios universitarios y las empresas de software enfrentan problemas similares:

- Gestión fragmentada de recursos físicos y digitales.
- Pérdida significativa de tiempo en instalaciones y configuraciones manuales.
- Entornos no estandarizados que generan inconsistencias ("funciona en mi máquina").
- Falta de trazabilidad del software e imágenes utilizadas.
- Dificultad para replicar entornos entre laboratorio y computadoras personales de estudiantes/desarrolladores.
- Escalabilidad limitada al pasar de academia a industria.

**En el ámbito universitario** se busca especialmente que los alumnos **no pierdan tiempo** en instalaciones y que puedan llevarse las mismas imágenes oficiales a sus computadoras personales para practicar fuera del laboratorio.

```diff
- COMENTARIO – CORNEJO HURTADO, DARIO:
- La problemática se presenta de forma cualitativa, sin ningún dato que
- respalde su urgencia (por ejemplo, tiempo promedio perdido en
- instalaciones, número de incidencias por semestre, o resultados de
- una encuesta a estudiantes/docentes). Sin evidencia concreta, es
- difícil justificar ante las autoridades por qué este proyecto debe
- priorizarse frente a otras iniciativas de la facultad.
```

---

## Objetivos

### Objetivo General
Desarrollar una plataforma híbrida (local + nube) que permita la gestión estandarizada, segura y trazable de laboratorios de computación en contextos académicos y empresariales.

### Objetivos Específicos
- Implementar catálogo centralizado de imágenes de contenedores con procesos automatizados.
- Gestionar usuarios, proyectos/cursos y recursos físicos de forma eficiente.
- Garantizar trazabilidad completa del software utilizado.
- Permitir a los estudiantes descargar y ejecutar localmente las imágenes del laboratorio.
- Crear dos versiones: Académica y Empresarial (con estándares superiores).
- Formar estudiantes bajo metodologías ágiles reales (Modelo Spotify).

```diff
- COMENTARIO – CORNEJO HURTADO, DARIO:
- Los objetivos listados están orientados casi exclusivamente a la
- plataforma técnica (imágenes, contenedores, versiones académica y
- empresarial), pero el documento de Organización y Gestión requiere
- objetivos propios sobre estructura organizacional, roles y políticas
- (tal como indica el objetivo general de ese documento). Se propone
- añadir objetivos específicos como: "Definir roles y responsabilidades
- claras para la gestión del laboratorio" y "Establecer una matriz RACI
- para los procesos críticos", que hoy no aparecen en ningún objetivo.
```

---

## Justificación y Beneficios

**Beneficios Universitarios:**
- Ahorro de tiempo para estudiantes y administradores.
- Entornos idénticos y reproducibles.
- Mayor calidad de proyectos y prácticas.
- Trazabilidad académica.

**Beneficios Empresariales:**
- Plataforma lista para entornos productivos.
- Estudiantes formados con estándares profesionales.
- Reducción de riesgos operativos.

---

## Enfoque Metodológico

El proyecto se desarrollará utilizando el **Modelo Spotify** adaptado al contexto universitario:

- **Tribe:** Platform Lab
- **Squads** multidisciplinarios (5-9 miembros)
- **Chapters** liderados por profesores con experiencia en industria
- **Guilds** temáticos

Se ejecutarán dos proyectos secuenciales:
1. **Proyecto Universitario** (Fase 1)
2. **Proyecto Empresa** (Fase 2)

---

## Modelo Organizacional Ágil (Spotify Adaptado)

### Squads Principales

**Proyecto 1 - Universitario**
- Squad Core Platform
- Squad Image & Container Management
- Squad Hardware & Lab Operations
- Squad Frontend & User Experience

**Proyecto 2 - Empresa** (evolución)
- Squad Core Enterprise Platform
- Squad Advanced Image & Security
- Squad Hardware Fleet & Hybrid Operations
- Squad Enterprise Experience & Analytics
- Squad Integration & Ecosystem

Los **Chapters** serán liderados por profesores con mínimo 5 años de experiencia industrial.

---

## Requisitos de Conocimientos y Habilidades

### Cuadro Comparativo (Resumen)

| Rol                          | Proyecto 1 (Nivel)     | Tiempo Mín. Práctica | Proyecto 2 (Nivel)      | Tiempo Mín. Práctica |
|-----------------------------|------------------------|----------------------|-------------------------|----------------------|
| Tech Lead / Arquitecto      | Avanzado              | 2 semestres         | Senior                 | 4 semestres         |
| Backend Developer           | Intermedio-Avanzado   | 2 semestres         | Avanzado               | 3-4 semestres       |
| DevOps / Platform Engineer  | Intermedio            | 1-2 semestres       | Senior                 | 3-4 semestres       |
| Security Engineer           | Básico-Intermedio     | 1 semestre          | Avanzado               | 2-3 semestres       |
| UX/UI Designer              | Intermedio            | 1-2 semestres       | Avanzado               | 2-3 semestres       |

**Requisitos Generales:**
- Proyecto 1: 3er-4to semestre, promedio mínimo 14, portafolio GitHub.
- Proyecto 2: Haber participado en Proyecto 1 (preferible), conocimientos avanzados en Kubernetes, GitOps y Seguridad.

---

## Arquitectura Técnica Propuesta

- **Modelo Híbrido**: On-premise (Proxmox + Kubernetes) + Nube
- **Componentes principales**:
  - GitLab (código y CI/CD)
  - Harbor (Registry de imágenes)
  - Keycloak (Identity & Access)
  - PostgreSQL + MinIO
- **Infraestructura**: Proxmox VE, Kubernetes (K3s/Talos), Ansible + Terraform

---

## Gestión de Imágenes y Trazabilidad

**Flujo Principal:**
1. Solicitud de imagen
2. Búsqueda automática en Harbor
3. Creación/Importación + Escaneo (Trivy)
4. Firma digital y aprobación
5. Publicación con metadatos
6. Descarga segura por estudiantes
7. Actualizaciones controladas

Esto garantiza **estandarización y trazabilidad completa**.

**Comentario — Tania Luz Ayque Puraca:**
- **Fase 0:** Inventario inicial de software, definición de SBOM obligatorio, criterios de escaneo Trivy, firma digital de imágenes.
- **Falta:** Rol explícito de "Responsable de Licencias" en estructura organizacional.
- **Falta:** Proceso de transición de licencias académicas a comerciales (Fase 1 → Fase 2).

---

## Fases de Implementación

1. Análisis y Diseño (1 mes)
2. Desarrollo Proyecto Universitario (4-6 meses)
3. Evolución a Proyecto Empresa (5-7 meses)
4. Piloto y Puesta en Producción
5. Mejora Continua

---

## Conclusiones y Recomendaciones

Esta plataforma representa una oportunidad estratégica para modernizar los laboratorios de la universidad, elevar la calidad formativa y generar un activo tecnológico de alto valor transferable a la industria.

**Recomendaciones:**
- Aprobar como proyecto inter-cátedra.
- Asignar presupuesto para infraestructura base.
- Formalizar participación de profesores como Chapter Leads.

---

## Anexos

### Anexo 1: Tabla Detallada de Roles y Habilidades

*(Ver documento complementario `roles-habilidades.md`)*

### Anexo 2: Diagrama de Arquitectura (C4)

*(Se incluirán diagramas en formato PlantUML o Draw.io dentro de la carpeta `/docs/architecture`)*

### Anexo 3: Backlog Inicial de Épicas

*(Ver carpeta `/backlog`)*

### Anexo 4: Plan de Dedicación Semanal por Squad

*(Ver documento `plan-dedicacion.md`)*

### Anexo 5: Estimación de Costos Iniciales

*(Ver documento `costos.md`)*

---

## Cómo Contribuir

1. Leer el [Code of Conduct](CODE_OF_CONDUCT.md)
2. Seguir las [guías de contribución](CONTRIBUTING.md)
3. Crear issues y pull requests

---

**Licencia:** MIT  
**Estado del Proyecto:** Propuesta Inicial (En fase de aprobación)

---

