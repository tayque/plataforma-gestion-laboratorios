# 1. Introducción, Problemática y Objetivos

**Sección 1 del Documento de Organización y Gestión de Laboratorios**

**Responsable:** Cornejo Hurtado, Dario Rafael

**Fecha:** Julio 2026

---

## 1.1 Introducción

### Alcance del Proyecto

Esta propuesta de **Organización y Gestión de Laboratorios** aplica específicamente a:

| Aspecto | Alcance |
|--------|---------|
| **Laboratorios cubiertos** | Laboratorios de Sistemas e Ingeniería de Software de la Escuela Profesional de Ingeniería de Sistemas (EPIS-UNSA), Arequipa |
| **Población estudiantil** | Aproximadamente 450-500 estudiantes (3er a 10mo semestre) |
| **Personal académico** | 15-20 docentes (incluyendo Chapter Leads y coordinadores) |
| **Personal técnico** | 3-5 administradores/técnicos de laboratorio |
| **Máquinas y recursos** | 60-80 computadoras de escritorio, 5-10 servidores, impresoras compartidas |
| **Facultades involucradas** | Ingeniería de Sistemas (EPIS) |
| **Horizonte temporal** | Fase 1 (Universitaria): Semestres 2026-II y 2026-I (6-8 meses) |

### Propósito de la Plataforma

La plataforma propuesta busca **centralizar, estandarizar y hacer trazable** la gestión de laboratorios de computación en el contexto universitario. Esto permitirá:

- **Eliminar pérdidas de tiempo:** Los estudiantes no perderán 20-30 minutos por sesión en instalaciones manuales repetitivas.
- **Garantizar consistencia:** Los entornos de desarrollo serán idénticos entre el laboratorio y las computadoras personales de los estudiantes.
- **Registrar auditoría:** Existirá un registro completo de qué software, versiones y licencias se utilizaron en cada práctica o proyecto.
- **Facilitar transición empresarial:** La transición a un contexto empresarial (Fase 2) será orgánica, utilizando la misma plataforma con estándares más altos.

---

## 1.2 Problemática Común

### Problemas Actuales en los Laboratorios de la EPIS

Los laboratorios de la EPIS enfrentan actualmente las siguientes dificultades operativas:

| # | Problema | Impacto Directo | Frecuencia |
|---|----------|-----------------|-----------|
| 1 | Pérdida de tiempo en instalaciones y configuraciones manuales | Estudiantes pierden 20-30 minutos por sesión en setup; reducción directa de tiempo práctico | Cada sesión de laboratorio |
| 2 | Entornos no estandarizados entre máquinas | Código funciona en una máquina pero no en otra ("funciona en mi máquina") | Constantemente durante proyectos |
| 3 | Falta de trazabilidad del software utilizado | No se registra qué versiones se usaron; dificulta auditoría académica y soporte técnico | Permanente |
| 4 | Dificultad para replicar entornos fuera del laboratorio | Estudiantes no pueden practicar en casa con el mismo ambiente; pierden continuidad de aprendizaje | Permanente |
| 5 | Gestión fragmentada de recursos | Hardware, software y usuarios gestionados por diferentes personas/sistemas sin coordinación | Permanente |
| 6 | Escalabilidad limitada | Difícil pasar de un modelo académico a uno empresarial sin cambios de infraestructura | En transición a Fase 2 |

### Evidencia de la Urgencia

**Datos cualitativos (Encuesta informal a estudiantes, Julio 2026):**

- **78%** de estudiantes reporta perder 20-30 minutos por sesión en instalaciones y configuraciones
- **65%** ha experimentado conflictos de versiones ("funciona en mi máquina pero no en el laboratorio")
- **82%** desearía poder trabajar en casa con el exacto mismo entorno del laboratorio

**Impacto académico cuantificado:**

- Reducción promedio de **30-40%** en tiempo efectivo dedicado a prácticas
- Aumento de incidencias reportadas a soporte técnico: **15-20 por semana**
- Calidad de proyectos limitada por problemas de entorno, no por conocimiento o competencia técnica

### Análisis de Causa Raíz

La raíz de estos problemas es la **falta de una estructura organizacional clara** que defina:

- **Quién** solicita, aprueba y distribuye las imágenes de entorno
- **Cómo** se documentan y validan las configuraciones
- **Qué** políticas rigen el software y las licencias
- **Cuándo** y **por qué** se actualizan los entornos

Sin estos elementos organizacionales, aunque se construya una plataforma técnica, esta no funcionará de forma sostenible o escalable.

---

## 1.3 Objetivos

### Objetivos Generales del Proyecto

**OG1 (Dimensión Técnica):** Desarrollar una plataforma híbrida (on-premise + nube) que automatice y estandarice la gestión de laboratorios de computación.

**OG2 (Dimensión Organizacional):** Establecer una estructura clara de roles, responsabilidades y procesos que permita usar la plataforma de forma efectiva, trazable y sostenible.

### Objetivos Específicos Técnicos

- **OET1:** Implementar un catálogo centralizado de imágenes Docker versionadas y escaneadas (Harbor + Trivy).
- **OET2:** Permitir que estudiantes descarguen y ejecuten localmente las imágenes del laboratorio.
- **OET3:** Garantizar trazabilidad completa del software utilizado (quién lo usó, cuándo, en qué proyecto).

### Objetivos Específicos Organizacionales (Nuevos)

Estos objetivos responden directamente a los problemas identificados y complementan la visión técnica:

- **OEO1:** Definir roles y responsabilidades claros para la gestión del laboratorio (Administrador, Jefe de Laboratorio, Responsable de Imágenes, Docentes, Estudiantes).
  
- **OEO2:** Establecer procesos documentados y trazables para solicitud, aprobación y distribución de imágenes.
  
- **OEO3:** Crear una matriz RACI (Responsable/Accountable/Consulted/Informed) para todos los procesos críticos: solicitud de imágenes, reserva de equipos, aprobación de software.
  
- **OEO4:** Definir políticas claras y documentadas de seguridad, gestión de licencias y auditoría, tanto para laboratorio como para empresa.
  
- **OEO5:** Establecer indicadores de cierre explícitos y métricas de éxito para cada etapa del proyecto.

### Relación entre Objetivos Técnicos y Organizacionales

No son independientes. El siguiente cuadro muestra cómo se complementan:

| Aspecto Técnico | Aspecto Organizacional | Resultado Integrado |
|-----------------|----------------------|-------------------|
| Imágenes Docker versionadas | Roles que solicitan/aprueban imágenes | Proceso completo de solicitud-aprobación-distribución |
| Catálogo centralizado (Harbor) | Procesos documentados de validación | Repositorio confiable y auditable |
| Trazabilidad de software | Políticas de licencias y seguridad | Cumplimiento normativo y legal |
| CI/CD automatizado | Responsables de cada paso | Gobernanza clara y trazable |

---

## 1.4 Conexión con la Épica 1: Gestión Organizacional y Procesos

### Por Qué la Épica 1 es Fundacional

La **Épica 1** ("Gestión Organizacional y Procesos del Laboratorio") es el cimiento sobre el cual descansan todas las demás épicas del proyecto. Su propósito es **documentar e implementar la organización mínima** requerida para que la plataforma funcione correctamente.

Todas las siguientes épicas dependen de que Épica 1 esté resuelta:

- **Épica 2 (Usuarios/Permisos):** necesita definición clara de roles de Épica 1
- **Épica 3 (Catálogo de Imágenes):** necesita procesos de solicitud/aprobación de Épica 1
- **Épica 4+ (Procesos, Auditoría):** necesitan políticas de Épica 1

### Indicadores de Cierre Propuestos para Épica 1

Sin criterios de cierre claros, esta épica corre el riesgo de quedar abierta indefinidamente mientras las demás avanzan. Por eso se proponen los siguientes indicadores concretos:

| Entregable | Criterio de Cierre | Responsable | Plazo Estimado |
|---|---|---|---|
| **Documento de Roles** | Definición clara de 5-7 roles con responsabilidades específicas y matriz RACI | Equipo de Organización | Semana 2 |
| **Procesos Documentados** | Mínimo 4 procesos críticos documentados con flujo claro: solicitud, aprobación, distribución, auditoría | Equipo de Procesos | Semana 3-4 |
| **Matriz RACI Completa** | Responsable/Accountable/Consulted/Informed definidos para cada proceso crítico | Jefe de Lab + Equipo | Semana 4 |
| **Políticas de Licencias y Seguridad** | Documento aprobado por autoridades de EPIS definiendo reglas de software, licencias y acceso | Equipo de Software + Legales | Semana 5 |
| **Validación con Stakeholders** | Revisión y aprobación formal por docentes, estudiantes y administración | Chapter Leads | Semana 6 |

**Importancia de estos indicadores:**

Sin ellos, la épica fundacional corre el riesgo de:
- Quedar abierta indefinidamente mientras las épicas dependientes avanzan sin una base sólida
- Generar inconsistencias entre lo que diseña el equipo técnico y lo que necesita el equipo organizacional
- Frenar las épicas 2, 3 y siguientes que no tendrán claridad sobre roles y procesos

---

## 1.5 Relación con Otras Secciones del Documento

Este archivo ("Introducción, problemática y objetivos") **establece el "por qué"** del proyecto organizacional. Las siguientes 7 secciones del documento implementan concretamente estos objetivos:

| Sección | Propósito | Cómo Implementa Esta Sección 1 |
|---------|-----------|------------------------------|
| **2. Estructura Organizacional** | Define la estructura de equipos (Squads, Chapters, Guilds) | Implementa objetivos OEO1 (roles claros) |
| **3. Roles de Autoridades y Encargados** | Define quién toma decisiones y aprueba | Define RACI de aprobación (OEO3) |
| **4. Roles de Docentes, Estudiantes y Personal Técnico** | Define responsabilidades por nivel | Define participantes en procesos (OEO2) |
| **5. Proceso de Solicitud de Imágenes** | Detalla el flujo completo de solicitud | Implementa política de aprobación (OEO4) |
| **6. Proceso de Reserva de Laboratorios** | Detalla gestión de equipos y acceso | Implementa políticas de acceso (OEO4) |
| **7. Gobernanza de Imágenes Docker** | Detalla versionado, escaneo y control | Implementa trazabilidad (OET3 + OEO3) |
| **8. Software, Licencias y Trazabilidad** | Detalla control de licencias y auditoría | Implementa política de software (OEO4 + OET3) |

Cada sección posterior es una "pieza del rompecabezas" que hace operativo lo definido aquí en términos de objetivos.

---

## 1.6 Conclusión

Los problemas identificados en esta sección responden a una necesidad real y documentada en los laboratorios de la EPIS. La solución propuesta no es solo una plataforma técnica, sino una **gobernanza clara, roles definidos y procesos trazables** que hagan sostenible y escalable la solución.

**Punto clave:** Los objetivos organizacionales (secciones 2-8 de este documento) son tan críticos como los objetivos técnicos del proyecto general. Sin una estructura clara de cómo usar la plataforma, ninguna solución técnica funciona correctamente.

El siguiente paso es que cada sección (2 a 8) desarrolle en detalle cómo implementa los objetivos planteados aquí.

---

## Referencias y Fuentes

- Encuesta informal a estudiantes de EPIS (Julio 2026)
- Registros de incidencias de soporte técnico (2025-2026)
- Documento general: "Plataforma Híbrida de Gestión de Laboratorios" (README.md)
- Backlog inicial: épicas y priorizaciones (backlog/inicial.md)
- Modelo Spotify adaptado: docs/organizacion-agil.md

---

**Versión:** 1.0  
**Última actualización:** Julio 2026  
**Estado:** Aprobado para implementación