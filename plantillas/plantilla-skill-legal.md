---
id: "[tema-en-kebab-case]"
titulo: "[Nombre humano de la skill]"
estado: borrador   # borrador | en-verificacion | verificada | requiere-actualizacion
ultima_revision: "[AAAA-MM-DD]"
revisado_por: "[quién verificó contra fuente oficial, y en calidad de qué — p. ej. fundador / abogado laboral]"
---

<!-- ═══════════════════════════════════════════════════════════════════════
CÓMO USAR ESTA PLANTILLA — borra este bloque al crear una skill real

1. Copia este archivo a: skills/<tema-en-kebab-case>.md
   El nombre del archivo debe ser idéntico al campo `id` del frontmatter.
2. Una skill = UN tema operativo (jornada, horas extra, aguinaldo...), no una
   ley completa. Una skill puede citar varias leyes a la vez; el amarre con
   cada ley vive en la sección (a).
3. Llena las secciones en orden. La (a) siempre primero: si no hay fuente
   verificable, no hay skill.
4. Reemplaza todo lo que esté [entre corchetes]. Ningún corchete puede
   sobrevivir en una skill con estado `verificada` — lo que no se sepa se
   registra como pregunta abierta en (d), nunca se inventa.
5. Los demás comentarios <!-- --> son guías de llenado: no se ven al renderizar
   en GitHub y pueden quedarse en el archivo final.

REGLAS NO NEGOCIABLES
- En (a) NO se interpreta: solo citas textuales y datos verificables en el DOF.
- Se cita siempre el TEXTO VIGENTE del artículo (el de la última reforma que
  lo tocó), no el texto original de la ley.
- En (c) NO se copia ley: solo lógica implementable, anclada a fuentes por ID.
- Toda revisión se registra en (e), incluso si no cambió nada
  ("revisado, sin cambios").
- Cadena de trazabilidad: F-xx (fuente) → RD-xx (regla) → código y tests de
  Klokk. Los IDs son estables y nunca se reciclan.
═══════════════════════════════════════════════════════════════════════ -->

# [Título de la skill]

> **Pregunta operativa que responde:** [en una línea: qué duda concreta de la
> operación diaria resuelve esta skill — p. ej. "¿cuándo una hora trabajada
> cuenta como X?"]

---

## (a) Fuente legal exacta

<!-- Solo hechos verificables. Cero interpretación, cero paráfrasis.
     Cada fuente recibe un ID estable (F-01, F-02...). -->

| ID   | Instrumento              | Artículo / fracción   | Última reforma en DOF | Link oficial |
|------|--------------------------|-----------------------|-----------------------|--------------|
| F-01 | [Ley / NOM / Reglamento] | [Art. NN, fracción X] | [AAAA-MM-DD]          | [URL de dof.gob.mx u otra fuente oficial] |
| F-02 | [...]                    | [...]                 | [AAAA-MM-DD]          | [...]        |

### Texto citado

<!-- Copia textual del artículo vigente, entre comillas, sin resumir ni
     modernizar la redacción. Si el artículo es largo, cita únicamente los
     párrafos relevantes e indícalo con [...]. -->

**F-01 — [Art. NN, Instrumento]:**

> "[Cita textual del artículo, copiada del texto vigente publicado en el DOF.]"

**F-02 — [Art. NN, Instrumento]:**

> "[Cita textual.]"

---

## (b) Interpretación operativa

<!-- Qué significa (a) en la práctica, en lenguaje claro. Sin jerga jurídica;
     si un término legal es inevitable, defínelo aquí mismo. -->

**Para una empresa (el empleador):**

[Qué obligación o derecho concreto genera esto en el día a día de una PyME:
qué debe hacer, cuándo, y qué le pasa si no lo hace.]

**Para Klokk (el producto):**

[Qué debe registrar, calcular, limitar o alertar Klokk para que sus clientes
cumplan con esto.]

---

## (c) Reglas derivadas

<!-- La lógica que un desarrollador convierte en código SIN tomar decisiones
     legales propias. Cada regla declara: cuándo aplica, la lógica exacta
     (fórmula, umbrales, unidades, redondeos, husos horarios si aplican) y las
     fuentes de (a) que la respaldan.
     Si al escribir una regla aparece una ambigüedad: NO se resuelve aquí — se
     registra como CL-xx en (d) y la regla queda marcada como parcial. -->

### RD-01 — [nombre corto de la regla]

- **Aplica cuando:** [condición de entrada, sin ambigüedad]
- **Regla:** [lógica exacta: fórmula, umbral, unidad, redondeo]
- **Fuente:** F-01
- **Notas de implementación:** [opcional — precisión decimal, orden de
  operaciones, zona horaria, referencias a CL-xx que la afectan]

### RD-02 — [nombre corto de la regla]

- **Aplica cuando:** [...]
- **Regla:** [...]
- **Fuente:** [F-01, F-02]

---

## (d) Casos límite y preguntas abiertas

<!-- Dónde la ley es ambigua, guarda silencio, o falta que la autoridad
     publique disposiciones. Una pregunta abierta NO bloquea publicar la
     skill, pero tiene que quedar registrada. IDs estables: CL-01, CL-02... -->

| ID    | Caso o pregunta       | Por qué es ambiguo                | Estado  | Quién lo resuelve |
|-------|-----------------------|-----------------------------------|---------|-------------------|
| CL-01 | [situación concreta]  | [qué dice la ley y qué NO dice]   | abierta | [abogado / autoridad pendiente de publicar / decisión de producto] |
| CL-02 | [...]                 | [...]                             | abierta | [...]             |

<!-- Cuando un caso se resuelva: cambia su estado a "resuelta", documenta cómo
     y cuándo (aquí mismo o en una nota bajo la tabla), y si la resolución
     produce lógica nueva, créala como una RD-xx y registra el cambio en (e). -->

---

## (e) Estado y última revisión

<!-- El estado VIGENTE vive en el frontmatter — una sola fuente de verdad,
     legible por máquina. Aquí vive el historial humano: quién revisó qué,
     cuándo y contra qué fuente. Toda revisión se registra, sin excepción. -->

**Regla de caducidad:** si `ultima_revision` tiene más de [N meses — umbral
por definir], esta skill se trata como `requiere-actualizacion` aunque el
frontmatter diga otra cosa.

| Fecha        | Revisó   | Qué se verificó o cambió       | Fuente contrastada |
|--------------|----------|--------------------------------|--------------------|
| [AAAA-MM-DD] | [nombre] | Creación inicial de la skill   | [edición del DOF u otra fuente oficial] |
