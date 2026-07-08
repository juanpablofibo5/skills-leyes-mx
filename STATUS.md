# STATUS — estado vivo del repo

**Actualizado:** 2026-07-08 (pivote D-18 en ejecución)

## Ahora mismo

- **PIVOTE a librería agnóstica (D-18/D-19):** skills por LEY que auditan el
  código real de cualquier repo target. R0 cerrado (repo renombrado a
  `skills-leyes-mx`, visión reescrita en README/CLAUDE.md) y R1 cerrado
  (flujo de auditoría F0–F5 publicado en
  `plantillas/flujo-auditoria-codigo.md`).
- **Gate abierto:** revisión de JP/Luis del flujo de auditoría antes de R2
  (reestructura a `skills/lft/` + módulos y `skills/nom-037-stps/`).
- **Gate en cola:** visto bueno de JP a `specs/teletrabajo-v2-nom037-spec.md`
  — su fase 2 se ejecutará DESPUÉS de R2, ya sobre la estructura nueva.
- Plan completo del pivote: BACKLOG → "Reestructura a librería agnóstica".

## Estado por skill (estructura actual, pre-R2)

| Skill | Fase | Gate pendiente |
|-------|------|----------------|
| `registro-jornada` | ✅ 2 completada | Fase 3 (abogado) · se normaliza en R2 (M-01) |
| `jornada-laboral` | ✅ 2 completada | Fase 3 (abogado) |
| `horas-extra` | ✅ 2 completada | Fase 3 (abogado) |
| `dias-de-descanso` | ✅ 2 completada | Fase 3 (abogado) |
| `dias-festivos` | ✅ 2 completada | Fase 3 (abogado) |
| `vacaciones` | ✅ 2 completada | Fase 3 (abogado) |
| `teletrabajo` | ✅ 2 completada (v1 solo LFT); spec v2 NOM-037 lista | Visto bueno de JP a la spec v2 → fase 2 (post-R2) → fase 3 |
| `conservacion-y-prueba` | ✅ 2 completada | Fase 3 (abogado) |
| `asistencia-y-faltas` | ✅ 2 completada | Fase 3 (abogado) |

En R2 estas skills se convierten en **módulos de `skills/lft/`** (la
NOM-037 en su propia skill); el contenido legal se mueve verbatim.

## Decisiones recientes (2026-07-08)

- **D-18 pivote:** librería agnóstica, skills por ley, flujo de auditoría
  sobre código real; Klokk = primer consumidor.
- **D-19 renombre:** `klokk-skills-leyes` → `skills-leyes-mx`.
- D-15 (P3 entra: menores y lactancia, serán módulos de `lft/`), D-16
  (consumo lo resuelve Luis), D-17 (CI con `verificada` bloqueada).

## Fuentes oficiales ya localizadas

- LFT consolidada ("Última Reforma DOF 14-05-2026") —
  https://www.diputados.gob.mx/LeyesBiblio/pdf/LFT.pdf
  · Rescisión/faltas: pp. 15–16 · Jornada: pp. 21–22 · Descansos: p. 23 ·
  Festivos: pp. 23–24 · Vacaciones: p. 24 · Obligaciones trabajadores:
  p. 39 · Teletrabajo: pp. 95–97 · Carga de la prueba: p. 335 ·
  Conservación: p. 340
- Decreto reducción de jornada, DOF 1-may-2026 vespertina —
  https://www.diputados.gob.mx/LeyesBiblio/ref/lft/LFT_ref52_01may26.pdf
  · Transitorios: pp. 3–4
- NOM-037-STPS-2023 (descargada 2026-07-08, D3/D4 en FUENTES.md) — DOF
  08-06-2023 ed. vespertina, la NOM en pp. 3–50 · Listado 5.1: p. 7 ·
  Política 5.2: p. 8 · Desconexión 4.11: p. 6 · Pausas/desconexión 7.3:
  p. 12 · PEC 10.3: pp. 14–25 · Conservación 10.4 y Transitorio: p. 26 ·
  Vigente desde 05-12-2023.
