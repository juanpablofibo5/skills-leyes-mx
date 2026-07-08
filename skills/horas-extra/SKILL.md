---
name: horas-extra
description: Clasifica el tiempo extraordinario de la LFT mexicana en su régimen correcto (+100 % dentro del tope, +200 % el excedente, pago ordinario por siniestro), valida los topes semanales por año (9/9/10/11/12 en 2026–2030), la distribución 4h×4 días y el techo de 12 horas diarias. Usar al calcular o auditar horas extra, configurar topes o revisar módulos de tiempo extraordinario.
metadata:
  version: "1.0.0"
  owner: "Juan Pablo"
  reviewed_at: "2026-07-07"
  ley: "LFT Arts. 65-68; Transitorios Primero y Cuarto del decreto DOF 2026-05-01"
  fuente: "LFT consolidada (última reforma DOF 2026-05-14) + decreto DOF 2026-05-01"
---

# Skill: horas-extra

**Qué hace:** clasifica cada hora trabajada más allá de la jornada ordinaria
en su régimen legal correcto (extraordinaria dentro del tope +100 %,
excedente del tope +200 %, o trabajo por siniestro con pago ordinario),
valida los topes semanales del año (calendario 9/9/10/11/12) y la
distribución permitida, y audita que un sistema los aplique bien.

**Por qué importa:** las horas extra son el cálculo más sensible en dinero de
un checador — el pago cambia de +0 % a +100 % o +200 % según la
clasificación. Un tope mal configurado o un porcentaje mal aplicado se
traduce directo en nómina incorrecta y en pérdida de defensa en juicio
(la correlación horas-pagos es la regla R9 de `registro-jornada`).

**Cuándo se activa:** al clasificar tiempo extraordinario, calcular
porcentajes de pago de horas extra, configurar topes semanales, o auditar el
módulo de horas extra de un sistema de asistencia o nómina.

**Frontera con `jornada-laboral`:** aquella define CUÁNDO el tiempo deja de
ser ordinario (sus límites diario/semanal, RD-05 de esa skill); ésta define
qué pasa con ese tiempo DESPUÉS: régimen, topes y porcentajes. Comparten el
techo absoluto de 12 horas diarias (Art. 68, párrafo tercero).

## Archivos de referencia

Cargar según lo que pida el cálculo o la auditoría:

- [references/texto-legal.md](references/texto-legal.md) — texto oficial
  verificado: Arts. 65–68 (F-01 a F-04) y Transitorios Primero y Cuarto
  (F-05, F-06), con documento y página de cada cita.
- [references/reglas.md](references/reglas.md) — las 8 reglas derivadas
  (RD-01 a RD-08) con riesgo y estado, y los 4 casos límite abiertos
  (CL-01 a CL-04).
- Plantilla del reporte: se reutiliza la de la librería —
  [../registro-jornada/assets/plantilla-reporte.md](../registro-jornada/assets/plantilla-reporte.md).

## Capa interpretativa

Sin criterios nuevos citados de memoria. Dos referencias ya existentes en la
librería (origen: deep research verificado de JP, en
[criterios-tribunales.md](../registro-jornada/references/criterios-tribunales.md)
de `registro-jornada`):

- **Carga de la prueba y presunción:** si el patrón no puede probar la
  jornada, el tribunal presume ciertos los hechos del trabajador "hasta 9
  horas extra semanales" (criterio de la Segunda Sala de la SCJN, citado en
  esa referencia). Con los topes nuevos del Transitorio Cuarto, si esa
  presunción se ajusta al tope del año es pregunta abierta → CL-04.
- **Correlación horas-pagos (R9 de registro-jornada):** las horas extra
  registradas deben explicar los pagos de nómina; por eso esta skill exige
  que cada hora quede etiquetada con su régimen (RD-08).

Lectura operativa que fundamenta reglas: la ley distingue DOS regímenes de
prolongación con pagos distintos — el extraordinario común (F-02: +100 %,
con tope y distribución) y el trabajo por siniestro/riesgo inminente
(F-01 + F-03: pago ordinario, "tiempo estrictamente indispensable", sin
tope numérico propio). Un sistema que los mezcla paga mal o audita mal.

## Procedimiento de auditoría y clasificación

1. **Recibir los candidatos a extraordinario** desde `jornada-laboral`
   (excedentes de límites diario/semanal ordinarios) — RD-01.
2. **Determinar el año auditado** y cargar el tope semanal vigente (RD-02).
3. **Separar el trabajo por siniestro** (RD-07): si el registro está marcado
   como siniestro/riesgo inminente, su régimen es pago ordinario y tiempo
   estrictamente indispensable; auditarlo aparte y no contarlo contra el tope
   del extraordinario común sin resolver antes su clasificación.
4. **Clasificar cada hora extraordinaria común:** dentro del tope semanal del
   año → régimen +100 % (RD-04); por encima del tope → excedente, máximo 4
   horas por semana, régimen +200 % (RD-05), anotando CL-03.
5. **Validar la distribución** del extraordinario: hasta 4 h/día y máximo 4
   días por semana (RD-03), anotando CL-02 en años de transición.
6. **Verificar el techo absoluto** de 12 horas por día sumando ordinaria +
   extraordinaria (RD-06).
7. **Auditar el etiquetado por régimen** y su exportabilidad para nómina
   (RD-08).
8. **Generar el reporte** con el formato de la sección siguiente, marcando
   los CL abiertos que apliquen.

## Árbol de decisión de severidad

```
Para cada regla que FALLA:

  ¿Corrompe el tope del año o el porcentaje de pago base? (RD-02, RD-04)
     SÍ  -> CRÍTICO  (nómina incorrecta en dinero, por cada trabajador)
     NO  -> siguiente pregunta

  ¿Clasifica mal regímenes, distribución o techos? (RD-01, RD-03, RD-05, RD-06, RD-08)
     SÍ  -> ALTO  (horas mal etiquetadas o excesos sin detectar)
     NO  -> siguiente pregunta

  ¿Es un régimen especial mal registrado? (RD-07)
     SÍ  -> MEDIO

  CL-01 a CL-04 y lo pendiente de autoridad -> INFORMATIVO
```

## Formato de salida

La plantilla de reporte de la librería
([../registro-jornada/assets/plantilla-reporte.md](../registro-jornada/assets/plantilla-reporte.md)),
con encabezado:

```
AUDITORÍA DE COMPLIANCE — Tiempo extraordinario (Arts. 65–68 LFT)
```

y una sección adicional fija:

```
TOPES APLICADOS ESTE AÑO: [tope semanal del año + distribución vigente]
```

## Límites de la skill

- No calcula montos de nómina: clasifica horas y valida porcentajes y topes;
  el cálculo monetario (salario base, integraciones) es del sistema de
  nómina.
- No redefine cuándo el tiempo deja de ser ordinario — eso es de
  `jornada-laboral`.
- No resuelve los CL abiertos: los reporta como INFORMATIVO.
- No es asesoría legal formal; lo declara en cada salida.
- Se revisa cuando cambie el año de calendario (tope nuevo), cuando el
  abogado resuelva CL-01–CL-04, o si la STPS publica disposiciones que
  toquen el registro del tiempo extraordinario.

## Estado del contenido

Citas de los Arts. 65–68 transcritas el 2026-07-07 del PDF oficial de la LFT
consolidada (diputados.gob.mx, portada: "Última Reforma DOF 14-05-2026"),
p. 22, y Transitorios Primero y Cuarto del decreto oficial
(`LFT_ref52_01may26.pdf`, DOF 1-may-2026 edición vespertina), pp. 3–4. Los
textos del decreto y de la consolidada coinciden entre sí en los artículos
reformados. La capa interpretativa solo referencia criterios ya presentes en
la librería; no se citaron criterios nuevos de memoria. Spec de origen:
`specs/horas-extra-spec.md`, aprobada por JP el 2026-07-07.

**Pendiente para el abogado (fase 3):** CL-01 a CL-04 y las reglas FIRME* —
en especial CL-03 (base del tope de +4h en transición), que impacta dinero.
Cuando el abogado los resuelva o cambie el año de calendario, esta skill se
revisa y sube su `version` y `reviewed_at`.
