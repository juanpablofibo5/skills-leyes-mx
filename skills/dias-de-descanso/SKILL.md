---
name: dias-de-descanso
description: Audita el descanso semanal de la LFT mexicana; al menos un día pagado por cada seis trabajados, prima dominical (+25 %), pago doble del descanso trabajado y proporcionales de semana incompleta. Usar al auditar patrones de descanso, detectar rachas de trabajo continuo o revisar pagos de domingos y descansos laborados.
metadata:
  version: "1.0.0"
  owner: "Juan Pablo"
  reviewed_at: "2026-07-07"
  ley: "LFT Arts. 69-73"
  fuente: "LFT consolidada (última reforma DOF 2026-05-14), Capítulo III, p. 23"
---

# Skill: dias-de-descanso

**Qué hace:** audita el descanso semanal: que exista al menos un día de
descanso pagado por cada seis trabajados, que los domingos laborados generen
prima dominical (+25 %), que los descansos trabajados se paguen doble además
del salario del descanso, y que las semanas incompletas acrediten su parte
proporcional.

**Por qué importa:** para un checador, las rachas de días trabajados sin
descanso y los descansos trabajados sin pago correcto son de los
incumplimientos más frecuentes y más caros de una PyME — y los más fáciles
de detectar con un registro de asistencia bien llevado. Es dinero directo
(prima 25 %, pago doble) y exposición en juicio.

**Cuándo se activa:** al auditar patrones de descanso semanal, detectar
rachas de trabajo continuo, calcular prima dominical, o revisar el pago de
descansos trabajados.

**Frontera con `dias-festivos`:** esta skill cubre el descanso SEMANAL
(Arts. 69–73). Los días de descanso obligatorio del calendario (Arts. 74–75:
festivos y su pago) son de la skill `dias-festivos`.

## Archivos de referencia

Cargar según lo que pida la auditoría:

- [references/texto-legal.md](references/texto-legal.md) — texto oficial
  verificado: Arts. 69–73 (F-01 a F-05), con documento y página de cada cita.
- [references/reglas.md](references/reglas.md) — las 6 reglas derivadas
  (RD-01 a RD-06) con riesgo y estado, y los 4 casos límite abiertos
  (CL-01 a CL-04).
- Plantilla del reporte: se reutiliza la de la librería —
  [../registro-jornada/assets/plantilla-reporte.md](../registro-jornada/assets/plantilla-reporte.md).

## Capa interpretativa

Sin criterios jurisprudenciales citados de memoria; si el abogado (fase 3)
aporta criterios sobre descanso semanal o prima dominical, se agregan con su
fuente. Lecturas operativas desde el propio texto:

- **El piso legal es 1 descanso por cada 6 trabajados (F-01).** "Por lo
  menos" admite más días de descanso (con la transición a 40 horas muchas
  empresas operarán semanas de 5 días); la skill audita el PISO legal, no la
  política interna de la empresa.
- **La prima dominical es por laborar en domingo (F-03).** El texto vigente
  dice "las personas que laboren en domingo" — la marca debe ponerse en toda
  jornada dominical; cómo se acumula con el pago doble del descanso trabajado
  queda abierto (CL-02).
- **El descanso trabajado se paga doble ADEMÁS del salario del descanso
  (F-05).** El sistema debe distinguir el salario del día de descanso (que ya
  se debe) del doble por el servicio prestado — son conceptos separados en el
  texto.

## Procedimiento de auditoría

1. **Cargar el patrón de descansos** pactado por trabajador (RD-02); si el
   sistema no lo registra, es hallazgo inmediato (no se puede auditar F-05
   sin saber qué día es descanso).
2. **Barrer rachas de días trabajados** consecutivos; alertar 7 o más sin
   descanso (RD-01), anotando CL-01 sobre el método de cómputo.
3. **Marcar domingos laborados** → prima +25 % para nómina (RD-03); si el
   domingo era además el descanso del trabajador, aplicar también el paso 4 y
   anotar CL-02.
4. **Detectar descansos trabajados** → verificar pago doble además del
   salario del descanso, como conceptos separados (RD-04).
5. **Calcular proporcionales** de semana incompleta o multi-patrón (RD-05),
   anotando CL-03 si el salario es variable.
6. **Auditar el etiquetado exportable** de domingos y descansos trabajados
   (RD-06).
7. **Generar el reporte** con el formato de la sección siguiente, marcando
   los CL abiertos que apliquen (incluido CL-04 si la empresa opera semana
   de 5 días).

## Árbol de decisión de severidad

```
Para cada regla que FALLA:

  ¿Deja rachas sin descanso o descansos trabajados sin detectar/pagar?
  (RD-01, RD-04)
     SÍ  -> CRÍTICO  (incumplimiento directo y caro, por trabajador)
     NO  -> siguiente pregunta

  ¿Deja dinero dominical sin marcar o sin exportar? (RD-03, RD-06)
     SÍ  -> ALTO  (nómina incompleta; correlación horas-pagos rota)
     NO  -> siguiente pregunta

  ¿Es registro de patrón de descansos o proporcionales incompletos?
  (RD-02, RD-05)
     SÍ  -> MEDIO

  CL-01 a CL-04 y lo pendiente de autoridad -> INFORMATIVO
```

## Formato de salida

La plantilla de reporte de la librería
([../registro-jornada/assets/plantilla-reporte.md](../registro-jornada/assets/plantilla-reporte.md)),
con encabezado:

```
AUDITORÍA DE COMPLIANCE — Días de descanso (Arts. 69–73 LFT)
```

y una sección adicional fija:

```
PATRÓN DE DESCANSOS AUDITADO: [día(s) de descanso pactados por trabajador o grupo]
```

## Límites de la skill

- No cubre los días de descanso obligatorio del calendario (festivos,
  Arts. 74–75) — eso es de `dias-festivos`.
- No calcula montos de nómina: marca, clasifica y verifica conceptos; el
  cálculo monetario es del sistema de nómina.
- No resuelve los CL abiertos: los reporta como INFORMATIVO.
- No es asesoría legal formal; lo declara en cada salida.
- Se revisa cuando el abogado resuelva CL-01–CL-04 o si la transición a 40
  horas genera criterios o reglamentos nuevos sobre el descanso semanal.

## Estado del contenido

Citas de los Arts. 69–73 transcritas el 2026-07-07 directamente del PDF
oficial de la LFT consolidada (diputados.gob.mx, portada: "Última Reforma DOF
14-05-2026"), p. 23 — Capítulo III "Días de descanso". Los Arts. 74–75 se
excluyeron deliberadamente: pertenecen a `dias-festivos`. No se citaron
criterios jurisprudenciales de memoria. Spec de origen:
`specs/dias-de-descanso-spec.md`, aprobada por JP el 2026-07-07.

**Pendiente para el abogado (fase 3):** CL-01 a CL-04 y las reglas FIRME* —
en especial CL-01 (método de cómputo de rachas) y CL-04 (naturaleza del
segundo día libre en semanas de 5 días). Cuando se resuelvan, esta skill se
revisa y sube su `version` y `reviewed_at`.
