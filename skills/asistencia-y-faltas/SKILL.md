---
name: asistencia-y-faltas
description: Audita la clasificación de ausencias de la LFT mexicana (justificada/injustificada), el contador de la causal de rescisión por más de 3 faltas en 30 días (Art. 47 fracc. X), el registro de permisos y avisos, y el soporte documental del despido por faltas. Usar al configurar alertas de faltas, auditar flujos de permisos o preparar soporte de rescisión.
metadata:
  version: "1.0.0"
  owner: "Juan Pablo"
  reviewed_at: "2026-07-07"
  ley: "LFT Arts. 46, 47 (fracc. X y aviso), 134 fracc. V, 135 fracc. II"
  fuente: "LFT consolidada (última reforma DOF 2026-05-14), pp. 15-16 y 39"
---

# Skill: asistencia-y-faltas

**Qué hace:** audita la clasificación de ausencias (justificada /
injustificada), el contador de la causal de rescisión por faltas (más de 3
injustificadas en 30 días, Art. 47 fracc. X), el registro de permisos y
avisos del trabajador, y el soporte documental que un despido por faltas
exigiría (aviso de rescisión con fechas exactas).

**Por qué importa:** las faltas son la causal de rescisión más común en
PyMEs y la fracción III del Art. 784 pone su prueba a cargo del patrón. Un
checador que no distingue falta injustificada de permiso, o que no puede
producir las fechas exactas, deja al cliente sin defensa — o rescindiendo
sin causa válida.

**Cuándo se activa:** al clasificar ausencias, configurar alertas de faltas
acumuladas, auditar flujos de permisos, o preparar el soporte de una
rescisión por inasistencias.

**Frontera:** los efectos de las vacaciones (ausencia justificada) son de
`vacaciones`; la conservación/exhibición del registro es de
`conservacion-y-prueba`; el "faltar" en remoto cruza con `teletrabajo`.

## Archivos de referencia

- [references/texto-legal.md](references/texto-legal.md) — texto oficial
  verificado: Arts. 46, 47 (fracc. X y aviso), 134-V y 135-II (F-01 a F-05).
- [references/reglas.md](references/reglas.md) — las 6 reglas derivadas
  (RD-01 a RD-06) y los 4 casos límite (CL-01 a CL-04).
- Plantilla del reporte: se reutiliza la de la librería —
  [../registro-jornada/assets/plantilla-reporte.md](../registro-jornada/assets/plantilla-reporte.md).

## Capa interpretativa

Sin criterios citados de memoria. Lecturas operativas del texto:

- **La falta injustificada tiene dos escapes (F-02, F-05):** permiso del
  patrón O causa justificada. El sistema debe modelar ambos con evidencia y
  fecha — sin ese dato, ninguna falta es defendible (784-III pone su prueba
  a cargo del patrón).
- **"MÁS de tres faltas" = a partir de la cuarta (F-02):** tres faltas
  injustificadas en 30 días NO habilitan la rescisión; la cuarta sí. El
  contador y sus alertas deben reflejar exactamente eso.
- **El despido por faltas vive o muere por las fechas (F-03):** el aviso debe
  referir "la fecha o fechas" exactas; el sistema debe poder producirlas.
- **Los retardos no existen en este catálogo:** la LFT leída regula faltas,
  no retardos; su efecto es materia del reglamento interior → CL-02.

## Procedimiento de auditoría

1. **Auditar la clasificación de ausencias** (RD-01): tipos disponibles,
   evidencia y fechas; detectar ausencias sin clasificar.
2. **Auditar el contador del 47-X** (RD-02): umbral en la 4ª falta
   injustificada dentro de 30 días, alerta en la 3ª; verificar la ventana
   usada y anotar CL-01.
3. **Auditar el flujo de permisos y avisos** (RD-03): registro de quién
   autorizó y del aviso del trabajador (134-V).
4. **Probar el soporte de rescisión** (RD-04): exportar las fechas exactas de
   las faltas de un trabajador en un periodo dado.
5. **Verificar el etiquetado exportable** por tipo de ausencia (RD-05).
6. **Auditar el manejo de retardos** (RD-06): sin conversión automática a
   falta salvo regla pactada; anotar CL-02.
7. **Generar el reporte** con el formato de la sección siguiente, anotando
   CL-04 si hay teletrabajadores.

## Árbol de decisión de severidad

```
Para cada regla que FALLA:

  ¿Ausencias sin clasificar o contador de la causal mal calibrado?
  (RD-01, RD-02)
     SÍ  -> CRÍTICO  (rescisiones inválidas o faltas indefendibles)
     NO  -> siguiente pregunta

  ¿Permisos sin registro, sin soporte de fechas, o sin etiquetas?
  (RD-03, RD-04, RD-05)
     SÍ  -> ALTO
     NO  -> siguiente pregunta

  ¿Retardos convertidos en faltas sin regla pactada? (RD-06)
     SÍ  -> MEDIO

  CL-01 a CL-04 y lo pendiente -> INFORMATIVO
```

## Formato de salida

La plantilla de reporte de la librería
([../registro-jornada/assets/plantilla-reporte.md](../registro-jornada/assets/plantilla-reporte.md)),
con encabezado:

```
AUDITORÍA DE COMPLIANCE — Asistencia y faltas (Arts. 46–47, 134–135 LFT)
```

y una sección adicional fija:

```
VENTANA DE CÓMPUTO AUDITADA: [método de la ventana de 30 días usado por el sistema] — pendiente CL-01
```

## Límites de la skill

- No decide despidos ni valida causales distintas de la fracc. X: produce el
  soporte documental y las alertas.
- Los efectos de vacaciones e incapacidades como ausencias justificadas se
  detallan en sus skills; aquí solo su etiquetado.
- No resuelve los CL abiertos: los reporta como INFORMATIVO.
- No es asesoría legal formal; lo declara en cada salida.
- Se revisa cuando el abogado resuelva CL-01–CL-04 o si se reforma el 47.

## Estado del contenido

Citas de los Arts. 46, 47 (fracc. X y párrafos del aviso), 134 fracc. V y
135 fracc. II transcritas el 2026-07-07 directamente del PDF oficial de la
LFT consolidada (diputados.gob.mx, "Última Reforma DOF 14-05-2026"),
pp. 15–16 y 39. Los retardos se trataron como no regulados por las fuentes
leídas (CL-02) — no se inventó su régimen. Spec de origen:
`specs/asistencia-y-faltas-spec.md`, construida en modo batch (D-11) y
**aprobada en bloque por JP el 2026-07-08 (D-14)**.

**Pendiente para el abogado (fase 3):** CL-01 a CL-04 — CL-01 (ventana de 30
días) define la lógica del contador, la alerta más importante de la skill.
