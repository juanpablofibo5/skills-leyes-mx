---
name: conservacion-y-prueba
description: Audita la columna probatoria de la LFT mexicana; qué documentos conservar y exhibir en juicio (Art. 804, incluidos controles de asistencia y sus plazos), qué hechos debe poder probar el patrón (Art. 784) y la presunción en contra si no exhibe (Art. 805). Usar al revisar políticas de retención y purga, exportación para juicio o cobertura probatoria del registro.
metadata:
  version: "1.0.0"
  owner: "Juan Pablo"
  reviewed_at: "2026-07-07"
  ley: "LFT Arts. 784, 804 y 805"
  fuente: "LFT consolidada (última reforma DOF 2026-05-14), pp. 335 y 340"
---

# Skill: conservacion-y-prueba

**Qué hace:** audita que el sistema conserve y pueda exhibir los documentos
que la ley obliga al patrón a presentar en juicio (contratos, nómina,
controles de asistencia, comprobantes de vacaciones y primas), con los plazos
legales de retención, y que el registro cubra los hechos cuya carga de la
prueba recae en el patrón.

**Por qué importa:** es la columna probatoria de toda la librería. Si el
patrón no exhibe estos documentos, se presumen ciertos los hechos que alegue
el trabajador (Arts. 784 y 805) — el registro perfecto que no se puede
exhibir a tiempo vale lo mismo que no tener registro.

**Cuándo se activa:** al auditar políticas de retención y purga de datos,
capacidad de exportación para juicio o inspección, o la cobertura probatoria
del registro (¿qué hechos puede probar el sistema?).

**Frontera:** el CÓMO registrar es de `registro-jornada`; aquí vive el
CONSERVAR, EXHIBIR y QUÉ HECHOS probar.

## Archivos de referencia

- [references/texto-legal.md](references/texto-legal.md) — texto oficial
  verificado: Arts. 784, 804 y 805 (F-01 a F-03), con documento y página.
- [references/reglas.md](references/reglas.md) — las 5 reglas derivadas
  (RD-01 a RD-05) y los 4 casos límite (CL-01 a CL-04).
- Plantilla del reporte: se reutiliza la de la librería —
  [../registro-jornada/assets/plantilla-reporte.md](../registro-jornada/assets/plantilla-reporte.md).

## Capa interpretativa

Sin criterios citados de memoria. Lecturas operativas del texto:

- **El catálogo probatorio de F-01 es el mapa de cobertura de Klokk:** de las
  14 fracciones del 784, el registro de asistencia alimenta directamente III
  (faltas), VIII (jornada ordinaria y extraordinaria), IX (descansos y
  obligatorios), X (vacaciones) y XI (primas). Es la justificación
  estatutaria de la correlación horas-pagos (R9 de registro-jornada).
- **El hallazgo 784-VIII:** la fracción habla de jornada extraordinaria
  "cuando ésta no exceda de nueve horas semanales" y su última reforma es de
  2019 — el decreto del 2026-05-01 NO la actualizó, aunque los topes de
  horas extra suben gradualmente a 12. La asimetría es CL-02.
- **Los plazos del 804 son el piso de retención de Klokk:** controles de
  asistencia (fracc. III): "durante el último año y un año después de que se
  extinga la relación laboral". Lectura operativa segura para un SaaS:
  conservar TODO el histórico mientras dure la relación + 1 año tras la
  extinción (el "último año" es lo mínimo exigible en cualquier momento;
  purgar antes es riesgo directo) → detalle en CL-01.

## Procedimiento de auditoría

1. **Mapear la cobertura documental** del sistema contra el catálogo del 804
   (RD-01).
2. **Auditar la política de retención y purga:** ningún registro de
   asistencia purgado dentro de los plazos del 804; recomendar histórico
   completo + 1 año tras extinción (RD-02, anotar CL-01).
3. **Probar la exhibición:** exportación íntegra por trabajador y periodo,
   incluyendo extrabajadores dentro del año posterior (RD-03).
4. **Verificar la cobertura de hechos del 784:** ¿el sistema puede probar
   faltas, jornada, descansos, vacaciones y primas con datos? (RD-04, anotar
   CL-02).
5. **Verificar respaldo y redundancia documentados** (RD-05).
6. **Generar el reporte** con el formato de la sección siguiente.

## Árbol de decisión de severidad

```
Para cada regla que FALLA:

  ¿Faltan documentos del catálogo o se purga dentro del plazo legal?
  (RD-01, RD-02)
     SÍ  -> CRÍTICO  (presunción en contra: se pierde el juicio por default)
     NO  -> siguiente pregunta

  ¿No puede exhibir, no cubre los hechos del 784, o no tiene respaldo?
  (RD-03, RD-04, RD-05)
     SÍ  -> ALTO
     NO  -> siguiente pregunta

  CL-01 a CL-04 y lo pendiente -> INFORMATIVO
```

*(Esta skill no tiene reglas de riesgo MEDIO; el árbol es de dos niveles.)*

## Formato de salida

La plantilla de reporte de la librería
([../registro-jornada/assets/plantilla-reporte.md](../registro-jornada/assets/plantilla-reporte.md)),
con encabezado:

```
AUDITORÍA DE COMPLIANCE — Conservación y prueba (Arts. 784, 804 y 805 LFT)
```

y una sección adicional fija:

```
POLÍTICA DE RETENCIÓN AUDITADA: [plazos de retención y purga configurados en el sistema]
```

## Límites de la skill

- No audita el CÓMO se registra (eso es `registro-jornada`): audita
  conservación, exhibición y cobertura probatoria.
- No resuelve los CL abiertos: los reporta como INFORMATIVO.
- No es asesoría legal formal; lo declara en cada salida.
- Se revisa si se reforman los Arts. 784/804/805 (en particular si una
  reforma armoniza 784-VIII con los topes 2026) o cuando el abogado resuelva
  CL-01–CL-04.

## Estado del contenido

Citas de los Arts. 784, 804 y 805 transcritas el 2026-07-07 directamente del
PDF oficial de la LFT consolidada (diputados.gob.mx, "Última Reforma DOF
14-05-2026"), pp. 335 y 340. Hallazgos de esta investigación: (1) el 804-III
da ancla estatutaria exacta a la R5 de `registro-jornada`; (2) el 784-VIII
conserva "nueve horas semanales" sin armonizar con los topes 2026 → CL-02.
Spec de origen: `specs/conservacion-y-prueba-spec.md`, **construida en modo
batch (D-11): revisión de JP pendiente en bloque**.

**Pendiente para el abogado (fase 3):** CL-01 a CL-04 — CL-02 y CL-03 son
del máximo interés para Klokk (carga de la prueba del extraordinario y
estatus probatorio del registro electrónico).
