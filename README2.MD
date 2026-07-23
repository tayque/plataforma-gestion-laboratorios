# Plataforma Híbrida de Gestión de Laboratorios de Computación

**Proyecto Académico-Empresarial**  
**Carrera de Sistemas / Ingeniería de Software**  
**Universidad [Nombre]**  
**Versión:** 1.0  
**Fecha:** Julio 2026

## Tabla de Contenidos

- [Introducción](README.md#introducción)
- [Problemática Común](#problemática-común)
- [Objetivos](#objetivos)
- [Justificación y Beneficios](#justificación-y-beneficios)
- [Modelo Organizacional](#modelo-organizacional-ágil-spotify-adaptado)
- [Arquitectura](#arquitectura-técnica-propuesta)
- [Fases del Proyecto](#fases-de-implementación)

---

## Introducción

Este proyecto busca desarrollar una **plataforma híbrida** (local + nube) para la gestión integral de laboratorios de computación, aplicable en universidades y empresas de software.

- COMENTARIO – CORNEJO HURTADO, DARIO:
- La introducción no delimita el alcance real del proyecto: no se indica
- cuántos laboratorios existen actualmente, a qué facultad o carreras
- pertenecen, ni cuántos estudiantes y docentes se verían involucrados.
- Sin esta delimitación, es difícil dimensionar correctamente los roles,
- procesos y políticas que se van a proponer en el documento de
- Organización y Gestión, ya que no se sabe si está pensado para un
- laboratorio piloto o para todos los de la universidad.

---

## Problemática Común

- Pérdida de tiempo en instalaciones manuales por parte de estudiantes y administradores.
- Entornos no estandarizados entre computadoras.
- Falta de trazabilidad del software utilizado.
- Dificultad para replicar el entorno del laboratorio en las computadoras personales de los alumnos.
- Gestión ineficiente de hardware y recursos.

- COMENTARIO – CORNEJO HURTADO, DARIO:
- La problemática se presenta de forma cualitativa, sin ningún dato que
- respalde su urgencia (por ejemplo, tiempo promedio perdido en
- instalaciones, número de incidencias por semestre, o resultados de
- una encuesta a estudiantes/docentes). Sin evidencia concreta, es
- difícil justificar ante las autoridades por qué este proyecto debe
- priorizarse frente a otras iniciativas de la facultad.

---

## Objetivos

**General:** Desarrollar una plataforma que estandarice, automatice y trace los entornos de desarrollo en laboratorios.

**Específicos:**
- Gestión centralizada de hardware y usuarios.
- Catálogo de imágenes de contenedores (Docker) con procesos automáticos.
- Trazabilidad completa del software.
- Posibilidad de que los alumnos descarguen y usen las mismas imágenes en sus PCs.
- Dos versiones: Académica y Empresarial (con estándares más altos).

- COMENTARIO – CORNEJO HURTADO, DARIO:
- Los objetivos listados están orientados casi exclusivamente a la
- plataforma técnica (imágenes, contenedores, versiones académica y
- empresarial), pero el documento de Organización y Gestión requiere
- objetivos propios sobre estructura organizacional, roles y políticas
- (tal como indica el objetivo general de ese documento). Se propone
- añadir objetivos específicos como: "Definir roles y responsabilidades
- claras para la gestión del laboratorio" y "Establecer una matriz RACI
- para los procesos críticos", que hoy no aparecen en ningún objetivo.
---

## Justificación y Beneficios

- **Universidad:** Ahorro de tiempo para estudiantes y administradores. Entornos reproducibles.
- **Industria:** Formación con estándares profesionales reales.
- **Trazabilidad:** Registro auditable de todas las imágenes y herramientas utilizadas.

---

## Modelo Organizacional Ágil (Spotify Adaptado)

Ver detalle completo en: [`docs/organizacion-agil.md`](docs/organizacion-agil.md)

## Arquitectura Técnica Propuesta

Ver detalle completo en: [`docs/arquitectura.md`](docs/arquitectura.md)

## Gestión de Imágenes y Trazabilidad

Ver detalle completo en: [`docs/gestion-imagenes.md`](docs/gestion-imagenes.md)

## Fases de Implementación

Ver detalle completo en: [`docs/fases-implementacion.md`](docs/fases-implementacion.md)

## Anexos

- [Requisitos de Roles y Habilidades](docs/roles-habilidades.md)
- [Cuadro Comparativo de Conocimientos](docs/roles-habilidades.md#cuadro-comparativo)
- [Plan de Dedicación](docs/plan-dedicacion.md)

---

**Estado:** Propuesta Inicial  
**Licencia:** MIT