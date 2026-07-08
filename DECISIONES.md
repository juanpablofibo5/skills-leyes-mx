# DECISIONES — log de decisiones del repo

Registro append-only. Cada decisión: qué se decidió, por qué, y quién la tomó.

| ID | Fecha | Decisión | Por qué / contexto |
|----|-------|----------|--------------------|
| D-01 | 2026-07-06 | Nombre oficial del producto: **Klokk** (una sola "c"); repo `klokk-skills-leyes`. | JP lo confirmó al detectarse la discrepancia con "Klockk"; coincide con logos y portafolio. |
| D-02 | 2026-07-06 | Una skill = un tema operativo, no una ley completa. | La LFT entera en un archivo sería inmantenible; la unidad de consumo es la regla operativa. |
| D-03 | 2026-07-06 | No se guardan PDFs del DOF en el repo; se enlaza a la fuente oficial y se cita documento + página. | Evitar peso y duplicación; el DOF es la fuente, git versiona nuestro texto. |
| D-04 | 2026-07-07 | Formato v2 — Agent Skills (carpeta + SKILL.md + references/ + assets/). La anatomía (a)–(e) sobrevive como checklist mapeado. | La spec de registro-jornada lo exigía; es el formato que el repo principal de Klokk consumirá. |
| D-05 | 2026-07-07 | R5 de `registro-jornada` (histórico) clasifica en la rama **ALTO** del árbol de severidad. | La spec traía inconsistencia interna (tabla: Alto; árbol: MEDIO; caso 4: ALTO). JP eligió alinear al riesgo Alto — Arts. 784/804 exigen conservar y exhibir. |
| D-06 | 2026-07-07 | Ninguna skill sube a `verificada` sin abogado; la fase 3 se hace UNA vez, sobre la librería completa. | Secuencia elegida por JP: primero construir todo, luego validación legal única. |
| D-07 | 2026-07-07 | Las specs de fase 1 las produce Claude contra fuente oficial descargada; **gate: visto bueno de JP** antes de construir. | Elegido por JP entre tres modelos de producción; equilibra velocidad y control humano. |
| D-08 | 2026-07-07 | Fuera de alcance del catálogo: aguinaldo, PTU y cálculo de nómina. | Klokk correlaciona horas con nómina (R9) pero no calcula pagos. Se reabre si el producto cambia. |
| D-09 | 2026-07-07 | Calendario de horas extra corregido: gradual 9/9/10/11/12 (2026–2030), NO salto a 12 en 2028. | Contraste con el Transitorio Cuarto del decreto oficial descargado; la síntesis previa era imprecisa. |
| D-10 | 2026-07-07 | Se adopta el sistema de proceso del agent-playbook: CLAUDE.md (kernel), STATUS, DECISIONES, BITACORA + protocolo de loops por fase con checklist y gate. | Pedido por JP: verificación del estado de cada fase y proceso completo versionado en GitHub. |
| D-11 | 2026-07-07 | Modo batch autorizado por JP: los loops de fase 1+2 corren de corrido SIN el gate individual de visto bueno; JP revisa las specs en bloque al volver. La fase 3 (abogado) no cambia. Las specs batch se marcan 🟡 "revisión de JP pendiente" — nunca "aprobada". | JP se ausenta ~30 min y pidió completar la librería. El marcado 🟡 conserva la trazabilidad de qué pasó por su gate y qué no. |
| D-12 | 2026-07-07 | `teletrabajo` v1 se construye solo con el capítulo de la LFT (fuente verificada en sesión); la NOM-037-STPS queda registrada como fuente PENDIENTE con un loop dedicado posterior. | La NOM es un documento extenso y separado; transcribirla a la carrera contradice la regla de cero errores. Cobertura parcial honesta > cobertura total dudosa. |
| D-13 | 2026-07-07 | La R5 de `registro-jornada` se ancla al Art. 804 LFT (fracc. III y último párrafo, verificado contra la consolidada p. 340): conservación "durante el último año y un año después de que se extinga la relación laboral". Se agregó nota de precisión en sus reglas; el detalle vive en `conservacion-y-prueba`. | La regla decía "mín. 12 meses" sin fuente exacta; la investigación de la nueva skill encontró el ancla estatutaria y un plazo post-extinción que faltaba. Mismo mecanismo que la corrección del calendario (D-09): precisión verificada, no cambio de fondo. |
