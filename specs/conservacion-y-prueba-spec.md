# Spec: skill `conservacion-y-prueba`

> 🟡 **CONSTRUIDA EN MODO BATCH (D-11) — 2026-07-07.** PENDIENTE: revisión de
> JP en bloque contra el PDF oficial, y fase 3 con abogado. Citas transcritas
> por Claude del PDF oficial descargado el 2026-07-07.

## 1. Resumen ejecutivo

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

## 2. Fuente legal — texto exacto verificado

| Doc | Qué es | URL | Uso |
|-----|--------|-----|-----|
| D1 | LFT consolidada vigente, Cámara de Diputados — "Última Reforma DOF 14-05-2026" | https://www.diputados.gob.mx/LeyesBiblio/pdf/LFT.pdf | Arts. 784 (p. 335), 804 y 805 (p. 340) |

| ID | Artículo | Última reforma anotada en la consolidada |
|----|----------|------------------------------------------|
| F-01 | Art. 784 | Artículo reformado DOF 04-01-1980, 30-11-2012, 01-05-2019 (párrafo primero reformado 01-05-2019) |
| F-02 | Art. 804 | Artículo reformado DOF 04-01-1980; párrafo final y fracc. IV reformados DOF 30-11-2012 |
| F-03 | Art. 805 | Artículo reformado DOF 04-01-1980 |

**F-01 — Art. 784 (D1, p. 335):**

> "El Tribunal eximirá de la carga de la prueba al trabajador, cuando por
> otros medios esté en posibilidad de llegar al conocimiento de los hechos, y
> para tal efecto a petición del trabajador o de considerarlo necesario
> requerirá al patrón para que exhiba los documentos que, de acuerdo con las
> leyes, tiene la obligación legal de conservar en la empresa, bajo el
> apercibimiento de que, de no presentarlos, se presumirán ciertos los hechos
> alegados por el trabajador. En todo caso, corresponderá al patrón probar su
> dicho cuando exista controversia sobre:
> I. Fecha de ingreso del trabajador;
> II. Antigüedad del trabajador;
> III. Faltas de asistencia del trabajador;
> IV. Causa de rescisión de la relación de trabajo;
> V. Terminación de la relación o contrato de trabajo para obra o tiempo
> determinado, en los términos de los artículos 37, fracción I, y 53,
> fracción III, de esta Ley;
> VI. Constancia de haber dado por escrito al trabajador o al Tribunal de la
> fecha y la causa del despido.
> La negativa lisa y llana del despido, no revierte la carga de la prueba.
> Asimismo, la negativa del despido y el ofrecimiento del empleo hecho al
> trabajador, no exime al patrón de probar su dicho;
> VII. El contrato de trabajo;
> VIII. Jornada de trabajo ordinaria y extraordinaria, cuando ésta no exceda
> de nueve horas semanales;
> IX. Pagos de días de descanso y obligatorios, así como del aguinaldo;
> X. Disfrute y pago de las vacaciones;
> XI. Pago de las primas dominical, vacacional y de antigüedad;
> XII. Monto y pago del salario;
> XIII. Pago de la participación de los trabajadores en las utilidades de las
> empresas; y
> XIV. Incorporación y aportaciones al Instituto Mexicano del Seguro Social;
> al Fondo Nacional de la Vivienda y al Sistema de Ahorro para el Retiro.
> La pérdida o destrucción de los documentos señalados en este artículo, por
> caso fortuito o fuerza mayor, no releva al patrón de probar su dicho por
> otros medios."

**F-02 — Art. 804 (D1, p. 340):**

> "El patrón tiene obligación de conservar y exhibir en juicio los documentos
> que a continuación se precisan:
> I. Contratos individuales de trabajo que se celebren, cuando no exista
> contrato colectivo o contrato Ley aplicable;
> II. Listas de raya o nómina de personal, cuando se lleven en el centro de
> trabajo; o recibos de pagos de salarios;
> III. Controles de asistencia, cuando se lleven en el centro de trabajo;
> IV. Comprobantes de pago de participación de utilidades, de vacaciones y de
> aguinaldos, así como las primas a que se refiere esta Ley, y pagos,
> aportaciones y cuotas de seguridad social; y
> V. Los demás que señalen las leyes.
> Los documentos señalados en la fracción I deberán conservarse mientras dure
> la relación laboral y hasta un año después; los señalados en las fracciones
> II, III y IV, durante el último año y un año después de que se extinga la
> relación laboral; y los mencionados en la fracción V, conforme lo señalen
> las Leyes que los rijan."

**F-03 — Art. 805 (D1, p. 340):**

> "El incumplimiento a lo dispuesto por el artículo anterior, establecerá la
> presunción de ser ciertos los hechos que el actor exprese en su demanda, en
> relación con tales documentos, salvo la prueba en contrario."

## 3. Capa interpretativa

Sin criterios citados de memoria. Lecturas operativas del texto:

- **El catálogo probatorio de F-01 es el mapa de cobertura de Klokk:** de las
  14 fracciones, el registro de asistencia alimenta directamente III
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

## 4. Reglas derivadas

| ID | Regla | Riesgo | Estado | Fuente |
|----|-------|--------|--------|--------|
| RD-01 | El sistema debe cubrir el catálogo de documentos del 804 que le competen: controles de asistencia (III) como núcleo, y soporte exportable que alimente II y IV (horas que explican pagos de salarios, vacaciones y primas). | Crítico | FIRME | F-02 |
| RD-02 | Plazos de retención (804, último párrafo): contratos (I) mientras dure la relación + 1 año después; nómina, asistencia y comprobantes (II–IV) durante el último año + 1 año tras la extinción de la relación. El sistema NO debe purgar registros de asistencia dentro de esos plazos; lectura operativa segura: todo el histórico de la relación + 1 año → CL-01. | Crítico | FIRME* | F-02; ver CL-01 |
| RD-03 | Exhibición bajo demanda: no presentar los documentos → se presumen ciertos los hechos del trabajador (784 pfo. primero y 805). El sistema debe poder exportar los documentos íntegros por trabajador y periodo en tiempo de juicio o inspección. | Alto | FIRME | F-01, F-03 |
| RD-04 | Cobertura de hechos del 784: el registro debe poder probar al menos las fracciones III (faltas), VIII (jornada ordinaria y extraordinaria), IX (descansos y obligatorios), X (vacaciones) y XI (primas) — con datos, no con dichos. La asimetría de VIII con los topes 2026 → CL-02. | Alto | FIRME | F-01; ver CL-02 |
| RD-05 | Pérdida o destrucción por caso fortuito no releva de probar por otros medios (784, último párrafo): el sistema debe tener respaldo y redundancia documentados de los registros. | Alto | FIRME* | F-01; regla técnica derivada |

\* FIRME por interpretación operativa: la obligación existe en el texto, pero
su aplicación exacta tiene una pregunta abierta registrada abajo.

### 4.1 Casos límite y preguntas abiertas

| ID | Caso o pregunta | Por qué es ambiguo | Estado | Quién resuelve |
|----|-----------------|--------------------|--------|----------------|
| CL-01 | ¿"Durante el último año" (804) permite purgar registros de asistencia de más de 12 meses con relación activa, o el piso práctico es todo el histórico? | El texto fija el mínimo exigible; purgar el histórico anterior es legal-mente discutible y probatoriamente riesgoso. | abierta | abogado laboralista |
| CL-02 | 784-VIII pone la carga de la prueba del patrón sobre la jornada extraordinaria "cuando ésta no exceda de nueve horas semanales", pero los topes 2026–2030 suben a 10/11/12. ¿Cómo queda la carga de la prueba entre 9 y el tope del año? | La fracción no fue actualizada por el decreto DOF 2026-05-01 (última reforma: 2019). | abierta | abogado laboralista |
| CL-03 | 804-III dice "controles de asistencia, cuando se lleven en el centro de trabajo" (texto de 1980); el 132-XXXIV hace obligatorio el registro electrónico desde 2026. ¿El registro electrónico queda comprendido en 804-III y sus plazos? | El 804 no fue reformado en 2026; la integración de ambos regímenes no está escrita. | abierta | abogado laboralista |
| CL-04 | Interacción entre la presunción del 805 y la "prueba plena" del registro electrónico acordado (132-XXXIV, párrafo tercero). | Dos reglas probatorias nuevas y viejas sin articulación expresa. | abierta | abogado laboralista |

## 5. Instrucciones de auditoría (cuerpo del SKILL.md)

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
6. **Generar el reporte** con el formato de la sección 6.

### 5.1 Árbol de decisión de severidad

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

**Checklist de consistencia:** RD-01/02 = Crítico ✓ · RD-03/04/05 = Alto ✓ ·
(sin nivel MEDIO en esta skill: no hay reglas de ese riesgo) · casos
alineados ✓.

## 6. Formato de salida

La plantilla de reporte de la librería, con encabezado:
`AUDITORÍA DE COMPLIANCE — Conservación y prueba (Arts. 784, 804 y 805 LFT)`
y una sección adicional fija: `POLÍTICA DE RETENCIÓN AUDITADA: [plazos de
retención y purga configurados en el sistema]`.

## 7. Límites de la skill

- No audita el CÓMO se registra (eso es `registro-jornada`): audita
  conservación, exhibición y cobertura probatoria.
- No resuelve los CL abiertos: los reporta como INFORMATIVO.
- No es asesoría legal formal; lo declara en cada salida.
- Se revisa si se reforman los Arts. 784/804/805 (en particular si una
  reforma armoniza 784-VIII con los topes 2026) o cuando el abogado resuelva
  CL-01–CL-04.

## 8. Estructura de archivos

```
skills/conservacion-y-prueba/
  SKILL.md                 <- frontmatter + secciones 3, 5, 6, 7 de esta spec
  references/
    texto-legal.md         <- sección 2 (F-01 a F-03, con doc y página)
    reglas.md              <- sección 4 (RD-01 a RD-05 + CL-01 a CL-04)
  assets/
    (sin plantilla propia: reutiliza la plantilla de reporte de la librería)
```

### 8.1 Frontmatter del SKILL.md

```yaml
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
```

## 9. Casos de prueba

| # | Entrada | Debe detectar | Severidad esperada |
|---|---------|---------------|--------------------|
| 1 | Sistema que purga automáticamente registros de asistencia a los 90 días (relación activa) | Falla RD-02: dentro del plazo del 804; anotar CL-01 | CRÍTICO |
| 2 | No existe exportación de controles de asistencia — solo dashboards en pantalla | Falla RD-01/RD-03: no hay documento exhibible del catálogo del 804 | CRÍTICO |
| 3 | Extrabajador que salió hace 8 meses; sus registros ya no son exportables | Falla RD-03: dentro del año posterior a la extinción debe poder exhibirse | ALTO |
| 4 | El registro no distingue faltas justificadas/injustificadas ni marca descansos trabajados | Falla RD-04: no puede probar las fracciones III y IX del 784 con datos | ALTO |
| 5 | Sin política de respaldo documentada; una base de datos única | Falla RD-05: la pérdida fortuita no releva de probar por otros medios | ALTO |
| 6 | Sistema con retención de histórico completo + 1 año, exportación íntegra (incluidos extrabajadores), cobertura de hechos del 784 y respaldos documentados | Ninguna falla firme; INFORMATIVO por CL abiertos (incluida la asimetría 784-VIII) | CUMPLE |

## 10. Kickoff prompt (para la fase 2)

> Construye la skill `conservacion-y-prueba` en el repo klokk-skills-leyes a
> partir de `specs/conservacion-y-prueba-spec.md`. Estructura EXACTA de la
> sección 8; solo contenido de la spec. Corre los 6 casos y reporta. Cierra
> el loop según CLAUDE.md.

---

## Estado del research

Citas de los Arts. 784, 804 y 805 transcritas por Claude el 2026-07-07
directamente del PDF oficial de la LFT consolidada (D1, pp. 335 y 340). Dos
hallazgos de esta investigación: (1) el 804-III da ancla estatutaria exacta a
la regla R5 de `registro-jornada` ("durante el último año y un año después de
que se extinga la relación laboral"); (2) el 784-VIII conserva "nueve horas
semanales" sin armonizar con los topes 2026 → CL-02. No se citaron criterios
de memoria.

**Pendiente para la revisión en bloque de JP:** contrastar F-01 a F-03 contra
las pp. 335 y 340 del PDF oficial.
**Pendiente para el abogado (fase 3):** CL-01 a CL-04 — CL-02 y CL-03 son
del máximo interés para Klokk (carga de la prueba del extraordinario y
estatus probatorio del registro electrónico).
