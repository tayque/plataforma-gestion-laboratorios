# Organizaciones Ágiles para Problemas Complejos

**El Modelo Spotify aplicado a un caso real: la Plataforma Híbrida de Gestión de Laboratorios de Computación**

Curso de Organización y Métodos · Julio 2026

---

## 1. Introducción

La disciplina de Organización y Métodos (O&M) estudia cómo diseñar estructuras, procesos y flujos de trabajo que permitan a una institución cumplir sus objetivos de forma eficiente. Durante décadas, ese diseño se apoyó en organigramas jerárquicos, manuales de procedimientos estáticos y una separación clara entre quien planifica y quien ejecuta. Ese enfoque funciona razonablemente bien cuando el problema a resolver es estable, repetitivo y predecible.

El presente material aborda un escenario distinto: el diseño organizacional para problemas complejos, es decir, problemas con múltiples partes interesadas, tecnología cambiante, requisitos que emergen sobre la marcha y alta incertidumbre. Para este tipo de problemas, las organizaciones ágiles —y en particular el Modelo Spotify— ofrecen un marco de diseño organizacional alternativo. Se utiliza como hilo conductor un caso real: el proyecto de una Plataforma Híbrida de Gestión de Laboratorios de Computación, que aplica precisamente este modelo.

---

## 2. Problemas complejos: por qué la organización tradicional no basta

### 2.1 El entorno VUCA

La sigla VUCA (Volatility, Uncertainty, Complexity, Ambiguity) describe entornos donde el cambio es rápido y difícil de anticipar (volatilidad), la información disponible es insuficiente para predecir resultados (incertidumbre), existen múltiples variables interconectadas (complejidad) y las relaciones causa-efecto no son claras (ambigüedad). La mayoría de los proyectos tecnológicos actuales —desarrollo de plataformas, transformación digital, integración de sistemas— se desenvuelven en este tipo de entorno.

### 2.2 El marco Cynefin: distinguir tipos de problema

El marco Cynefin, desarrollado por Dave Snowden, clasifica los problemas en cuatro dominios y es útil para decidir qué tipo de organización aplicar a cada uno:

- **Simple (claro):** relación causa-efecto evidente. Se resuelve con procedimientos estandarizados y buenas prácticas. Ejemplo: check-in de un equipo en el inventario.
- **Complicado:** requiere conocimiento experto para identificar la solución, pero es analizable. Ejemplo: configurar una red o un clúster de Kubernetes.
- **Complejo:** la relación causa-efecto solo se comprende en retrospectiva; no hay una única solución correcta de antemano. Requiere experimentar, observar y adaptar ("probar-sentir-responder"). Ejemplo: diseñar un catálogo de imágenes de contenedores que satisfaga a la vez a estudiantes, docentes y empresas.
- **Caótico:** no hay relación causa-efecto discernible; se requiere actuar primero para estabilizar la situación. Ejemplo: una caída total del laboratorio en plena evaluación.

> **Idea central:** los problemas complejos no se resuelven con más planificación anticipada, sino con estructuras organizacionales que permitan experimentar rápido, aprender del error y ajustar el rumbo con frecuencia.

Una organización jerárquica clásica —con aprobaciones en cascada y especialización rígida por departamento— es eficiente para lo simple y lo complicado, pero se vuelve lenta y frágil frente a lo complejo: cada cambio de requisito debe atravesar varios niveles de aprobación, y el conocimiento queda fragmentado entre silos que no se comunican con fluidez.

---

## 3. Agilidad organizacional (más allá del equipo)

La agilidad organizacional traslada los principios ágiles —iteración corta, entrega incremental, retroalimentación continua, autonomía del equipo— desde el nivel de un solo equipo de desarrollo hacia el diseño de la organización completa. No se trata solo de que un equipo use Scrum o Kanban, sino de repensar cómo se agrupan las personas, cómo fluye la autoridad y cómo se coordinan múltiples equipos que trabajan en un mismo problema complejo.

### 3.1 El equilibrio entre autonomía y alineación

El reto central del diseño organizacional ágil es lograr que los equipos tengan autonomía suficiente para decidir cómo resolver un problema (sin esperar aprobaciones de arriba hacia abajo para cada decisión técnica), y al mismo tiempo mantengan alineación con los objetivos estratégicos de la organización, evitando que cada equipo tome direcciones contradictorias entre sí.

Cuando la autonomía es alta pero la alineación es baja, el resultado es caos: equipos desconectados, duplicación de esfuerzo, inconsistencias. Cuando la alineación es alta pero la autonomía es baja, el resultado es una burocracia lenta que no logra adaptarse a la complejidad del problema. El diseño organizacional ágil busca maximizar ambas dimensiones a la vez.

---

## 4. El Modelo Spotify

El Modelo Spotify es un patrón de diseño organizacional que la empresa Spotify popularizó (aunque la propia compañía aclara que evolucionó y nunca fue un modelo "cerrado") para escalar equipos ágiles manteniendo autonomía y alineación. Se estructura en cuatro unidades:

### 4.1 Squad

Es la unidad básica: un equipo pequeño, multidisciplinario (5-9 personas) y autónomo, con todas las competencias necesarias para diseñar, construir y entregar una parte del producto de principio a fin, con mínima dependencia de otros equipos. Cada squad tiene una misión clara y actúa casi como una "mini-startup" dentro de la organización.

### 4.2 Tribe

Agrupa varios squads que trabajan en un área de producto relacionada (por ejemplo, toda la plataforma de un mismo proyecto). El tribe coordina la visión general y evita que los squads dupliquen esfuerzos o pierdan coherencia entre sí.

### 4.3 Chapter

Es la agrupación transversal de personas que comparten la misma disciplina o especialidad (por ejemplo, todos los desarrolladores backend, aunque estén repartidos en distintos squads). El chapter garantiza estándares técnicos comunes, mentoría y desarrollo profesional dentro de la disciplina, sin frenar la autonomía diaria del squad.

### 4.4 Guild

Es una comunidad de interés informal y voluntaria que cruza toda la organización (por ejemplo, un guild de seguridad o de accesibilidad), abierta a cualquiera interesado en el tema, independientemente de su squad, tribe o chapter. Sirve para compartir conocimiento de forma orgánica.

| Unidad | Tipo de agrupación | Propósito principal |
|---|---|---|
| Squad | Multidisciplinaria, por misión de producto | Entregar valor de forma autónoma y de punta a punta |
| Tribe | Conjunto de squads relacionados | Alinear visión y coordinar dependencias entre squads |
| Chapter | Por disciplina/especialidad técnica | Estandarizar calidad técnica y desarrollo profesional |
| Guild | Comunidad de interés voluntaria | Compartir conocimiento transversal |

*El resultado es una matriz: cada persona pertenece "verticalmente" a un squad (donde entrega valor día a día) y "horizontalmente" a un chapter (donde mantiene su desarrollo técnico), y opcionalmente participa en guilds temáticos.*

---

## 5. Por qué este diseño encaja con problemas complejos

- Reduce el tamaño del lote de decisión: al ser autónomo, un squad puede probar una solución, observar el resultado y corregir el rumbo en días, no en meses.
- Distribuye el conocimiento experto sin fragmentarlo: los chapters evitan que cada squad reinvente sus propios estándares.
- Permite escalar sin perder identidad de producto: los tribes agrupan squads por área de negocio, no por función, lo que mantiene el foco en el problema del usuario.
- Favorece el aprendizaje continuo, coherente con el dominio "complejo" de Cynefin: probar, sentir, responder, en vez de planificar-ejecutar-controlar.

---

## 6. El caso: Plataforma Híbrida de Gestión de Laboratorios de Computación

### 6.1 El problema

Los laboratorios de computación universitarios y las empresas de software comparten un mismo dolor: gestión fragmentada de recursos físicos y digitales, tiempo perdido en instalaciones manuales, entornos no estandarizados ("funciona en mi máquina"), falta de trazabilidad del software utilizado, y dificultad para que un estudiante replique en su propia computadora el mismo entorno del laboratorio.

El proyecto propone una plataforma híbrida (local + nube) que integre gestión de hardware, usuarios, proyectos/cursos, repositorios de código (GitLab) y un catálogo centralizado de imágenes de contenedores (Docker/Harbor), garantizando estandarización, trazabilidad y reproducibilidad.

### 6.2 ¿Por qué es un problema complejo (y no solo complicado)?

Aplicando el marco Cynefin al caso: no existe una única arquitectura "correcta" conocida de antemano, porque las necesidades de un aula universitaria (bajo presupuesto, alta rotación de estudiantes) difieren de las de una empresa (seguridad, cumplimiento, SLAs). Los requisitos emergerán con el uso real, hay múltiples interesados con intereses distintos (estudiantes, docentes, administradores de TI, empresas) y la tecnología base (contenedores, Kubernetes, identidad, seguridad) evoluciona constantemente. Esto ubica al proyecto en el dominio complejo de Cynefin: se requiere experimentar con fases piloto, observar el uso real y adaptar el diseño, no un plan cerrado desde el inicio.

### 6.3 Aplicación del Modelo Spotify: el Tribe "Platform Lab"

El proyecto organiza a los estudiantes y docentes bajo un Tribe único llamado "Platform Lab", que evoluciona en dos fases secuenciales.

| Fase 1 – Proyecto Universitario | Fase 2 – Proyecto Empresa (evolución) |
|---|---|
| Squad Core Platform | Squad Core Enterprise Platform |
| Squad Image & Container Management | Squad Advanced Image & Security |
| Squad Hardware & Lab Operations | Squad Hardware Fleet & Hybrid Operations |
| Squad Frontend & User Experience | Squad Enterprise Experience & Analytics |
| — | Squad Integration & Ecosystem |

Cada squad es multidisciplinario y responsable de una porción vertical del producto (por ejemplo, el squad de imágenes cubre desde el diseño hasta la entrega del catálogo de contenedores), replicando el mismo principio de autonomía de punta a punta que define al Modelo Spotify.

### 6.4 Chapters liderados por docentes

Los Chapters agrupan a los estudiantes por especialidad técnica, transversalmente a los squads, y están liderados por profesores con un mínimo de cinco años de experiencia en la industria, lo que aporta mentoría real y estándares profesionales:

- Chapter Backend & Arquitectura
- Chapter DevOps & Platform Engineering
- Chapter Security & Compliance
- Chapter Frontend & UX

### 6.5 El dilema organizacional: ¿dónde ubicar la gestión de procesos?

Durante la planificación del backlog surgió una pregunta típica del diseño organizacional ágil: los procesos administrativos del laboratorio (reserva de equipos, aprobación de imágenes, matriz RACI, indicadores de uso) ¿ameritan un squad propio? El equipo del proyecto descartó esa opción porque un squad dedicado solo a procesos generaría un silo desconectado de la ejecución técnica y sería costoso en recursos.

> **Solución adoptada:** un Chapter de "Organización y Procesos" liderado por un docente con experiencia en Gestión de Proyectos o ITIL, combinado con un rol de Process Owner (u "Organization Champion") dentro de cada squad, dedicado parcialmente a documentar los procesos de su propia área.

Esta decisión ilustra en la práctica el principio de autonomía + alineación: cada squad sigue siendo dueño de sus procesos (autonomía), mientras el Chapter transversal garantiza una matriz RACI y estándares comunes (alineación), sin crear una estructura burocrática separada del trabajo técnico diario.

### 6.6 Cadencia y artefactos ágiles del proyecto

- Dedicación semanal: 15-20 horas/estudiante en la Fase 1 (Universitaria) y 20-25 horas/estudiante en la Fase 2 (Empresa).
- Ritmo de coordinación: 2 reuniones de squad y 1 revisión con el Chapter (docente) por semana.
- Backlog priorizado con MoSCoW (Must/Should/Could/Won't have), organizado en épicas: Organización y Procesos, Usuarios y Permisos, Catálogo de Imágenes, Hardware e Inventario, Frontend, Arquitectura base.
- Fases de implementación: Análisis y Diseño (1 mes) → Proyecto Universitario (4-6 meses) → Evolución a Proyecto Empresa (5-7 meses) → Piloto → Mejora continua.

---

## 7. Lecciones para el diseño organizacional

- La estructura debe reflejar el tipo de problema: procesos simples/complicados admiten jerarquía y procedimiento; problemas complejos requieren squads autónomos que aprendan iterando.
- La agilidad organizacional no elimina la necesidad de coordinación: los Chapters y la matriz RACI muestran que "ágil" no significa "sin estructura", sino una estructura distinta, orientada a autonomía con alineación.
- Los dilemas organizacionales (como "¿dónde va Organización y Procesos?") rara vez se resuelven creando más unidades separadas; con frecuencia la mejor respuesta es un rol transversal combinado con una responsabilidad distribuida dentro de cada equipo.
- Un mismo diseño organizacional (Tribe → Squads → Chapters) puede evolucionar de un contexto académico a uno empresarial simplemente ajustando el número y enfoque de los squads, sin rediseñar el modelo desde cero.

---

## 8. Conclusiones

El caso de la Plataforma Híbrida de Gestión de Laboratorios muestra que Organización y Métodos, aplicada a problemas complejos, no consiste en imponer un procedimiento fijo sino en diseñar una estructura —el Modelo Spotify, en este ejemplo— que permita a equipos autónomos aprender, adaptarse y coordinarse con el resto de la organización. Para el estudiante de O&M, el valor del caso está en observar cómo una decisión organizacional concreta (dónde ubicar el Chapter de Organización y Procesos) se deriva directamente de los principios teóricos de autonomía, alineación y del dominio "complejo" del marco Cynefin.

---

## 9. Preguntas de discusión

1. ¿Qué otros procesos del laboratorio caen en el dominio "complicado" (procedimiento claro) frente a los que caen en el dominio "complejo" (requieren experimentación)?
2. Si el proyecto creciera a 10 squads, ¿en qué punto convendría dividir el Tribe "Platform Lab" en dos tribes independientes?
3. ¿Qué riesgos organizacionales aparecen si el rol de Process Owner dentro de cada squad no tiene tiempo protegido para documentar procesos?
4. ¿Cómo mediría usted, con indicadores concretos, si el modelo está logrando el equilibrio entre autonomía y alineación?

---

## 10. Respuestas de los integrantes a las preguntas de discusión

### Respuestas — Huaynacho Mango, Jerry Anderson

**1. ¿Qué otros procesos del laboratorio caen en el dominio "complicado" frente a los que caen en el dominio "complejo"?**

En el dominio **complicado** caen los procesos que tienen una solución correcta conocida y solo requieren conocimiento experto para ejecutarse: la reserva de laboratorios y horarios, el alta y baja de usuarios con sus permisos, el inventario y mantenimiento preventivo del hardware, el escaneo de vulnerabilidades de una imagen con Trivy y la renovación de licencias de software. Todos ellos pueden documentarse en un procedimiento y automatizarse.

En el dominio **complejo** caen los procesos cuyo resultado solo se entiende en retrospectiva y requieren experimentar: definir la política de priorización cuando varios cursos compiten por los mismos recursos, decidir qué imágenes merecen entrar al catálogo oficial (las necesidades reales emergen con el uso), diseñar el modelo de gobernanza entre docentes, estudiantes y administradores de TI, y lograr la adopción de la plataforma por parte de los usuarios. En estos casos conviene lanzar pilotos, observar el uso real y ajustar, en lugar de fijar un procedimiento cerrado desde el inicio.

**2. Si el proyecto creciera a 10 squads, ¿en qué punto convendría dividir el Tribe "Platform Lab" en dos tribes independientes?**

Convendría dividir cuando el Tribe deja de cumplir su propósito: alinear una visión común. Las señales concretas serían tres. Primero, cuando aparecen dos áreas de producto con usuarios y objetivos claramente distintos (por ejemplo, la plataforma académica y la plataforma empresarial), de modo que las reuniones de coordinación tratan temas que ya no interesan a la mitad de los squads. Segundo, cuando el número de personas supera lo que un Tribe Lead puede coordinar con relaciones de confianza (la literatura sugiere alrededor de 40-100 personas, y 10 squads de 5-9 miembros ya bordean ese límite). Tercero, cuando las dependencias cruzadas entre squads de distinta área se vuelven la excepción y no la regla. En el caso del proyecto, el corte natural sería un tribe "Plataforma Académica" y otro "Plataforma Empresarial", manteniendo los Chapters transversales a ambos para no fragmentar los estándares técnicos.

**3. ¿Qué riesgos organizacionales aparecen si el rol de Process Owner dentro de cada squad no tiene tiempo protegido para documentar procesos?**

El riesgo principal es que la documentación de procesos siempre pierde frente a la presión de entregar funcionalidad, porque es trabajo importante pero no urgente. Las consecuencias en cadena serían: procesos que solo existen en la cabeza de algunos miembros (conocimiento tácito), lo cual es grave en un contexto universitario con alta rotación de estudiantes por semestre; una matriz RACI desactualizada que genera confusión de responsabilidades ante incidentes; pérdida de trazabilidad de las decisiones (¿por qué se aprobó esta imagen?, ¿quién autorizó este cambio?); y a mediano plazo, la desaparición práctica del rol, con lo que se repetiría el silo que el diseño quiso evitar, pero ahora sin nadie a cargo. La mitigación es tratar la documentación como trabajo del sprint: reservarle un porcentaje fijo de la dedicación semanal e incluirla en la definición de terminado de cada entrega.

**4. ¿Cómo mediría usted, con indicadores concretos, si el modelo está logrando el equilibrio entre autonomía y alineación?**

Para la **autonomía** mediría: (a) porcentaje de decisiones técnicas que el squad resuelve sin escalar al Chapter o al Tribe (meta: mayoría de decisiones locales); (b) lead time desde que el squad decide un cambio hasta que lo entrega, pues los tiempos largos suelen delatar aprobaciones en cascada; y (c) número de bloqueos por dependencia de otro squad por sprint.

Para la **alineación** mediría: (d) porcentaje de entregas que cumplen los estándares definidos por los Chapters (revisiones de código, seguridad, documentación); (e) retrabajo por inconsistencias entre squads, por ejemplo dos squads resolviendo el mismo problema de forma incompatible (meta: tendencia a cero); y (f) el resultado de una encuesta corta trimestral donde cada miembro evalúa "entiendo cómo mi trabajo aporta al objetivo del Tribe".

El equilibrio se logra cuando ambos grupos de indicadores son buenos a la vez: si (a)-(c) son buenos pero (d)-(f) malos, hay caos (autonomía sin alineación); si ocurre lo contrario, hay burocracia (alineación sin autonomía).
