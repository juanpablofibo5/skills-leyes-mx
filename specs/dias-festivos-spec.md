# Spec: skill `dias-festivos`

> ✅ **SPEC APROBADA.** Construida en modo batch (D-11) el 2026-07-07;
> revisada y aprobada en bloque por JP el 2026-07-08 (D-14). Pendiente:
> fase 3 con abogado laboralista.

## 1. Resumen ejecutivo

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

## 2. Fuente legal — texto exacto verificado

**Documento oficial usado (descargado el 2026-07-07):**

| Doc | Qué es | URL | Uso |
|-----|--------|-----|-----|
| D1 | LFT consolidada vigente, Cámara de Diputados — portada indica "Última Reforma DOF 14-05-2026" | https://www.diputados.gob.mx/LeyesBiblio/pdf/LFT.pdf | Texto vigente de los Arts. 74–75 (pp. 23–24 del PDF) |

### 2.1 Artículos vigentes

| ID | Artículo | Última reforma anotada en la consolidada |
|----|----------|------------------------------------------|
| F-01 | Art. 74 | Artículo reformado DOF 22-12-1987, 17-01-2006; fracción VII reformada DOF 30-09-2024 |
| F-02 | Art. 75 | Párrafo primero reformado DOF 01-05-2019 |

**F-01 — Art. 74 (D1, p. 23):**

> "Son días de descanso obligatorio:
> I. El 1o. de enero;
> II. El primer lunes de febrero en conmemoración del 5 de febrero;
> III. El tercer lunes de marzo en conmemoración del 21 de marzo;
> IV. El 1o. de mayo;
> V. El 16 de septiembre;
> VI. El tercer lunes de noviembre en conmemoración del 20 de noviembre;
> VII. El 1o. de octubre de cada seis años, cuando corresponda a la
> transmisión del Poder Ejecutivo Federal;
> VIII. El 25 de diciembre, y
> IX. El que determinen las leyes federales y locales electorales, en el caso
> de elecciones ordinarias, para efectuar la jornada electoral."

**F-02 — Art. 75 (D1, pp. 23–24):**

> "En los casos del artículo anterior los trabajadores y los patrones
> determinarán el número de trabajadores que deban prestar sus servicios. Si
> no se llega a un convenio, resolverá el Tribunal.
> Los trabajadores quedarán obligados a prestar los servicios y tendrán
> derecho a que se les pague, independientemente del salario que les
> corresponda por el descanso obligatorio, un salario doble por el servicio
> prestado."

## 3. Capa interpretativa

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

## 4. Reglas derivadas

| ID | Regla | Riesgo | Estado | Fuente |
|----|-------|--------|--------|--------|
| RD-01 | El calendario de festivos del año se genera con las reglas del Art. 74: fijos (1-ene, 1-may, 16-sep, 25-dic), lunes móviles (primer lunes de febrero, tercer lunes de marzo, tercer lunes de noviembre), sexenal (1-oct solo el año de transmisión del Ejecutivo) y electoral (jornada electoral ordinaria, según leyes electorales). Nunca fechas conmemoradas fijas para los móviles. | Crítico | FIRME | F-01 |
| RD-02 | Festivo laborado: se paga salario doble por el servicio, además del salario que ya corresponde por el descanso obligatorio — dos conceptos separados y exportables. | Crítico | FIRME | F-02 |
| RD-03 | La designación de quién trabaja en festivo se determina por convenio (o Tribunal); el sistema debe registrar la asignación pactada antes del festivo. | Medio | FIRME | F-02 |
| RD-04 | Toda jornada registrada en festivo debe quedar etiquetada de forma exportable para nómina (correlación horas-pagos, R9 de registro-jornada). | Alto | FIRME* | F-01, F-02; interpretación operativa de la correlación |
| RD-05 | Los festivos electoral (fracc. IX) y sexenal (fracc. VII) requieren una fuente de calendario externa mantenida (leyes electorales / año de transmisión); el sistema debe declarar de dónde toma esas fechas. | Medio | FIRME* | F-01; ver CL-03 y CL-04 |

\* FIRME por interpretación operativa: la obligación existe en el texto, pero
su aplicación exacta tiene una pregunta abierta registrada abajo.

### 4.1 Casos límite y preguntas abiertas

| ID | Caso o pregunta | Por qué es ambiguo | Estado | Quién resuelve |
|----|-----------------|--------------------|--------|----------------|
| CL-01 | Festivo que cae en domingo y se labora: ¿se acumulan el doble del Art. 75 y la prima dominical del Art. 71 (+25 %)? | Son regímenes distintos con supuestos traslapados; el texto no dice si se suman. | abierta | abogado laboralista |
| CL-02 | Festivo que coincide con el día de descanso SEMANAL del trabajador y se labora: ¿aplica el doble del Art. 73, el del Art. 75, o ambos? | Dos fuentes de pago doble para el mismo día; el texto no resuelve el concurso. | abierta | abogado laboralista |
| CL-03 | ¿De qué fuente oficial y con qué anticipación se toma la fecha de la jornada electoral (fracc. IX)? | Depende de leyes electorales federales y locales, externas a la LFT. | abierta | decisión de producto + abogado |
| CL-04 | Confirmación de los años de transmisión del Ejecutivo para la fracc. VII (siguiente aplicable esperado: 2030). | El texto dice "cuando corresponda a la transmisión"; el año concreto debe confirmarse contra calendario oficial, no asumirse. | abierta | abogado / fuente oficial al configurar |

## 5. Instrucciones de auditoría (cuerpo del SKILL.md)

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
6. **Generar el reporte** con el formato de la sección 6.

### 5.1 Árbol de decisión de severidad

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

**Checklist de consistencia (requisito 5 del brief):** RD-01/02 = Crítico en
tabla y árbol ✓ · RD-04 = Alto ✓ · RD-03/05 = Medio ✓ · casos alineados ✓.

## 6. Formato de salida

La plantilla de reporte de la librería, con encabezado:
`AUDITORÍA DE COMPLIANCE — Días de descanso obligatorio (Arts. 74–75 LFT)` y
una sección adicional fija: `CALENDARIO DEL AÑO AUDITADO: [festivos computados
con su fracción de origen]`.

## 7. Límites de la skill

- No cubre el descanso semanal ni la prima dominical — eso es de
  `dias-de-descanso`.
- No calcula montos de nómina: marca, clasifica y verifica conceptos.
- No determina la fecha electoral ni los años de transmisión: exige que el
  sistema declare su fuente (RD-05) y lo reporta.
- No resuelve los CL abiertos: los reporta como INFORMATIVO.
- No es asesoría legal formal; lo declara en cada salida.
- Se revisa si se reforma el Art. 74 (nuevas fracciones) o cuando el abogado
  resuelva CL-01–CL-04.

## 8. Estructura de archivos

```
skills/dias-festivos/
  SKILL.md                 <- frontmatter + secciones 3, 5, 6, 7 de esta spec
  references/
    texto-legal.md         <- sección 2 (F-01, F-02, con doc y página)
    reglas.md              <- sección 4 (RD-01 a RD-05 + CL-01 a CL-04)
  assets/
    (sin plantilla propia: reutiliza la plantilla de reporte de la librería)
```

### 8.1 Frontmatter del SKILL.md

```yaml
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
```

## 9. Casos de prueba

| # | Entrada | Debe detectar | Severidad esperada |
|---|---------|---------------|--------------------|
| 1 | Calendario configurado con el 5 de febrero y el 20 de noviembre en fecha fija | Falla RD-01: las fracc. II y VI son lunes móviles (primer lunes de febrero, tercer lunes de noviembre) | CRÍTICO |
| 2 | Festivo laborado pagado como día sencillo | Falla RD-02: salario doble por el servicio + salario del descanso, como conceptos separados | CRÍTICO |
| 3 | Jornadas registradas el 25 de diciembre sin ninguna etiqueta de festivo | Falla RD-04: festivo laborado sin marcar para nómina | ALTO |
| 4 | Sistema sin registro de quiénes fueron designados para trabajar el festivo | Falla RD-03: la asignación por convenio no está registrada | MEDIO |
| 5 | Sistema con calendario móvil correcto, pago doble separado, etiquetas, asignaciones y fuente declarada para la fracc. IX | Ninguna falla firme; solo INFORMATIVO por CL abiertos | CUMPLE |
| 6 | Festivo que cae en domingo, laborado, con doble pagado pero prima dominical sin evaluar | RD-02 cumplida; la acumulación con la prima es CL-01 → pregunta abierta, no hallazgo firme | INFORMATIVO (CL-01) |

## 10. Kickoff prompt (para la fase 2)

> Construye la skill `dias-festivos` en el repo klokk-skills-leyes a partir
> de `specs/dias-festivos-spec.md`. Sigue EXACTAMENTE la estructura de la
> sección 8. No inventes contenido legal: usa solo lo que está en la spec.
> Corre los 6 casos de prueba y reporta. Cierra el loop según CLAUDE.md.

---

## Estado del research

Citas de los Arts. 74–75 transcritas por Claude el 2026-07-07 directamente
del PDF oficial de la LFT consolidada (D1, descargado de diputados.gob.mx esa
fecha; portada: "Última Reforma DOF 14-05-2026"), pp. 23–24. La fracc. VII
refleja la reforma DOF 30-09-2024 (1 de octubre sexenal). No se citaron
criterios de memoria.

**Pendiente para la revisión en bloque de JP:** contrastar F-01 y F-02 contra
las pp. 23–24 del PDF oficial.
**Pendiente para el abogado (fase 3):** CL-01 a CL-04 — en especial los
concursos de pago doble (CL-01, CL-02), que son dinero directo.
