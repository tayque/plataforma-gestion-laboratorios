\# 1. Introducción, Problemática y Objetivos

&#x20;

\*\*Sección 1 del Documento de Organización y Gestión de Laboratorios\*\*  

\*\*Responsable:\*\* Cornejo Hurtado, Dario Rafael  

\*\*Fecha:\*\* Julio 2026

&#x20;

\---

&#x20;

\## 1.1 Introducción

&#x20;

\### Alcance del Proyecto

&#x20;

Esta propuesta de \*\*Organización y Gestión de Laboratorios\*\* aplica a:

&#x20;

| Aspecto | Alcance |

|--------|---------|

| \*\*Laboratorios cubiertos\*\* | Laboratorios de Sistemas e Ingeniería de Software de la Escuela Profesional de Ingeniería de Sistemas (EPIS-UNSA), Arequipa |

| \*\*Población estudiantil\*\* | Aproximadamente 450-500 estudiantes (3er a 10mo semestre) |

| \*\*Personal académico\*\* | 15-20 docentes (incluyendo Chapter Leads y coordinadores) |

| \*\*Personal técnico\*\* | 3-5 administradores/técnicos de laboratorio |

| \*\*Máquinas/Recursos\*\* | \~60-80 computadoras de escritorio, 5-10 servidores, impresoras compartidas |

| \*\*Facultades involucradas\*\* | Ingeniería de Sistemas (EPIS) |

| \*\*Fases iniciales\*\* | Fase 1 (Universitaria): Semestres 2026-II y 2026-I (6-8 meses) |

&#x20;

\### Propósito

&#x20;

La plataforma propuesta busca \*\*centralizar, estandarizar y hacer trazable\*\* la gestión de laboratorios de computación en el contexto universitario, para que:

&#x20;

\- Los estudiantes \*\*no pierdan tiempo\*\* en instalaciones manuales repetitivas.

\- Los entornos de desarrollo sean \*\*idénticos\*\* entre el laboratorio y las computadoras personales.

\- Existe \*\*registro auditable\*\* de qué software, versiones y licencias se usaron en cada práctica/proyecto.

\- La transición a un contexto empresarial (Fase 2) sea orgánica, usando la misma plataforma con estándares más altos.

\---

&#x20;

\## 1.2 Problemática Común

&#x20;

\### Problemas Identificados

&#x20;

Los laboratorios de la EPIS actualmente enfrentan las siguientes dificultades:

&#x20;

| # | Problema | Impacto | Frecuencia |

|---|----------|--------|-----------|

| 1 | Pérdida de tiempo en instalaciones y configuraciones manuales | Estudiantes pierden 20-30 min por sesión en setup; reducción de tiempo práctico | Cada sesión de lab |

| 2 | Entornos no estandarizados entre máquinas | Código funciona en una máquina pero no en otra ("funciona en mi máquina") | Constantemente |

| 3 | Falta de trazabilidad del software utilizado | No se sabe qué versiones se usaron en un proyecto; dificulta auditoría académica | Permanente |

| 4 | Dificultad para replicar entornos fuera del laboratorio | Estudiantes no pueden practicar en casa con el mismo ambiente; pierden continuidad | Permanente |

| 5 | Gestión fragmentada de recursos | Hardware, software y usuarios gestionados por diferentes personas/sistemas | Permanente |

| 6 | Escalabilidad limitada | Difícil pasar de un modelo académico a uno empresarial (cambios de infraestructura) | En transición a Fase 2 |

&#x20;

\### Evidencia de la Urgencia

&#x20;

\*\*Datos cualitativos recolectados (Encuesta informal a estudiantes, 2026):\*\*

\- 78% de estudiantes reporta perder 20-30 minutos por sesión en instalaciones/configuraciones.

\- 65% ha experimentado conflictos de versiones ("funciona en mi máquina pero no en el lab").

\- 82% desearía poder trabajar en casa con el mismo entorno del laboratorio.

\*\*Impacto académico:\*\*

\- Reducción promedio de 30-40% en tiempo efectivo de prácticas.

\- Aumento de incidencias reportadas a soporte técnico: \~15-20 por semana.

\- Calidad de proyectos limitada por problemas de entorno, no por conocimiento.

\---

&#x20;

\## 1.3 Objetivos

&#x20;

\### Objetivos Generales

&#x20;

\*\*OG1 (Técnico):\*\* Desarrollar una plataforma híbrida que estandarice y automatice la gestión de laboratorios.

&#x20;

\*\*OG2 (Organizacional):\*\* Establecer una estructura de roles, responsabilidades y procesos claros para que la plataforma se use de forma efectiva, trazable y sostenible.

&#x20;

\### Objetivos Específicos Técnicos

&#x20;

\- \*\*OET1:\*\* Implementar un catálogo centralizado de imágenes Docker versionadas y escaneadas (Harbor + Trivy).

\- \*\*OET2:\*\* Permitir que estudiantes descarguen y ejecuten localmente las imágenes del laboratorio.

\- \*\*OET3:\*\* Garantizar trazabilidad completa del software utilizado (quién lo usó, cuándo, en qué proyecto).

\### Objetivos Específicos Organizacionales ⭐ (Nuevos)

&#x20;

\- \*\*OEO1:\*\* Definir roles y responsabilidades claros para la gestión del laboratorio (Administrador, Jefe de Lab, Responsable de Imágenes, Docentes, Estudiantes).

\- \*\*OEO2:\*\* Establecer procesos documentados y trazables para solicitud, aprobación y distribución de imágenes.

\- \*\*OEO3:\*\* Crear una matriz RACI para todos los procesos críticos (solicitud de imágenes, reserva de equipos, aprobación de software).

\- \*\*OEO4:\*\* Definir políticas claras de seguridad, licencias y auditoría para laboratorio y empresa.

\- \*\*OEO5:\*\* Establecer indicadores de cierre y métricas de éxito para cada étapa del proyecto.

\### Comparativa: Objetivos Técnicos vs Organizacionales

&#x20;

```

Técnicos (Qué se construye)          Organizacionales (Cómo se gestiona)

─────────────────────────────        ──────────────────────────────────

Imágenes Docker                  →   Roles que las solicitan/aprueban

Catálogo centralizado            →   Procesos de validación

Trazabilidad de software         →   Políticas de licencias

CI/CD automatizado               →   Responsables de cada paso

```

&#x20;

\---

&#x20;

\## 1.4 Diagrama: De Problema a Objetivo

&#x20;

```mermaid

graph TD

&#x20;   A\["🔴 PROBLEMA<br/>Entornos no estandarizados<br/>20-30 min perdidos por sesión"] -->|Identifica| B\["📊 CAUSA RAÍZ<br/>Falta gestión centralizada<br/>y procesos claros"]

&#x20;   

&#x20;   B -->|Requiere| C\["🎯 OBJETIVO TÉCNICO<br/>Catálogo de imágenes<br/>+ Trazabilidad"]

&#x20;   

&#x20;   B -->|Requiere| D\["🎯 OBJETIVO ORGANIZACIONAL<br/>Roles, procesos, matriz RACI<br/>+ Políticas de aprobación"]

&#x20;   

&#x20;   C -->|Implementa| E\["✅ SOLUCIÓN<br/>Plataforma Híbrida<br/>Fase 1 Universitaria"]

&#x20;   

&#x20;   D -->|Implementa| E

&#x20;   

&#x20;   E -->|Resultado| F\["🎉 BENEFICIO<br/>Entornos reproducibles<br/>+ Tiempo disponible para práctica<br/>+ Trazabilidad completa"]

```

&#x20;

\---

&#x20;

\## 1.5 Conexión con la Épica 1: Gestión Organizacional y Procesos

&#x20;

\### Épica Fundacional

&#x20;

La \*\*Épica 1\*\* ("Gestión Organizacional y Procesos del Laboratorio") es el cimiento sobre el cual descansan todas las demás épicas del proyecto. Su propósito es \*\*documentar e implementar la organización mínima\*\* requerida para que la plataforma funcione.

&#x20;

\### Indicadores de Cierre para la Épica 1

&#x20;

| Entregable | Criterio de Cierre | Responsable | Plazo (Fase 1) |

|---|---|---|---|

| \*\*Documento de Roles\*\* | Definición clara de 5-7 roles con responsabilidades RACI | Equipo Organización | Semana 2 |

| \*\*Procesos Documentados\*\* | Mínimo 4 procesos críticos (solicitud, aprobación, distribución, auditoría) con flujo claro | Equipo Procesos | Semana 3-4 |

| \*\*Matriz RACI\*\* | Responsable/Accountable/Consulted/Informed definidos para cada proceso | Jefe de Lab + Equipo | Semana 4 |

| \*\*Políticas de Seguridad y Licencias\*\* | Documento de políticas aprobado por autoridades | Software + Legales | Semana 5 |

| \*\*Validación con stakeholders\*\* | Revisión y aprobación por docentes, estudiantes y administración | Chapter Leads | Semana 6 |

&#x20;

\### Por qué estos indicadores importan

&#x20;

Sin criterios de cierre claros, esta épica fundacional corre el riesgo de:

\- Quedar abierta indefinidamente mientras las demás épicas avanzan sin base sólida.

\- Generar inconsistencias entre lo que diseña el equipo técnico y lo que necesita el organizacional.

\- Frenar las épicas dependientes (Épica 2: Usuarios/Permisos, Épica 3: Imágenes).

\*\*Por eso es crítico cerrar bien la Épica 1 antes de avanzar agresivamente.\*\*

&#x20;

\---

&#x20;

\## 1.6 Relación con Otras Secciones del Documento

&#x20;

Este archivo ("Introducción, problemática y objetivos") \*\*establece el "por qué"\*\* del proyecto organizacional. Las secciones siguientes lo complementan así:

&#x20;

| Sección | Propósito | Relación con la Sección 1 |

|---------|-----------|-------------------------|

| 2 - Estructura Organizacional | Define la estructura (Squads, Chapters, Guilds) | Implementa los objetivos OEO1 |

| 3 - Roles de Autoridades | Define quién toma decisiones | Define RACI de aprobación (OEO3) |

| 4 - Roles de Docentes/Estudiantes | Define responsabilidades por nivel | Define participantes en procesos (OEO2) |

| 5 - Proceso Solicitud de Imágenes | Detalla el flujo de solicitud | Implementa política de aprobación (OEO4) |

| 6 - Proceso Reserva de Labs | Detalla gestión de equipos | Implementa políticas de acceso (OEO4) |

| 7 - Gobernanza de Imágenes | Detalla versionado y control | Implementa trazabilidad (OET3 + OEO3) |

| 8 - Software, Licencias y Trazabilidad | Detalla control de licencias | Implementa política de software (OEO4 + OET3) |

&#x20;

\---

&#x20;

\## 1.7 Conclusión

&#x20;

La introducción, problemática y objetivos propuestos en esta sección responden a una necesidad real y documentada en los laboratorios de la EPIS. 

&#x20;

\*\*El objetivo no es solo construir una plataforma técnica\*\*, sino establecer una \*\*gobernanza clara, roles definidos y procesos trazables\*\* que hagan sostenible y escalable la solución, tanto en el contexto universitario como en su evolución hacia el empresarial.

&#x20;

Los objetivos organizacionales (secciones 2-8) son tan críticos como los técnicos, porque sin una estructura clara \*\*ninguna plataforma funciona correctamente\*\*.

&#x20;

\---

&#x20;

\## Bibliografía y Referencias

&#x20;

\- Encuesta informal a estudiantes de EPIS (Julio 2026)

\- Registros de incidencias de soporte técnico (2025-2026)

\- Documento general: "Plataforma Híbrida de Gestión de Laboratorios" (README.md)

\- Backlog inicial: épicas y priorizaciones (backlog/inicial.md)

\- Modelo Spotify adaptado: docs/organizacion-agil.md

\---

&#x20;

\*\*Versión:\*\* 1.0  

\*\*Última actualización:\*\* Julio 2026  

\*\*Estado:\*\* Aprobado para Tarea 2

&#x20;

