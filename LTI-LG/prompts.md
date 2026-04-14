# Prompts utilizados — LTI-LG

Este archivo documenta los prompts utilizados con Claude (claude-sonnet-4-6) para generar el documento de diseño `LTI-LG.md`.

## Prompt 1 — Definición de funcionalidades clave del ATS

**Herramienta:** Claude Code (claude-sonnet-4-6)

**Rol asignado en el prompt:**
> Eres un product manager experto, con experiencia en sistemas de gestión de recursos humanos.

**Prompt completo:**
```
Eres un product manager experto, con experiencia en sistemas de gestión de recursos humanos. Definí funcionalidades clave para desarrollar el ATS (Applicant-Tracking System) del futuro, teniendo como premisas:
- Aumentar la eficiencia para los departamentos de HR
- Mejorar la colaboración en tiempo real entre reclutadores y managers
- Automatizaciones
- Asistencia de IA en diversas tareas
```

**Output obtenido:** Listado estructurado de 7 categorías de funcionalidades con subfuncionalidades detalladas: Gestión Inteligente de Candidatos, Colaboración en Tiempo Real, Automatizaciones, Asistencia de IA, Experiencia del Candidato, Analítica e Inteligencia de Negocio, y Compliance y Datos.

---

## Prompt 2 — Generación del documento de diseño completo (LTI-LG.md)

**Herramienta:** Claude Code (claude-sonnet-4-6) via skill `/create-lti-software-design-document`

**Prompt completo (argumentos del skill):**
El prompt de entrada fue el output completo del Prompt 1 (funcionalidades del ATS) pasado como argumento al skill de generación de documentos de diseño.

**Instrucciones del skill aplicadas:**
El skill instruyó al modelo para actuar como senior software architect y product strategist, generando un documento con la siguiente estructura obligatoria:
1. Product overview (3-4 párrafos)
2. Main features (5-8 features con descripción)
3. Lean Canvas (prose + diagrama Mermaid block-beta)
4. Use cases (3 casos de uso con diagramas de secuencia Mermaid)
5. Data model (entidades con atributos y diagrama ER en Mermaid)
6. High-level system design (4 párrafos + diagrama hub-and-spoke Mermaid)
7. C4 diagram (3 niveles: context, container, component con diagramas Mermaid)

**Decisiones de diseño tomadas por el modelo:**
- Arquitectura: monolito modular (justificado para v1 por velocidad y coherencia transaccional)
- Stack tecnológico sugerido: Node.js + TypeScript, React, PostgreSQL + pgvector, Redis/BullMQ, S3-compatible storage
- Componente C4 elegido: AI Gateway (elegido por ser el más crítico arquitectónicamente — impacta costos, latencia y disponibilidad de funcionalidades IA)
- Los tres casos de uso priorizados: (1) Screening automatizado con IA, (2) Evaluación colaborativa post-entrevista, (3) Handoff automático a onboarding

**Output obtenido:** Documento completo `LTI-LG.md` con todos los artefactos requeridos por el ejercicio.
