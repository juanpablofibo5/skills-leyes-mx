# Spec: skill `asistencia-y-faltas`

> 🟡 **CONSTRUIDA EN MODO BATCH (D-11) — 2026-07-07.** PENDIENTE: revisión de
> JP en bloque contra el PDF oficial, y fase 3 con abogado. Citas transcritas
> por Claude del PDF oficial descargado el 2026-07-07.

## 1. Resumen ejecutivo

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

## 2. Fuente legal — texto exacto verificado

| Doc | Qué es | URL | Uso |
|-----|--------|-----|-----|
| D1 | LFT consolidada vigente, Cámara de Diputados — "Última Reforma DOF 14-05-2026" | https://www.diputados.gob.mx/LeyesBiblio/pdf/LFT.pdf | Arts. 46 y 47 (pp. 15–16), 134 y 135 (p. 39) |

| ID | Artículo | Última reforma anotada en la consolidada |
|----|----------|------------------------------------------|
| F-01 | Art. 46 | Sin anotación de reforma |
| F-02 | Art. 47, fracción X | Sin anotación de reforma en la fracción |
| F-03 | Art. 47, párrafos finales (aviso de rescisión) | Párrafos reformados/adicionados DOF 04-01-1980, 30-11-2012, 01-05-2019 |
| F-04 | Art. 134, fracción V | Sin anotación de reforma en la fracción |
| F-05 | Art. 135, fracción II | Sin anotación de reforma en la fracción |

**F-01 — Art. 46 (D1, p. 15):**

> "El trabajador o el patrón podrá rescindir en cualquier tiempo la relación
> de trabajo, por causa justificada, sin incurrir en responsabilidad."

**F-02 — Art. 47, fracción X (D1, p. 15):**

> "Son causas de rescisión de la relación de trabajo, sin responsabilidad
> para el patrón: [...]
> X. Tener el trabajador más de tres faltas de asistencia en un período de
> treinta días, sin permiso del patrón o sin causa justificada;"

**F-03 — Art. 47, párrafos finales (D1, p. 16):**

> "El patrón que despida a un trabajador deberá darle aviso escrito en el que
> refiera claramente la conducta o conductas que motivan la rescisión y la
> fecha o fechas en que se cometieron.
> El aviso deberá entregarse personalmente al trabajador en el momento mismo
> del despido o bien, comunicarlo al Tribunal competente, dentro de los cinco
> días hábiles siguientes, en cuyo caso deberá proporcionar el último
> domicilio que tenga registrado del trabajador a fin de que la autoridad se
> lo notifique en forma personal.
> La prescripción para ejercer las acciones derivadas del despido no
> comenzará a correr sino hasta que el trabajador reciba personalmente el
> aviso de rescisión.
> La falta de aviso al trabajador personalmente o por conducto del Tribunal,
> por sí sola presumirá la separación no justificada, salvo prueba en
> contrario que acredite que el despido fue justificado."

**F-04 — Art. 134, fracción V (D1, p. 39):**

> "Son obligaciones de los trabajadores: [...]
> V.- Dar aviso inmediato al patrón, salvo caso fortuito o de fuerza mayor,
> de las causas justificadas que le impidan concurrir a su trabajo;"

**F-05 — Art. 135, fracción II (D1, p. 39):**

> "Queda prohibido a los trabajadores: [...]
> II. Faltar al trabajo sin causa justificada o sin permiso del patrón;"

## 3. Capa interpretativa

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

## 4. Reglas derivadas

| ID | Regla | Riesgo | Estado | Fuente |
|----|-------|--------|--------|--------|
| RD-01 | Toda ausencia se clasifica como justificada (permiso del patrón o causa justificada, con evidencia y fecha del aviso del trabajador) o injustificada. Sin clasificación, el registro no sirve para la causal ni para el 784-III. | Crítico | FIRME | F-02, F-04, F-05 |
| RD-02 | Contador de la causal: MÁS de tres faltas injustificadas (la 4ª) en un período de 30 días habilita rescisión sin responsabilidad. El sistema alerta en la 3ª y marca la 4ª. La naturaleza de la ventana (días naturales/laborables, móvil/fija) → CL-01. | Crítico | FIRME* | F-02; ver CL-01 |
| RD-03 | Flujo de permisos con registro: quién autorizó, cuándo, y el aviso del trabajador (134-V) con su fecha. Permisos verbales sin registro dejan la ausencia en ambigüedad probatoria. | Alto | FIRME | F-04, F-05 |
| RD-04 | Soporte del despido por faltas: el sistema debe poder producir las fechas exactas de las faltas injustificadas del periodo, aptas para el aviso escrito del 47 (sin aviso → presunción de separación injustificada). | Alto | FIRME | F-03 |
| RD-05 | Etiquetado exportable de ausencias por tipo (injustificada / permiso / causa justificada / vacaciones / incapacidad) para su uso probatorio (784-III, 804-III). | Alto | FIRME* | F-02, F-04; interpretación operativa de la correlación probatoria |
| RD-06 | Retardos: se registran como hechos, pero el sistema NO debe convertirlos automáticamente en "faltas" sin una regla pactada en el reglamento interior — la LFT no los regula como falta. | Medio | FIRME* | Interpretación operativa; ver CL-02 |

\* FIRME por interpretación operativa: la obligación existe en el texto, pero
su aplicación exacta tiene una pregunta abierta registrada abajo.

### 4.1 Casos límite y preguntas abiertas

| ID | Caso o pregunta | Por qué es ambiguo | Estado | Quién resuelve |
|----|-----------------|--------------------|--------|----------------|
| CL-01 | La ventana de "un período de treinta días" del 47-X: ¿días naturales o laborables? ¿ventana móvil o periodos fijos? | El texto no lo define; cambia qué secuencias de faltas activan la causal. | abierta | abogado laboralista |
| CL-02 | ¿Pueden los retardos acumulados pactarse como falta en el reglamento interior, y con qué límites? | La LFT leída no regula retardos; es materia de reglamento interior y criterios. | abierta | abogado laboralista |
| CL-03 | ¿Qué evidencia basta para "causa justificada" (incapacidades, caso fortuito del 134-V) y quién la califica? | El texto exige la causa pero no define el estándar probatorio del trabajador. | abierta | abogado laboralista |
| CL-04 | ¿Qué constituye "faltar" en teletrabajo (sin centro de trabajo físico): no conectarse, no fichar, no entregar? | Cruce del 47-X con el capítulo de teletrabajo; sin definición legal. | abierta | abogado laboralista + decisión de producto |

## 5. Instrucciones de auditoría (cuerpo del SKILL.md)

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
7. **Generar el reporte** con el formato de la sección 6, anotando CL-04 si
   hay teletrabajadores.

### 5.1 Árbol de decisión de severidad

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

**Checklist de consistencia:** RD-01/02 = Crítico ✓ · RD-03/04/05 = Alto ✓ ·
RD-06 = Medio ✓ · casos alineados ✓.

## 6. Formato de salida

La plantilla de reporte de la librería, con encabezado:
`AUDITORÍA DE COMPLIANCE — Asistencia y faltas (Arts. 46–47, 134–135 LFT)` y
una sección adicional fija: `VENTANA DE CÓMPUTO AUDITADA: [método de la
ventana de 30 días usado por el sistema] — pendiente CL-01`.

## 7. Límites de la skill

- No decide despidos ni valida causales distintas de la fracc. X: produce el
  soporte documental y las alertas.
- Los efectos de vacaciones e incapacidades como ausencias justificadas se
  detallan en sus skills; aquí solo su etiquetado.
- No resuelve los CL abiertos: los reporta como INFORMATIVO.
- No es asesoría legal formal; lo declara en cada salida.
- Se revisa cuando el abogado resuelva CL-01–CL-04 o si se reforma el 47.

## 8. Estructura de archivos

```
skills/asistencia-y-faltas/
  SKILL.md                 <- frontmatter + secciones 3, 5, 6, 7 de esta spec
  references/
    texto-legal.md         <- sección 2 (F-01 a F-05, con doc y página)
    reglas.md              <- sección 4 (RD-01 a RD-06 + CL-01 a CL-04)
  assets/
    (sin plantilla propia: reutiliza la plantilla de reporte de la librería)
```

### 8.1 Frontmatter del SKILL.md

```yaml
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
```

## 9. Casos de prueba

| # | Entrada | Debe detectar | Severidad esperada |
|---|---------|---------------|--------------------|
| 1 | Trabajador con 4 faltas injustificadas en 30 días y el sistema nunca alertó | Falla RD-02: la causal se activó sin detección (alerta debida en la 3ª, marca en la 4ª); anotar CL-01 | CRÍTICO |
| 2 | El sistema registra "ausente" sin distinguir permiso, causa justificada o injustificada | Falla RD-01: sin clasificación no hay causal defendible ni prueba del 784-III | CRÍTICO |
| 3 | Permisos otorgados de palabra; el registro no guarda quién autorizó ni cuándo | Falla RD-03: ausencias en ambigüedad probatoria | ALTO |
| 4 | No se pueden exportar las fechas exactas de las faltas de un trabajador para el aviso de rescisión | Falla RD-04: el aviso del 47 exige conducta y fechas; sin ellas, presunción de separación injustificada | ALTO |
| 5 | El sistema convierte 3 retardos en 1 falta automáticamente, sin regla pactada en el reglamento | Falla RD-06; anotar CL-02 | MEDIO |
| 6 | Sistema con clasificación completa, contador en la 4ª con alerta en la 3ª (ventana declarada), permisos registrados, fechas exportables y retardos sin conversión automática | Ninguna falla firme; INFORMATIVO por CL abiertos | CUMPLE |

## 10. Kickoff prompt (para la fase 2)

> Construye la skill `asistencia-y-faltas` en el repo klokk-skills-leyes a
> partir de `specs/asistencia-y-faltas-spec.md`. Estructura EXACTA de la
> sección 8; solo contenido de la spec. Corre los 6 casos y reporta. Cierra
> el loop según CLAUDE.md.

---

## Estado del research

Citas de los Arts. 46, 47 (fracc. X y párrafos del aviso), 134 fracc. V y
135 fracc. II transcritas por Claude el 2026-07-07 directamente del PDF
oficial de la LFT consolidada (D1, pp. 15–16 y 39). No se citaron criterios
de memoria; los retardos se trataron como no regulados por las fuentes
leídas (CL-02), no se inventó su régimen.

**Pendiente para la revisión en bloque de JP:** contrastar F-01 a F-05 contra
las pp. 15–16 y 39 del PDF oficial.
**Pendiente para el abogado (fase 3):** CL-01 a CL-04 — CL-01 (ventana de 30
días) define la lógica del contador, la alerta más importante de la skill.
