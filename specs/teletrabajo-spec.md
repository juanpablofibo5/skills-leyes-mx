# Spec: skill `teletrabajo`

> 🟡 **CONSTRUIDA EN MODO BATCH (D-11) — 2026-07-07.** PENDIENTE: revisión de
> JP en bloque y fase 3 con abogado. **Alcance v1 (D-12): solo el capítulo de
> la LFT; la NOM-037-STPS queda como fuente PENDIENTE con loop dedicado.**

## 1. Resumen ejecutivo

**Qué hace:** determina quién es teletrabajador (umbral legal del 40 % del
tiempo), y audita que el sistema registre su jornada con los mismos límites
que a presenciales, respete el derecho a la desconexión, supervise de forma
proporcional a la intimidad, y registre modalidad, reversibilidad e insumos.

**Por qué importa:** la regla R6 de `registro-jornada` exige registrar
teletrabajadores con los mismos estándares; esta skill define QUIÉN es
teletrabajador y QUÉ obligaciones especiales genera para un checador — el
punto ciego típico de las PyMEs híbridas.

**Cuándo se activa:** al clasificar trabajadores híbridos o remotos, auditar
el registro de jornada remota, configurar alertas de desconexión o revisar
mecanismos de supervisión a distancia.

**Frontera:** los límites de jornada son de `jornada-laboral`; el registro
electrónico es de `registro-jornada`. Aquí vive lo ESPECIAL del teletrabajo.

## 2. Fuente legal — texto exacto verificado

| Doc | Qué es | URL | Uso |
|-----|--------|-----|-----|
| D1 | LFT consolidada vigente, Cámara de Diputados — "Última Reforma DOF 14-05-2026" | https://www.diputados.gob.mx/LeyesBiblio/pdf/LFT.pdf | Capítulo XII Bis "Teletrabajo", Arts. 330-A a 330-K (pp. 95–97 del PDF) |

Todos los artículos del capítulo: "Artículo adicionado DOF 11-01-2021"
(Capítulo adicionado DOF 11-01-2021). Se citan los relevantes para un
sistema de asistencia; el capítulo completo vive en D1 pp. 95–97.

**F-01 — Art. 330-A, párrafos primero, cuarto y quinto (D1, p. 95):**

> "El teletrabajo es una forma de organización laboral subordinada que
> consiste en el desempeño de actividades remuneradas, en lugares distintos
> al establecimiento o establecimientos del patrón, por lo que no se requiere
> la presencia física de la persona trabajadora bajo la modalidad de
> teletrabajo, en el centro de trabajo, utilizando primordialmente las
> tecnologías de la información y comunicación, para el contacto y mando
> entre la persona trabajadora bajo la modalidad de teletrabajo y el patrón.
> [...]
> Se regirán por las disposiciones del presente Capítulo las relaciones
> laborales que se desarrollen más del cuarenta por ciento del tiempo en el
> domicilio de la persona trabajadora bajo la modalidad de teletrabajo, o en
> el domicilio elegido por ésta.
> No será considerado teletrabajo aquel que se realice de forma ocasional o
> esporádica."

**F-02 — Art. 330-B, fracción VI (D1, p. 95):**

> "VI. Los mecanismos de contacto y supervisión entre las partes, así como la
> duración y distribución de horarios, siempre que no excedan los máximos
> legales, y"

**F-03 — Art. 330-E, fracciones IV y VI (D1, p. 96):**

> "IV. Llevar registro de los insumos entregados a las personas trabajadoras
> bajo la modalidad de teletrabajo, en cumplimiento a las disposiciones en
> materia de seguridad y salud en el trabajo establecidas por la Secretaría
> del Trabajo y Previsión Social;
> [...]
> VI. Respetar el derecho a la desconexión de las personas trabajadoras en la
> modalidad de teletrabajo al término de la jornada laboral;"

**F-04 — Art. 330-G (D1, p. 97):**

> "El cambio en la modalidad de presencial a teletrabajo, deberá ser
> voluntario y establecido por escrito conforme al presente Capítulo, salvo
> casos de fuerza mayor debidamente acreditada.
> En todo caso, cuando se dé un cambio a la modalidad de teletrabajo las
> partes tendrán el derecho de reversibilidad a la modalidad presencial, para
> lo cual podrán pactar los mecanismos, procesos y tiempos necesarios para
> hacer válida su voluntad de retorno a dicha modalidad."

**F-05 — Art. 330-I (D1, p. 97):**

> "Los mecanismos, sistemas operativos y cualquier tecnología utilizada para
> supervisar el teletrabajo deberán ser proporcionales a su objetivo,
> garantizando el derecho a la intimidad de las personas trabajadoras bajo la
> modalidad de teletrabajo, y respetando el marco jurídico aplicable en
> materia de protección de datos personales.
> Solamente podrán utilizarse cámaras de video y micrófonos para supervisar
> el teletrabajo de manera extraordinaria, o cuando la naturaleza de las
> funciones desempeñadas por la persona trabajadora bajo la modalidad de
> teletrabajo lo requiera."

**F-06 — Art. 330-J (D1, p. 97):**

> "Las condiciones especiales de seguridad y salud para los trabajos
> desarrollados al amparo del presente Capítulo serán establecidas por la
> Secretaría del Trabajo y Previsión Social en una Norma Oficial Mexicana,
> misma que deberá considerar a los factores ergonómicos, psicosociales, y
> otros riesgos que pudieran causar efectos adversos para la vida, integridad
> física o salud de las personas trabajadoras que se desempeñen en la
> modalidad de teletrabajo."

**F-07 — Art. 330-K, fracción II (D1, p. 97):**

> "II. Vigilar que los salarios no sean inferiores a los que se paguen en la
> empresa al trabajador presencial con funciones iguales o similares;"

## 3. Capa interpretativa

Sin criterios citados de memoria. Lecturas operativas del texto:

- **El umbral del 40 % define el régimen (F-01):** más del 40 % del tiempo en
  el domicilio → aplican las obligaciones especiales del capítulo. El texto
  no define la ventana de medición → CL-01.
- **El teletrabajo NO relaja la jornada (F-02):** los horarios pactados no
  pueden exceder los máximos legales — los límites de `jornada-laboral` y el
  registro del Art. 132 Fr. XXXIV aplican íntegros (coherente con R6 de
  registro-jornada).
- **La NOM del 330-J existe como mandato** — su contenido (NOM-037-STPS) se
  transcribirá en un loop dedicado (D-12); hasta entonces sus requisitos
  específicos son PENDIENTE en esta skill.

## 4. Reglas derivadas

| ID | Regla | Riesgo | Estado | Fuente |
|----|-------|--------|--------|--------|
| RD-01 | Clasificación: si la relación se desarrolla más del 40 % del tiempo en el domicilio del trabajador (o el que eligió), es teletrabajo y aplican las obligaciones del capítulo; lo ocasional o esporádico NO es teletrabajo. La ventana de medición del 40 % → CL-01. | Crítico | FIRME* | F-01; ver CL-01 |
| RD-02 | La jornada del teletrabajador se pacta y registra con los MISMOS máximos legales que presenciales (duración y distribución de horarios en el contrato); el checador la registra con los mismos estándares. | Crítico | FIRME | F-02 |
| RD-03 | Derecho a la desconexión al término de la jornada: el sistema debe conocer el fin de jornada de cada teletrabajador y poder detectar/alertar actividad laboral posterior. Qué constituye violación exactamente → CL-02. | Alto | FIRME* | F-03 (fracc. VI); ver CL-02 |
| RD-04 | Supervisión proporcional: los mecanismos de monitoreo (incluido el checador) deben ser proporcionales, respetar intimidad y datos personales; cámaras y micrófonos solo de manera extraordinaria o por la naturaleza de las funciones. | Alto | FIRME | F-05 |
| RD-05 | Modalidad e historial: el cambio a teletrabajo es voluntario y por escrito, con derecho de reversibilidad; el sistema debe registrar la modalidad vigente de cada trabajador y su historial de cambios. | Medio | FIRME | F-04 |
| RD-06 | Registro de insumos entregados al teletrabajador (obligación patronal): el sistema debe poder registrarlo o integrarse con quien lo haga. | Medio | FIRME | F-03 (fracc. IV) |
| RD-07 | Requisitos específicos de seguridad y salud del teletrabajo (NOM del 330-J / NOM-037-STPS): NO auditar hasta transcribir la NOM contra su texto oficial (D-12). | — | PENDIENTE | F-06; ver CL-03 |

\* FIRME por interpretación operativa: la obligación existe en el texto, pero
su aplicación exacta tiene una pregunta abierta registrada abajo.

### 4.1 Casos límite y preguntas abiertas

| ID | Caso o pregunta | Por qué es ambiguo | Estado | Quién resuelve |
|----|-----------------|--------------------|--------|----------------|
| CL-01 | ¿Sobre qué ventana se mide el "más del cuarenta por ciento del tiempo" (semana, mes, contrato)? ¿Y cómo se mide: días, horas? | El texto no define periodo ni unidad de medición. | abierta | abogado laboralista |
| CL-02 | ¿Qué constituye violación del derecho a la desconexión (mensajes, asignación de tareas, llamadas) y qué evidencia debe guardar el sistema? | La LFT enuncia el derecho sin definir su alcance operativo. | abierta | abogado laboralista |
| CL-03 | Requisitos específicos de la NOM-037-STPS (seguridad y salud en teletrabajo): pendientes de transcripción contra el texto oficial de la NOM. | Fuente aún no transcrita al repo (D-12); no se audita de memoria. | abierta | loop dedicado + abogado |
| CL-04 | Registro de jornada remota entre husos horarios distintos al del centro de trabajo. | Cross-ref: es el CL-03 de `jornada-laboral`; aplica con más frecuencia en teletrabajo. | abierta | decisión de producto + abogado |

## 5. Instrucciones de auditoría (cuerpo del SKILL.md)

1. **Clasificar la plantilla:** calcular el % de tiempo en domicilio por
   trabajador y marcar como teletrabajadores a los que superen 40 % (RD-01,
   anotar CL-01 con la ventana usada).
2. **Auditar el registro de jornada remota:** mismos estándares y máximos que
   presenciales (RD-02); si el sistema exime a remotos del checador, es falla
   inmediata.
3. **Auditar la desconexión:** fin de jornada conocido por el sistema y
   capacidad de detectar actividad posterior (RD-03, anotar CL-02).
4. **Auditar la proporcionalidad de la supervisión:** sin cámaras/micrófonos
   permanentes; minimización de datos (RD-04).
5. **Verificar modalidad e historial** (RD-05) y el registro de insumos
   (RD-06).
6. **Marcar RD-07 como PENDIENTE** (NOM-037) — nunca auditar requisitos de la
   NOM de memoria.
7. **Generar el reporte** con el formato de la sección 6.

### 5.1 Árbol de decisión de severidad

```
Para cada regla que FALLA:

  ¿Clasifica mal quién es teletrabajador o exime su jornada del registro?
  (RD-01, RD-02)
     SÍ  -> CRÍTICO
     NO  -> siguiente pregunta

  ¿Desconexión sin detección o supervisión desproporcionada? (RD-03, RD-04)
     SÍ  -> ALTO
     NO  -> siguiente pregunta

  ¿Modalidad/insumos sin registrar? (RD-05, RD-06)
     SÍ  -> MEDIO

  RD-07 (NOM-037) y CL-01 a CL-04 -> INFORMATIVO / PENDIENTE
```

**Checklist de consistencia:** RD-01/02 = Crítico ✓ · RD-03/04 = Alto ✓ ·
RD-05/06 = Medio ✓ · RD-07 = PENDIENTE/informativo ✓ · casos alineados ✓.

## 6. Formato de salida

La plantilla de reporte de la librería, con encabezado:
`AUDITORÍA DE COMPLIANCE — Teletrabajo (Arts. 330-A a 330-K LFT)` y una
sección adicional fija: `CLASIFICACIÓN APLICADA: [ventana y método usados
para medir el 40 %] — pendiente CL-01`.

## 7. Límites de la skill

- v1 SOLO cubre el capítulo de la LFT; los requisitos de la NOM-037-STPS
  están PENDIENTES (D-12) y así se reportan siempre.
- Los límites de jornada y el registro electrónico son de `jornada-laboral`
  y `registro-jornada`; aquí solo lo especial del teletrabajo.
- No resuelve los CL abiertos: los reporta como INFORMATIVO.
- No es asesoría legal formal; lo declara en cada salida.
- Se revisa al transcribir la NOM-037 (sube a v2), cuando el abogado resuelva
  CL-01–CL-04, o si se reforma el capítulo.

## 8. Estructura de archivos

```
skills/teletrabajo/
  SKILL.md                 <- frontmatter + secciones 3, 5, 6, 7 de esta spec
  references/
    texto-legal.md         <- sección 2 (F-01 a F-07, con doc y página)
    reglas.md              <- sección 4 (RD-01 a RD-07 + CL-01 a CL-04)
  assets/
    (sin plantilla propia: reutiliza la plantilla de reporte de la librería)
```

### 8.1 Frontmatter del SKILL.md

```yaml
---
name: teletrabajo
description: Clasifica teletrabajadores (umbral legal >40 % del tiempo en domicilio) y audita sus obligaciones especiales en la LFT mexicana; registro de jornada remota con los mismos máximos, derecho a la desconexión, supervisión proporcional a la intimidad, modalidad e insumos. Usar al auditar plantillas híbridas o remotas. NOM-037 pendiente (v1 solo LFT).
metadata:
  version: "1.0.0"
  owner: "Juan Pablo"
  reviewed_at: "2026-07-07"
  ley: "LFT Arts. 330-A a 330-K (Capítulo XII Bis)"
  fuente: "LFT consolidada (última reforma DOF 2026-05-14), pp. 95-97; NOM-037-STPS PENDIENTE (D-12)"
---
```

## 9. Casos de prueba

| # | Entrada | Debe detectar | Severidad esperada |
|---|---------|---------------|--------------------|
| 1 | Empleado que trabaja 3 de 5 días en casa (60 %) tratado como presencial sin obligaciones de teletrabajo | Falla RD-01: supera el 40 %, es teletrabajador; anotar CL-01 | CRÍTICO |
| 2 | Teletrabajadores eximidos del checador "porque están en casa" | Falla RD-02: mismos estándares y máximos que presenciales | CRÍTICO |
| 3 | Sistema sin fin de jornada configurado para remotos; tareas asignadas a las 23:00 sin ninguna marca | Falla RD-03: desconexión sin detección posible; anotar CL-02 | ALTO |
| 4 | Checador remoto que exige cámara encendida toda la jornada para "verificar presencia" | Falla RD-04: cámaras solo de manera extraordinaria; supervisión desproporcionada | ALTO |
| 5 | Sin registro de qué trabajadores están en modalidad teletrabajo ni de sus cambios | Falla RD-05: modalidad e historial sin registrar | MEDIO |
| 6 | Sistema que clasifica >40 %, registra jornada remota igual que presencial, marca fin de jornada, supervisa proporcionalmente y registra modalidad e insumos | Ninguna falla firme; INFORMATIVO por NOM-037 pendiente (RD-07) y CL abiertos | CUMPLE |

## 10. Kickoff prompt (para la fase 2)

> Construye la skill `teletrabajo` en el repo klokk-skills-leyes a partir de
> `specs/teletrabajo-spec.md`. Estructura EXACTA de la sección 8; solo
> contenido de la spec. Corre los 6 casos y reporta. Cierra el loop según
> CLAUDE.md.

---

## Estado del research

Citas de los Arts. 330-A, 330-B, 330-E, 330-G, 330-I, 330-J y 330-K
transcritas por Claude el 2026-07-07 directamente del PDF oficial de la LFT
consolidada (D1, pp. 95–97; capítulo adicionado DOF 11-01-2021). **La
NOM-037-STPS NO fue transcrita en este loop (D-12):** sus requisitos son
PENDIENTE (RD-07/CL-03) y la skill lo declara en cada salida. No se citaron
criterios de memoria.

**Pendiente para la revisión en bloque de JP:** contrastar F-01 a F-07 contra
las pp. 95–97 del PDF oficial.
**Pendiente para el abogado (fase 3):** CL-01 (ventana del 40 %), CL-02
(alcance de la desconexión). **Pendiente de loop dedicado:** NOM-037 → v2.
