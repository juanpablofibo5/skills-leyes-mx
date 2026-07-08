# STATUS — estado vivo del repo

**Actualizado:** 2026-07-08

## Ahora mismo

- **Batch aprobado:** JP revisó y aprobó en bloque las 5 specs del modo
  batch (D-14). Las 9 skills de P1+P2 están construidas y con specs
  aprobadas; todas `en-verificacion` esperando la fase 3.
- **Sin loop abierto.** El plan vigente es la **Ruta a v1.0** (ver
  BACKLOG.md): infraestructura de calidad → completar contenido (NOM-037,
  decisión P3) → blindaje pre-abogado → fase 3 y tag v1.0.0.

## Estado por skill

| Skill | Fase | Gate pendiente |
|-------|------|----------------|
| `registro-jornada` | ✅ 2 completada | Fase 3 (abogado) |
| `jornada-laboral` | ✅ 2 completada | Fase 3 (abogado) |
| `horas-extra` | ✅ 2 completada | Fase 3 (abogado) |
| `dias-de-descanso` | ✅ 2 completada | Fase 3 (abogado) |
| `dias-festivos` | ✅ 2 completada | Fase 3 (abogado) |
| `vacaciones` | ✅ 2 completada | Fase 3 (abogado) |
| `teletrabajo` | ✅ 2 completada (v1 solo LFT) | NOM-037 → v2 (D-12) + fase 3 |
| `conservacion-y-prueba` | ✅ 2 completada | Fase 3 (abogado) |
| `asistencia-y-faltas` | ✅ 2 completada | Fase 3 (abogado) |

Todas las specs: aprobadas por JP (4 con gate individual, 5 en bloque el
2026-07-08, D-14).

## Decisiones abiertas de JP

1. **P3:** ¿entran `trabajo-de-menores` y `lactancia-y-descansos-especiales`
   al catálogo antes de la fase 3?
2. **Mecanismo de consumo** desde el repo principal de Klokk (recomendación:
   tags de release; v1.0.0 = verificada por abogado).

## Fuentes oficiales ya localizadas (descargadas 2026-07-07)

- LFT consolidada ("Última Reforma DOF 14-05-2026") —
  https://www.diputados.gob.mx/LeyesBiblio/pdf/LFT.pdf
  · Rescisión/faltas: pp. 15–16 · Jornada: pp. 21–22 · Descansos: p. 23 ·
  Festivos: pp. 23–24 · Vacaciones: p. 24 · Obligaciones trabajadores:
  p. 39 · Teletrabajo: pp. 95–97 · Carga de la prueba: p. 335 ·
  Conservación: p. 340
- Decreto reducción de jornada, DOF 1-may-2026 vespertina —
  https://www.diputados.gob.mx/LeyesBiblio/ref/lft/LFT_ref52_01may26.pdf
  · Transitorios: pp. 3–4
- NOM-037-STPS: **PENDIENTE de descarga y transcripción** (D-12, etapa 2 de
  la Ruta a v1.0).
