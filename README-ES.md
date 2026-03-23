# Guía de creación de proyectos de programación

## Relación de documentos

| Documento         | Responde                | Quién lo escribe                                 |
| ----------------- | ----------------------- | ------------------------------------------------ |
| `concept.md`      | Qué y por qué           | Humano (con ayuda de IA)                         |
| `architecture.md` | Cómo                    | IA a partir de concept.md                        |
| `task.md`         | Qué hacer ahora         | IA a partir de architecture.md                   |
| `ADR-XXX.md`      | Por qué esta decisión   | IA o humano cuando surge una decisión importante |
| `README.md`       | Cómo entrar al proyecto | IA al final, cuando todo lo anterior existe      |

## Flujo de trabajo

```
1. idea rough → concept.md         (humano completa el molde)
2. concept.md → architecture.md    (IA genera)
3. architecture.md → task.md       (IA genera)
4. architecture.md → ADR-XXXX.md   (IA genera uno por decisión importante)
5. todos los anteriores → README.md (IA genera al final)
```

**Regla clave:** no pasar al siguiente paso si el anterior tiene secciones vacías importantes.  
Específicamente: no generar `architecture.md` sin tener claro el stack y los actores del sistema.

---

## Prompt: concept.md

**Qué necesitas antes de usar este prompt:**
- Tipo de proyecto (CLI, web app, API, framework, etc.)
- Objetivo principal en una frase
- Funciones principales (aunque sea en borrador)

```
Toma esta idea y conviértela en un concept.md claro, breve y accionable usando el molde proporcionado.

Reglas:
- Mantén el foco en problema, objetivo, actores y criterio de éxito
- NO incluyas arquitectura, stack tecnológico ni detalles de implementación
- Si la idea no está clara en alguna sección, escribe una pregunta en lugar de inventar
- La sección "Fuera de alcance" es obligatoria — ayuda a delimitar el trabajo
- Sé conciso: una línea por punto donde sea posible

[pegar idea aquí]
```

---

## Prompt: architecture.md

**Qué necesitas antes de usar este prompt:**
- `concept.md` completo (especialmente actores, funciones y restricciones)
- Stack tecnológico decidido (o al menos preferido)

```
A partir de este concept.md y el stack indicado, genera un architecture.md usando el molde proporcionado.

Reglas:
- Empieza por el Stack tecnológico (sección 2) — todo lo demás depende de esto
- Incluye todos los módulos/componentes con su responsabilidad en una línea cada uno
- Si el sistema tiene múltiples roles, completa la sección "Roles y permisos"
- En "Contratos e interfaces públicas" incluye al menos los endpoints o comandos críticos con su respuesta esperada
- Incluye la estructura del repositorio como árbol de carpetas
- Si hay una decisión no obvia (ej: por qué ese framework, esa base de datos), márcala como candidato a ADR
- Si falta información para tomar una decisión, escríbelo en "Supuestos abiertos" en lugar de inventar

[pegar concept.md aquí]
```

---

## Prompt: task.md

**Qué necesitas antes de usar este prompt:**
- `architecture.md` completo

```
A partir de esta architecture.md, genera un task.md usando el molde proporcionado.

Reglas:
- Cada tarea debe ser implementable en una sesión de trabajo (1-4 horas)
- Si una tarea es más grande, divídela en subtareas
- Organiza las tareas por módulo, igual que están definidos en architecture.md
- Cada módulo debe tener su propio "entregable del módulo" — qué funciona cuando ese módulo está completo
- Incluye tareas de testing dentro de cada módulo, no solo al final
- Marca dependencias entre tareas cuando existan
- La sección 0 "Entregable mínimo" debe describir el escenario de smoke test completo del sistema

[pegar architecture.md aquí]
```

---

## Prompt: ADR

**Cuándo escribir un ADR:**  
Cuando una decisión técnica cambia el stack, la estructura del repositorio, el modelo de datos o cómo se comunican los módulos. Si te preguntas si merece ADR, probablemente sí.

```
Genera un ADR usando el molde proporcionado para la siguiente decisión:

Decisión: [nombre de lo que se eligió]
Contexto: [por qué hubo que decidir algo]
Alternativas que consideramos: [lista]

Reglas:
- El título del ADR debe decir qué se decidió, no qué se evaluó
- En "Consecuencias negativas" sé honesto — todo tiene trade-offs
- En "Impacto en la arquitectura" indica qué secciones de architecture.md afecta
```

---

## Prompt: README.md

**Qué necesitas antes de usar este prompt:**
- `concept.md`, `architecture.md`, `task.md` y al menos un ADR

```
A partir de estos documentos, genera un README.md para el repositorio usando el molde proporcionado.

Reglas:
- La descripción inicial debe poder entenderla alguien externo al proyecto
- Los requisitos previos deben incluir versiones mínimas
- Los comandos de "Cómo correrlo" deben ser ejecutables tal como están escritos
- Lista solo los ADRs que alguien nuevo necesita leer para entender las decisiones importantes
- No repitas architecture.md — enlázalo

[pegar concept.md + architecture.md aquí]
```

---

## Señales de que el documento no está listo para pasar al siguiente paso

**concept.md no está listo si:**
- No tiene actores definidos
- Las funciones principales son más de 10 o son vagas
- "Fuera de alcance" está vacío
- El objetivo no es verificable

**architecture.md no está listo si:**
- El stack tecnológico no está definido
- Los módulos no tienen responsabilidades claras
- No hay contratos/interfaces mínimas definidas
- La estructura del repositorio está vacía
- Hay decisiones importantes sin ADR candidato

**task.md no está listo si:**
- Las tareas no tienen un "entregable del módulo"
- Hay tareas que duran más de un día sin estar divididas
- No hay tareas de testing por módulo
- El "Entregable mínimo" (sección 0) está vacío