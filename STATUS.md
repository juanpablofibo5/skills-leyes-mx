# STATUS — estado vivo del repo

**Actualizado:** 2026-07-08

## Ahora mismo

- **Loop NOM-037 fase 1 CERRADO (2026-07-08) — gate ABIERTO:** la
  NOM-037-STPS-2023 se descargó del DOF (D3 PDF ed. vespertina + D4 HTML,
  SHA-256 en FUENTES.md) y la spec BORRADOR para subir `teletrabajo` a v2
  está en `specs/teletrabajo-v2-nom037-spec.md` (F-08–F-19, RD-07 redefinida
  + RD-08–RD-12, CL-03 resuelta + CL-05–CL-07 nuevos, 7 casos). **Gate:
  visto bueno de JP** → después, fase 2 (construcción de la skill v2).
- **Etapa 1 de la Ruta a v1.0 COMPLETADA (2026-07-08):** CI de validación
  activo en cada push (`tools/validar.py` + Action `validacion`, D-17) y
  plantilla v2 publicada. Las 9 skills pasan el validador en verde.
- **Auditoría de transcripción CERRADA (M-08, 2026-07-08):** ~45 citas F-xx
  de las 9 skills contra D1/D2, 0 discrepancias (detalle en BITACORA).
- Revisión integral hecha: hallazgos M-01 a M-08 marcados en BACKLOG
  ("Hallazgos de la revisión integral"). Divergencia de formato solo en
  `registro-jornada` (M-01, pre-convención).
- Siguiente al disparar: fase 2 de teletrabajo v2 (tras el gate) y los dos
  loops P3 (D-15).

## Estado por skill

| Skill | Fase | Gate pendiente |
|-------|------|----------------|
| `registro-jornada` | ✅ 2 completada | Fase 3 (abogado) |
| `jornada-laboral` | ✅ 2 completada | Fase 3 (abogado) |
| `horas-extra` | ✅ 2 completada | Fase 3 (abogado) |
| `dias-de-descanso` | ✅ 2 completada | Fase 3 (abogado) |
| `dias-festivos` | ✅ 2 completada | Fase 3 (abogado) |
| `vacaciones` | ✅ 2 completada | Fase 3 (abogado) |
| `teletrabajo` | ✅ 2 completada (v1 solo LFT); spec v2 NOM-037 lista | Visto bueno de JP a la spec v2 → fase 2 → fase 3 |
| `conservacion-y-prueba` | ✅ 2 completada | Fase 3 (abogado) |
| `asistencia-y-faltas` | ✅ 2 completada | Fase 3 (abogado) |

Todas las specs: aprobadas por JP (4 con gate individual, 5 en bloque el
2026-07-08, D-14).

## Decisiones recientes (2026-07-08)

- **P3 entra completo (D-15):** `trabajo-de-menores` y
  `lactancia-y-descansos-especiales` se construyen en la etapa 2 — el
  catálogo final pre-abogado es de **11 skills**.
- **Consumo (D-16):** decisión diferida con dueño — Luis la resuelve al
  integrar la librería en el repo principal.
- **Siguiente loop al disparar:** Etapa 1 de la Ruta a v1.0 (CI de
  validación + plantilla v2).

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
