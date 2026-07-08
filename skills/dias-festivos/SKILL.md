---
name: dias-festivos
description: Genera y audita el calendario de días de descanso obligatorio de la LFT mexicana (fijos, lunes móviles, sexenal y electoral) y el pago doble del festivo laborado además del salario del descanso. Usar al configurar calendarios laborales, auditar pagos de festivos o clasificar jornadas en días de descanso obligatorio.
metadata:
  version: "1.0.0"
  owner: "Juan Pablo"
  reviewed_at: "2026-07-07"
  ley: "LFT Arts. 74-75"
  fuente: "LFT consolidada (última reforma DOF 2026-05-14), pp. 23-24"
---

# Skill: dias-festivos

**Qué hace:** genera el calendario de días de descanso obligatorio del año
(fijos, de lunes móvil, sexenal y electoral), audita que los festivos
laborados se paguen con salario doble además del salario del descanso
obligatorio, y que la designación de quién trabaja en festivo quede
registrada.

**Por qué importa:** los festivos de lunes móvil (febrero, marzo, noviembre)
son un error clásico de configuración — un sistema que celebra el 5 de
febrero en fecha fija aplica mal el descanso y el pago de ese día para todos
los trabajadores. Y el festivo laborado sin pago doble es incumplimiento
directo, por trabajador.

**Cuándo se activa:** al configurar o auditar calendarios laborales, validar
el pago de festivos trabajados, o clasificar jornadas registradas en días de
descanso obligatorio.

**Frontera con `dias-de-descanso`:** aquella cubre el descanso SEMANAL
(Arts. 69–73); ésta cubre los descansos OBLIGATORIOS del calendario
(Arts. 74–75). Cuando un festivo coincide con domingo o con el descanso
semanal del trabajador, los regímenes se traslapan → CL-01 y CL-02.

## Archivos de referencia

- [references/texto-legal.md](references/texto-legal.md) — texto oficial
  verificado: Arts. 74–75 (F-01, F-02), con documento y página.
- [references/reglas.md](references/reglas.md) — las 5 reglas derivadas
  (RD-01 a RD-05) y los 4 casos límite (CL-01 a CL-04).
- Plantilla del reporte: se reutiliza la de la librería —
  [../registro-jornada/assets/plantilla-reporte.md](../registro-jornada/assets/plantilla-reporte.md).

## Capa interpretativa

Sin criterios jurisprudenciales citados de memoria. Lecturas operativas del
propio texto:

- **Tres tipos de festivo (F-01):** de fecha fija (I, IV, V, VIII), de lunes
  móvil (II, III, VI — se celebran el lunes, no la fecha conmemorada),
  sexenal (VII — solo el año de transmisión del Ejecutivo) y electoral (IX —
  depende de las leyes electorales, fuente externa a la LFT).
- **El festivo trabajado se paga doble ADEMÁS del salario del descanso
  (F-02)** — misma estructura de dos conceptos separados que el Art. 73 del
  descanso semanal.
- **Trabajar en festivo es por convenio (F-02):** requiere determinación
  previa de quiénes prestan servicios; el sistema debe poder registrarla.

## Procedimiento de auditoría

1. **Generar o validar el calendario del año auditado** con RD-01 (fijos +
   lunes móviles computados + sexenal si aplica + electoral si hay fuente),
   anotando CL-03/CL-04 para las fracciones IX y VII.
2. **Cruzar las jornadas registradas contra el calendario:** toda jornada en
   festivo se marca (RD-04).
3. **Verificar la asignación pactada** de quienes trabajan el festivo
   (RD-03).
4. **Verificar el pago:** salario doble por el servicio + salario del
   descanso obligatorio como conceptos separados (RD-02).
5. **Detectar traslapes** festivo-domingo (anotar CL-01) y festivo-descanso
   semanal (anotar CL-02); reportarlos como preguntas abiertas, no como
   hallazgos firmes.
6. **Generar el reporte** con el formato de la sección siguiente.

## Árbol de decisión de severidad

```
Para cada regla que FALLA:

  ¿Calendario mal generado o festivo trabajado sin pago doble? (RD-01, RD-02)
     SÍ  -> CRÍTICO  (aplica mal el día a TODOS los trabajadores / dinero directo)
     NO  -> siguiente pregunta

  ¿Festivos laborados sin etiquetar para nómina? (RD-04)
     SÍ  -> ALTO
     NO  -> siguiente pregunta

  ¿Asignación sin registrar o fuente externa sin declarar? (RD-03, RD-05)
     SÍ  -> MEDIO

  CL-01 a CL-04 y lo pendiente -> INFORMATIVO
```

## Formato de salida

La plantilla de reporte de la librería
([../registro-jornada/assets/plantilla-reporte.md](../registro-jornada/assets/plantilla-reporte.md)),
con encabezado:

```
AUDITORÍA DE COMPLIANCE — Días de descanso obligatorio (Arts. 74–75 LFT)
```

y una sección adicional fija:

```
CALENDARIO DEL AÑO AUDITADO: [festivos computados con su fracción de origen]
```

## Límites de la skill

- No cubre el descanso semanal ni la prima dominical — eso es de
  `dias-de-descanso`.
- No calcula montos de nómina: marca, clasifica y verifica conceptos.
- No determina la fecha electoral ni los años de transmisión: exige que el
  sistema declare su fuente (RD-05) y lo reporta.
- No resuelve los CL abiertos: los reporta como INFORMATIVO.
- No es asesoría legal formal; lo declara en cada salida.
- Se revisa si se reforma el Art. 74 (nuevas fracciones) o cuando el abogado
  resuelva CL-01–CL-04.

## Estado del contenido

Citas de los Arts. 74–75 transcritas el 2026-07-07 directamente del PDF
oficial de la LFT consolidada (diputados.gob.mx, portada: "Última Reforma DOF
14-05-2026"), pp. 23–24; la fracc. VII refleja la reforma DOF 30-09-2024.
Spec de origen: `specs/dias-festivos-spec.md`, construida en modo batch
(D-11) y **aprobada en bloque por JP el 2026-07-08 (D-14)**.

**Pendiente para el abogado (fase 3):** CL-01 a CL-04 — en especial los
concursos de pago doble (CL-01, CL-02). Cuando se resuelvan, esta skill se
revisa y sube su `version` y `reviewed_at`.
