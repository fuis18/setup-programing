# Guía para la creación de proyectos de programación

## Lista de documentos

| Documento         | Respuesta                         | Autor                                            |
| ----------------- | --------------------------------- | ------------------------------------------------ |
| `concept.md`      | Qué y por qué                     | Humano (con asistencia de IA)                    |
| `architecture.md` | Estilo, pila, principios, riesgos | IA basada en concept.md                          |
| `design.md`       | Módulos, flujos, datos, contratos | IA basada en architecture.md                     |
| `task.md`         | Qué hacer a continuación          | IA basada en design.md                           |
| `ADR-XXX.md`      | Por qué esta decisión             | IA o humano cuando surge una decisión importante |
| `README.md`       | Cómo acceder al proyecto          | IA al final, cuando todo lo anterior existe      |

## Flujo de trabajo

1. Idea preliminar → concept.md (se completa la plantilla manualmente)
2. concept.md → architecture.md (genera la IA: estilo, arquitectura, principios, decisiones)
3. architecture.md → design.md (genera la IA: módulos, flujos, modelo de datos, contratos)
4. design.md → task.md (genera la IA)
5. architecture.md → ADR-XXXX.md (genera la IA un archivo por cada decisión importante)
6. Todos los anteriores → README.md (genera la IA el último archivo)


**Regla clave:** No continúe con el siguiente paso si el anterior contiene secciones importantes vacías.

En concreto: No genere `architecture.md` sin comprender claramente la arquitectura del sistema y los actores. No genere `design.md` sin un estilo arquitectónico y límites de módulos definidos.

---

## Prompt: concept.md

**Lo que necesitas antes de usar esta sugerencia:**

- Tipo de proyecto (CLI, aplicación web, API, framework, etc.)
- Objetivo principal en una frase
- Funcionalidades principales (aunque sea un borrador)

```
Convierte esta idea en un concepto.md claro, conciso y práctico utilizando la plantilla proporcionada.

Reglas:
- Céntrate en el problema, el objetivo, las partes interesadas y los criterios de éxito.
- NO incluyas detalles de arquitectura, pila tecnológica ni implementación.
- Si la idea no está clara en alguna sección, pregunta en lugar de inventar.
- La sección "Fuera del alcance" es obligatoria; ayuda a definir el alcance del trabajo.
- Sé conciso: una línea por punto siempre que sea posible.

[Pegar idea aquí]
```

---

## Prompt: architecture.md

**Lo que necesitas antes de usar esta herramienta:**

- Un archivo `concept.md` completo (especialmente actores, roles y restricciones)
- Una pila tecnológica definida (o al menos preferida)
- La plantilla `adr_mold.md`

```
Usando este archivo concept.md y la pila tecnológica especificada, genera un archivo architecture.md con la plantilla proporcionada.

Para cada decisión no obvia que encuentres, genera también un archivo ADR con la plantilla adr_mold proporcionada.

Reglas:
- Comience con la pila tecnológica (sección 2): todo lo demás depende de esto.
- Incluya todos los módulos/componentes con sus responsabilidades en una línea cada uno.
- Si el sistema tiene múltiples roles, complete la sección "Roles y permisos".
- En "Contratos e interfaces públicas", incluya al menos los puntos finales o comandos críticos con su respuesta esperada.
- Incluya la estructura del repositorio como un árbol de carpetas.
- Si hay una decisión no obvia (por ejemplo, por qué ese framework, esa base de datos), genere su ADR en línea justo después de architecture.md.
- Si falta información para tomar una decisión, escríbala en "Supuestos abiertos" en lugar de adivinar.

[pegar concept.md aquí]

---
Plantilla ADR:
[pegar adr_mold.md aquí]
```
---

## Prompt: design.md

**Lo que necesitas antes de usar esta solicitud:**

- Un archivo `architecture.md` completo (especialmente el estilo arquitectónico y la pila tecnológica).

```
A partir de este archivo architecture.md, genera un archivo design.md usando la plantilla proporcionada.

Reglas:
- La Sección 1 (Convención de capas/carpetas) debe ser coherente con el estilo arquitectónico de architecture.md.
- Cada módulo de la Sección 2 debe tener una responsabilidad de una sola línea Y un límite de "NO maneja".
- Incluye al menos el flujo de la ruta de ejecución ideal en la Sección 4.
- Los contratos de la Sección 6 deben ser ejecutables tal como están escritos; no se permiten marcadores de posición vagos.
- La estructura del repositorio en la Sección 7 debe coincidir con la convención de carpetas de la Sección 1.

[Pegar architecture.md aquí]
```

---

## Prompt: task.md

**Lo que necesitas antes de usar esta herramienta:**

- Un archivo `design.md` completo

```
A partir de este archivo `design.md`, genera un archivo `task.md` usando la plantilla proporcionada.

Reglas:
- Cada tarea debe poder implementarse en una sesión de trabajo (1-4 horas).
- Si una tarea es extensa, divídela en subtareas.
- Organiza las tareas por módulo, como se define en `architecture.md`.
- Cada módulo debe tener su propio "entregable del módulo": qué funciona cuando el módulo está completo.
- Incluye tareas de prueba dentro de cada módulo, no solo al final.
- Marca las dependencias entre tareas donde existan.
- La sección 0, "Entregable mínimo", debe describir el escenario completo de la prueba de humo para el sistema.

[Pegar architecture.md aquí]
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

- `concept.md`, `architecture.md`,  `design.md`, `task.md` y al menos un ADR

```
A partir de estos documentos, genere un archivo README.md para el repositorio utilizando la plantilla proporcionada.

Reglas:
- La descripción inicial debe ser comprensible para alguien ajeno al proyecto.
- Los requisitos previos deben incluir las versiones mínimas.
- Los comandos de "Cómo ejecutar" deben ser ejecutables tal como están escritos.
- Incluya solo los ADR que un nuevo usuario necesita leer para comprender las decisiones importantes.
- No repita architecture.md ni design.md; cree enlaces a ellos.

[Pegue concept.md aquí]
[Pegue architecture.md aquí]
[Pegue design.md aquí]
[Pegue task.md aquí]
[Pegue los ADR aquí]
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

**El archivo design.md no está listo si:**

- Los módulos no tienen límites claros de "NO maneja".
- La convención de carpetas contradice el estilo arquitectónico.
- Los contratos tienen marcadores de posición vagos en lugar de estructuras de solicitud/respuesta concretas.
- La estructura del repositorio está vacía o es inconsistente con la convención de carpetas.
- No hay flujos definidos (como mínimo, el flujo principal).

**task.md no está listo si:**

- Las tareas no tienen un "entregable del módulo"
- Hay tareas que duran más de un día sin estar divididas
- No hay tareas de testing por módulo
- El "Entregable mínimo" (sección 0) está vacío