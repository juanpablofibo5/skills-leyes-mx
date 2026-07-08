# Spec: skill `teletrabajo` v2 — incorporación de la NOM-037-STPS-2023

> 🔍 **BORRADOR — PENDIENTE DE VISTO BUENO DE JP.** Fase 1 del loop NOM-037
> (etapa 2 de la Ruta a v1.0; cierra D-12). Esta spec SUBE la skill
> `skills/teletrabajo/` de v1 (solo LFT) a v2 (LFT + NOM-037-STPS-2023).
> La fase 2 NO se ejecuta hasta el visto bueno. Base: la spec v1 aprobada
> (`specs/teletrabajo-spec.md`, D-14) — aquí solo se especifica lo que
> CAMBIA o se AGREGA.

## 1. Resumen ejecutivo

**Qué hace la v2:** incorpora a la skill `teletrabajo` los requisitos de la
NOM-037-STPS-2023 (Teletrabajo — Condiciones de seguridad y salud en el
trabajo, DOF 08-06-2023) que un sistema de registro de asistencia puede
verificar o alimentar con sus datos: el listado patronal de teletrabajadores
(con el % de tiempo en teletrabajo), el alcance completo del derecho a la
desconexión (que la NOM extiende a horarios no laborables, vacaciones,
permisos, licencias y pausas convenidas), las pausas y los reposos de
lactancia, la documentación del cambio de modalidad y su reversibilidad, y
la conservación de evidencias por al menos un año.

**Por qué importa:** la v1 dejó la NOM como PENDIENTE (RD-07/CL-03, D-12).
La NOM está VIGENTE desde el 05-12-2023 (Transitorio PRIMERO: 180 días
naturales tras su publicación el 08-06-2023) — toda PyME con teletrabajadores
ya es inspeccionable contra ella, y el listado del numeral 5.1 (con su campo
"tiempo en porcentaje") es exactamente el dato que un checador produce.

**Cuándo se activa:** igual que v1 (clasificar híbridos/remotos, auditar
jornada remota, desconexión y supervisión), más: al generar o auditar el
listado NOM de teletrabajadores, al configurar pausas/lactancia y al revisar
la retención de evidencias.

**Frontera:** las condiciones físicas y ergonómicas del lugar de trabajo, las
listas de verificación de SST, la capacitación anual y los exámenes médicos
son obligaciones de la NOM que NO se verifican con datos de asistencia:
quedan explícitamente fuera del alcance (sección 7), no como pendientes.

## 2. Fuente legal — texto exacto verificado

| Doc | Qué es | URL | Uso |
|-----|--------|-----|-----|
| D3 | NOM-037-STPS-2023 en el DOF, edición vespertina del 08-06-2023 (PDF oficial de la edición, 61 pp.; la NOM ocupa las pp. 3–50) | https://www.dof.gob.mx/abrirPDF.php?archivo=08062023-VES.pdf&anio=2023&repo= | Citas por página de la edición |
| D4 | NOM-037-STPS-2023, texto íntegro de la nota del DOF (HTML, nota 5691672) | https://www.dof.gob.mx/nota_detalle.php?codigo=5691672&fecha=08/06/2023 | Texto completo para verificación cruzada |

Ambos documentos se descargaron el 2026-07-08 con hash SHA-256 estable
(doble descarga idéntica); las filas D3/D4 de `FUENTES.md` anclan su
integridad. Las citas F-08 a F-19 se transcribieron de D4 y se verificaron
palabra por palabra contra las páginas de D3 (pp. 5–26 revisadas
visualmente). La NOM es texto original de 2023: no tiene reformas conocidas
(búsqueda del 2026-07-08 sin resultados de modificación en el DOF; el hash
de FUENTES.md detecta cualquier cambio futuro). Las F-01 a F-07 (LFT) de la
v1 quedan intactas.

**F-08 — Numerales 1 y 2 (D3, p. 5):**

> "1. Objetivo.
> Establecer las condiciones de seguridad y salud en el trabajo en los
> lugares de trabajo en donde las personas trabajadoras bajo la modalidad de
> Teletrabajo realicen sus actividades, a fin de prevenir accidentes y
> enfermedades, así como promover un medioambiente seguro y saludable en su
> entorno laboral.
> 2. Campo de aplicación.
> La presente Norma Oficial Mexicana rige en toda la República Mexicana y
> aplica a todos los centros de trabajo que cuenten con personas trabajadoras
> bajo la modalidad de Teletrabajo."

**F-09 — Numeral 4.11, definición de Desconexión (D3, p. 6):**

> "4.11 Desconexión: Derecho de un trabajador a apartarse del trabajo
> (incluida la desconexión de las TIC de manera digital) y abstenerse de
> participar en cualquier tipo de comunicación con el centro de trabajo al
> término de la jornada laboral, en los horarios no laborables, vacaciones,
> permisos y licencias.
> En horarios flexibles, la desconexión aplica también durante las pausas
> convenidas entre la persona trabajadora bajo la modalidad de Teletrabajo
> con el patrón y asentadas, según aplique, en el contrato colectivo de
> trabajo o reglamento interior."

**F-10 — Numeral 4.20, definición de Persona trabajadora bajo la modalidad de Teletrabajo (D3, p. 6):**

> "4.20 Persona trabajadora bajo la modalidad de Teletrabajo: Persona
> trabajadora que presta su servicio personal, remunerado y subordinado en
> lugar(es) fijo(s), distinto(s) al centro de trabajo, y utiliza las
> tecnologías de la información y la comunicación para el desempeño de sus
> labores de Teletrabajo."

Nota de lectura: esta definición y el campo de aplicación (F-08) NO repiten
el umbral de "más del cuarenta por ciento" del Art. 330-A de la LFT (F-01)
→ CL-05.

**F-11 — Numeral 5.1, listado de teletrabajadores, completo (D3, p. 7):**

> "5.1 Contar con un listado actualizado de las personas trabajadoras bajo
> la modalidad de Teletrabajo con, al menos, la información siguiente:
> a) Nombre de las personas trabajadoras bajo la modalidad de Teletrabajo;
> b) Género;
> c) Estado civil
> d) Actividades a desarrollar;
> e) Nombre y perfil de puesto;
> f) Tiempo (en porcentaje) de la relación laboral que usa para realizar
> Teletrabajo;
> g) Número telefónico de contacto;
> h) Domicilio de las personas trabajadoras bajo la modalidad de Teletrabajo;
> i) Lugares de trabajo propuestos por las personas trabajadoras bajo la
> modalidad de Teletrabajo y convenidos con el patrón;
> j) Razón social y domicilio del centro de trabajo.
> k) Listado del equipo de cómputo y ergonómico otorgado a la persona
> trabajadora.
> Nota: La confidencialidad de los datos contenidos en el listado de
> personas trabajadoras bajo la modalidad de Teletrabajo estará bajo la
> responsabilidad del patrón."

(Puntuación reproducida tal cual la edición oficial: el inciso c) no lleva
punto y coma y el j) cierra con punto.)

**F-12 — Numeral 5.2, encabezado e incisos d) y e) (D3, p. 8):**

> "5.2 Establecer, por escrito, implantar, mantener y difundir en el centro
> de trabajo y entre las personas trabajadoras bajo la modalidad de
> Teletrabajo una Política de Teletrabajo que cumpla con las disposiciones
> del contrato colectivo de trabajo o del reglamento interior de trabajo,
> según aplique, en cumplimiento a lo establecido en los artículos 330-C,
> 330-D y 330-E de la Ley Federal del Trabajo, y que:
> [...]
> d) Indique los mecanismos y reglas de contacto entre el centro de trabajo
> y las personas trabajadoras bajo la modalidad de Teletrabajo, siempre que
> se garantice el derecho a la privacidad de las personas trabajadoras bajo
> la modalidad de Teletrabajo, y que dichos mecanismos o reglas no
> interfieran en la relación trabajo-familia, y que sean proporcionales a su
> objetivo;
> e) Establezca la duración del horario de labores pactado, y/o la
> distribución convenida de los horarios de las jornadas de trabajo de
> éstas, siempre que no excedan los máximos legales y contractuales,
> incluyendo el derecho a las pausas para descanso y a la desconexión
> (incluida la desconexión de las TIC de manera digital) al término de la
> jornada laboral, en los horarios no laborables, vacaciones, permisos y
> licencias;"

**F-13 — Numeral 5.2, inciso h) (D3, p. 8):**

> "h) Determine el horario dentro de la jornada laboral en el que, durante
> un máximo de seis meses, las madres trabajadoras bajo la modalidad de
> Teletrabajo en periodo de lactancia contarán con tiempo para alimentar a
> sus hijos e hijas, pudiendo elegir entre tomar dos reposos extraordinarios
> por día, de media hora cada uno, o bien reducir una hora su jornada
> laboral, en los términos establecidos por el artículo 170 de la Ley
> Federal del Trabajo;"

**F-14 — Numeral 5.6 (D3, p. 9):**

> "5.6 Establecer y documentar, en su caso, el proceso de implementación del
> Teletrabajo para el centro de trabajo que cambie de la modalidad
> presencial a Teletrabajo y viceversa, y que al menos contemple lo
> siguiente:
> a) La manera de mantener y establecer comunicación entre la persona
> trabajadora bajo la modalidad de Teletrabajo y el centro de trabajo;
> b) Los momentos, condiciones o causas en que la persona trabajadora bajo
> la modalidad de Teletrabajo asistirá al centro de trabajo;
> c) Indicar la forma en que se supervisará el desarrollo del Teletrabajo, y
> d) Establecer la manera en que se dará mantenimiento al equipo de cómputo
> o herramientas (incluidas las TIC´s) de trabajo utilizadas y/o asignadas
> para el Teletrabajo."

**F-15 — Numeral 5.10 (D3, p. 10):**

> "5.10 Establecer mecanismos para la reversibilidad de la modalidad de
> Teletrabajo a presencial, cuando la persona trabajadora bajo la modalidad
> de Teletrabajo informe al patrón de alguna condición, o alteración de las
> condiciones de seguridad y salud en el trabajo, que justifique el regreso
> al trabajo presencial, o porque así convenga a sus intereses laborales, de
> acuerdo con lo que al respecto se hubiere asentado por escrito en
> cumplimiento con lo previsto por el artículo 330-G de la Ley."

**F-16 — Numeral 7.3, encabezado e incisos d) y e) (D3, p. 12):**

> "7.3 Para evitar riesgos de trabajo provocados por factores de riesgo
> psicosocial, según aplique:
> [...]
> d) Se cuente con pausas y tiempos de descanso adecuados para las personas
> trabajadoras bajo la modalidad de Teletrabajo, y
> e) Se respete el derecho a la desconexión (incluida la desconexión de las
> TIC de manera digital) de las personas trabajadoras bajo la modalidad de
> Teletrabajo al término de la jornada laboral, durante las pausas
> convenidas en horarios flexibles, en los horarios no laborables,
> vacaciones, permisos y licencias."

**F-17 — Numeral 10.3, tabla del PEC, fila 5.1, observaciones (D3, p. 14):**

> "El listado de las personas trabajadoras bajo la modalidad de Teletrabajo
> puede presentarse de manera impresa, o en archivos electrónicos de medios
> digitales.
> La actualización del listado de las personas trabajadoras bajo la
> modalidad de Teletrabajo se da cuando una nueva persona trabajadora se
> incorpora a esta modalidad, o cuando una de las que ya están en el listado
> deja de estarlo.
> Los nombres de las personas trabajadoras bajo la modalidad de Teletrabajo
> que se encuentren en el listado podrán ser compulsados con otros
> documentos que el patrón exhiba como, por ejemplo:
> · Listas de nómina;
> · Lista de trabajadores inscritos a la seguridad social que le corresponda
> al centro de trabajo, o
> · Lista de los trabajadores que cuenten en el contrato colectivo o
> individual de trabajo, según aplique."

**F-18 — Numeral 10.4 (D3, p. 26):**

> "10.4 Las evidencias de tipo documental o los registros a que alude esta
> Norma podrán exhibirse de manera impresa o en medios informáticos o
> digitales, y se deberán conservar al menos durante un año."

**F-19 — Transitorio PRIMERO (D3, p. 26):**

> "PRIMERO. La presente Norma Oficial Mexicana entrará a los 180 días
> naturales posteriores a su publicación en el Diario Oficial de la
> Federación."

(Sic: la edición oficial omite "en vigor". Publicación 08-06-2023 + 180 días
naturales = **en vigor desde el 05-12-2023** — cómputo aritmético del
transitorio, no cita.)

## 3. Capa interpretativa

Sin criterios citados de memoria. Lecturas operativas del texto:

- **La NOM ya no es pendiente (F-19):** vigente desde el 05-12-2023. La v2
  elimina el "PENDIENTE NOM-037" de cada salida de la v1 y lo sustituye por
  reglas auditables (RD-08 a RD-12); lo no verificable con asistencia pasa a
  "fuera de alcance" declarado, no a pendiente.
- **El listado 5.1 es dato de checador (F-11, F-17):** el campo f) — "Tiempo
  (en porcentaje) de la relación laboral que usa para realizar Teletrabajo" —
  se calcula de los registros de asistencia (dónde marca cada quien); el PEC
  admite el listado en "archivos electrónicos de medios digitales", lo
  compulsa contra nómina (la correlación que Klokk ya hace, R9 de
  registro-jornada) y define "actualizado" como reflejar altas y bajas de la
  modalidad. La ventana de medición del % sigue sin definirse (CL-01) y el
  umbral de aplicación de la NOM tampoco (CL-05).
- **La desconexión es más ancha que en la LFT (F-09, F-12 e, F-16 e):** la
  LFT la enuncia "al término de la jornada laboral" (F-03); la NOM la define
  además "en los horarios no laborables, vacaciones, permisos y licencias" y,
  en horarios flexibles, "durante las pausas convenidas". Un checador que
  solo vigile el fin de jornada cubre una fracción del derecho: debe cruzar
  actividad contra TODOS esos periodos — que son exactamente los estados de
  ausencia/descanso que ya registra (`vacaciones`, `dias-de-descanso`,
  `dias-festivos`). Qué actos constituyen violación sigue abierto (CL-02).
- **Pausas y lactancia entran a la jornada registrable (F-12 e, F-13,
  F-16 d):** la política debe incluir pausas para descanso, y la NOM
  aterriza los reposos de lactancia del Art. 170 LFT (2 reposos de media
  hora, o reducción de 1 hora, máximo 6 meses) DENTRO del horario pactado de
  teletrabajo — eventos que el sistema debe poder registrar sin contarlos
  contra la persona. "Adecuadas" no está definido (CL-07).
- **El cambio de modalidad genera papel y calendario (F-14, F-15):** proceso
  documentado presencial↔teletrabajo que incluye "los momentos, condiciones
  o causas" de asistencia al centro (5.6 b) — es decir, el patrón híbrido
  debe poder decir QUÉ días toca centro de trabajo, y el checador es quien
  evidencia si eso se cumple; refuerza RD-05 (330-G, reversibilidad).
- **Retención mínima de un año (F-18):** los registros digitales valen como
  evidencia y se conservan "al menos durante un año". Es un PISO de la NOM:
  los registros de jornada tienen plazos LFT mayores (skill
  `conservacion-y-prueba`) — aplica siempre el plazo más largo.

## 4. Reglas derivadas

La tabla completa de la skill v2. RD-01 a RD-06 vienen de la v1 aprobada
(cambios marcados con **v2:**); RD-07 se REDEFINE (era PENDIENTE); RD-08 a
RD-12 son nuevas.

| ID | Regla | Riesgo | Estado | Fuente |
|----|-------|--------|--------|--------|
| RD-01 | (v1, sin cambio de lógica) Clasificación: más del 40 % del tiempo en domicilio → teletrabajo LFT; lo ocasional/esporádico NO. Ventana de medición → CL-01. **v2:** si la NOM aplica también bajo el umbral → CL-05. | Crítico | FIRME* | F-01; ver CL-01, ver CL-05 |
| RD-02 | (v1, sin cambio) Jornada del teletrabajador con los MISMOS máximos y registro que presenciales. **v2:** la política de teletrabajo debe fijar duración/distribución del horario pactado sin exceder máximos legales Y contractuales. | Crítico | FIRME | F-02; F-12 (inciso e) |
| RD-03 | (v1, sin cambio) Desconexión al término de la jornada: fin de jornada conocido por el sistema y detección de actividad posterior. | Alto | FIRME* | F-03 (fracc. VI); ver CL-02 |
| RD-04 | (v1, sin cambio) Supervisión proporcional a la intimidad y datos personales; cámaras/micrófonos solo extraordinarios. **v2:** las reglas de contacto deben además garantizar privacidad, no interferir en la relación trabajo-familia y ser proporcionales a su objetivo. | Alto | FIRME | F-05; F-12 (inciso d) |
| RD-05 | (v1, sin cambio) Cambio a teletrabajo voluntario y por escrito, con reversibilidad; modalidad vigente e historial registrados. | Medio | FIRME | F-04 |
| RD-06 | (v1, sin cambio) Registro de insumos entregados o integración con quien lo lleve. **v2:** el listado NOM exige el "listado del equipo de cómputo y ergonómico otorgado" por persona (inciso k). | Medio | FIRME | F-03 (fracc. IV); F-11 (inciso k) |
| RD-07 | (REDEFINIDA; era PENDIENTE) La NOM-037-STPS-2023 está VIGENTE desde el 05-12-2023 (180 días naturales tras DOF 08-06-2023): la skill deja de reportarla como pendiente. Sus requisitos verificables con datos de asistencia se auditan con RD-08 a RD-12; sus obligaciones de SST física/ergonómica, capacitación y exámenes médicos se declaran fuera de alcance (sección 7), nunca se auditan de memoria. | — | FIRME | F-08, F-19 |
| RD-08 | (NUEVA) Listado de teletrabajadores: el patrón debe contar con un listado actualizado con al menos los incisos a) a k) del 5.1; es válido en archivo electrónico/digital; "actualizado" = refleja cada alta y baja de la modalidad; se compulsa contra nómina. El checador debe poder producir o alimentar sus campos operativos: quién está en modalidad, % de tiempo en teletrabajo (inciso f, calculado de asistencia), lugares de trabajo convenidos (inciso i, contra el lugar donde se marca) y equipo otorgado (inciso k, vía RD-06); los demás campos (género, estado civil, domicilio, etc.) pueden vivir en otro sistema integrado. Conservación de versiones → CL-06. | Alto | FIRME | F-11, F-17; ver CL-06 |
| RD-09 | (NUEVA) Desconexión de alcance completo: además del término de la jornada (RD-03), el sistema debe poder detectar/alertar actividad o comunicación laboral en horarios no laborables, vacaciones, permisos y licencias, y — en horarios flexibles — durante las pausas convenidas. Cruza con los estados de ausencia que el checador ya registra. Qué acto constituye violación y qué evidencia guardar → CL-02. | Alto | FIRME* | F-09, F-12 (inciso e), F-16 (inciso e); ver CL-02 |
| RD-10 | (NUEVA) Pausas y lactancia registrables: la política debe incluir pausas para descanso dentro del horario pactado, y para madres en lactancia (máx. 6 meses) el horario debe determinar 2 reposos extraordinarios de media hora por día O reducción de 1 hora de jornada — el sistema debe poder registrar estos eventos sin computarlos como incumplimiento de jornada. Qué es una pausa "adecuada" → CL-07. | Medio | FIRME* | F-12 (inciso e), F-13, F-16 (inciso d); ver CL-07 |
| RD-11 | (NUEVA) Cambio de modalidad documentado: proceso de implementación presencial↔teletrabajo documentado, incluyendo los momentos/condiciones/causas de asistencia al centro de trabajo (5.6 b) y los mecanismos de reversibilidad (5.10); el checador registra el calendario híbrido pactado y evidencia su cumplimiento, ligado al historial de modalidad de RD-05. | Medio | FIRME | F-14, F-15 |
| RD-12 | (NUEVA) Conservación de evidencias NOM: los registros digitales valen como evidencia y se conservan al menos UN AÑO (10.4). Es piso, no techo: para registros de jornada aplican los plazos mayores de la LFT (skill `conservacion-y-prueba`) — el sistema aplica siempre el plazo más largo. | Medio | FIRME | F-18 |

\* FIRME por interpretación operativa: la obligación existe en el texto, pero
su aplicación exacta tiene una pregunta abierta registrada abajo.

### 4.1 Casos límite y preguntas abiertas

CL-01, CL-02 y CL-04 vienen de la v1 (CL-01 y CL-02 se refinan con la NOM);
CL-03 se RESUELVE en este loop; CL-05 a CL-07 son nuevos.

| ID | Caso o pregunta | Por qué es ambiguo | Estado | Quién resuelve |
|----|-----------------|--------------------|--------|----------------|
| CL-01 | ¿Sobre qué ventana se mide el "más del cuarenta por ciento del tiempo" (semana, mes, contrato)? ¿Días u horas? **v2:** la NOM obliga a declarar el % en el listado (F-11, inciso f) pero tampoco define ventana ni método. | Ni la LFT ni la NOM definen periodo ni unidad de medición. | abierta | abogado laboralista |
| CL-02 | ¿Qué constituye violación del derecho a la desconexión (mensajes, asignación de tareas, llamadas) y qué evidencia debe guardar el sistema? **v2:** la NOM ya define CUÁNDO aplica (F-09: término de jornada, no laborables, vacaciones, permisos, licencias, pausas convenidas); sigue abierto QUÉ actos la violan. | El alcance temporal quedó definido por la NOM; el alcance material no. | abierta | abogado laboralista |
| CL-03 | Requisitos específicos de la NOM-037-STPS: pendientes de transcripción contra el texto oficial. **Resuelta 2026-07-08:** NOM transcrita y verificada contra el DOF 08-06-2023 (D3/D4, FUENTES.md); los requisitos aplicables al checador son RD-08 a RD-12 y el resto quedó fuera de alcance declarado (sección 7). | — | resuelta | loop NOM-037 (esta spec) |
| CL-04 | Registro de jornada remota entre husos horarios distintos al del centro de trabajo. | Cross-ref: es el CL-03 de `jornada-laboral`; aplica con más frecuencia en teletrabajo. | abierta | decisión de producto + abogado |
| CL-05 | ¿La NOM-037 aplica a trabajadores remotos que NO superan el 40 % del tiempo (p. ej. híbridos de 1–2 días)? El campo de aplicación (F-08) y la definición 4.20 (F-10) hablan de "personas trabajadoras bajo la modalidad de Teletrabajo" sin repetir el umbral del 330-A. | Lectura conservadora: la NOM sigue al régimen LFT (>40 %); lectura literal: aplica a toda persona en la modalidad. La diferencia decide a quién exigir el listado y la política. | abierta | abogado laboralista |
| CL-06 | ¿El "listado actualizado" (F-11) exige conservar el historial de versiones (altas/bajas con fecha) o solo el estado vigente? | El PEC define actualización como reflejar altas y bajas (F-17) y el 10.4 exige conservar evidencias un año (F-18), pero no dice si las versiones anteriores del listado son "evidencia". | abierta | abogado laboralista |
| CL-07 | ¿Qué son pausas "adecuadas" (F-16, inciso d) — duración, frecuencia — y cómo registrar las pausas convenidas de horarios flexibles sin que ese registro se vuelva supervisión desproporcionada (tensión con RD-04)? | La NOM no define "adecuadas" ni el nivel de granularidad exigible del registro de pausas. | abierta | abogado laboralista |

## 5. Instrucciones de auditoría (cuerpo del SKILL.md v2)

1. **Clasificar la plantilla:** % de tiempo en domicilio por trabajador;
   >40 % → teletrabajador (RD-01; anotar CL-01 con la ventana usada y CL-05
   si hay remotos bajo el umbral).
2. **Auditar el registro de jornada remota:** mismos estándares y máximos
   que presenciales (RD-02); eximir a remotos del checador es falla
   inmediata.
3. **Auditar el listado NOM (RD-08):** existe, está en formato digital
   accesible, refleja altas/bajas de modalidad, y el sistema produce o
   alimenta sus campos operativos (% de tiempo, lugares convenidos, equipo).
4. **Auditar la desconexión completa (RD-03 + RD-09):** fin de jornada
   conocido Y cruce de actividad contra horarios no laborables, vacaciones,
   permisos, licencias y pausas convenidas (anotar CL-02).
5. **Auditar la proporcionalidad de la supervisión (RD-04):** sin
   cámaras/micrófonos permanentes; reglas de contacto con privacidad y sin
   interferir la relación trabajo-familia.
6. **Auditar pausas y lactancia (RD-10):** pausas registrables dentro del
   horario pactado; reposos de lactancia (2×30 min o −1 h, máx. 6 meses) sin
   computar como incumplimiento (anotar CL-07).
7. **Verificar modalidad, reversibilidad y calendario híbrido (RD-05 +
   RD-11):** historial de cambios documentado y días de asistencia al centro
   pactados vs. reales. Verificar insumos/equipo (RD-06).
8. **Verificar la retención (RD-12):** registros de teletrabajo conservados
   ≥ 1 año y, para jornada, el plazo mayor de `conservacion-y-prueba`.
9. **Generar el reporte** con el formato de la sección 6.

### 5.1 Árbol de decisión de severidad

```
Para cada regla que FALLA:

  ¿Clasifica mal quién es teletrabajador o exime su jornada del registro?
  (RD-01, RD-02)
     SÍ  -> CRÍTICO
     NO  -> siguiente pregunta

  ¿Sin listado NOM o desactualizado, desconexión sin cubrir todos sus
  periodos, o supervisión desproporcionada? (RD-08, RD-03/RD-09, RD-04)
     SÍ  -> ALTO
     NO  -> siguiente pregunta

  ¿Pausas/lactancia, modalidad/calendario híbrido, insumos o retención sin
  registrar o sin documentar? (RD-10, RD-05/RD-11, RD-06, RD-12)
     SÍ  -> MEDIO

  RD-07 (vigencia NOM, meta-regla) y CL-01 a CL-07 -> INFORMATIVO / PENDIENTE
```

**Checklist de consistencia:** RD-01/02 = Crítico ✓ · RD-08, RD-03/09,
RD-04 = Alto ✓ · RD-10, RD-05/11, RD-06, RD-12 = Medio ✓ · RD-07 = — /
informativo ✓ · casos de prueba alineados (sección 9) ✓.

## 6. Formato de salida

La plantilla de reporte de la librería, con encabezado actualizado:
`AUDITORÍA DE COMPLIANCE — Teletrabajo (Arts. 330-A a 330-K LFT +
NOM-037-STPS-2023)` y la misma sección adicional fija de la v1:
`CLASIFICACIÓN APLICADA: [ventana y método usados para medir el 40 %] —
pendiente CL-01`.

## 7. Límites de la skill (v2)

- Cubre el capítulo LFT completo (v1) y SOLO los numerales de la NOM-037
  verificables con datos de asistencia (RD-08 a RD-12). **Fuera de alcance
  declarado** (se listan en el reporte como "no auditado — fuera del dominio
  del checador", nunca como pendiente): condiciones físicas y ergonómicas
  del lugar de trabajo (numerales 7.1, 7.2 y 7.3 incisos a–c), listas de
  verificación de SST y su validación por la Comisión de Seguridad e Higiene
  (5.3, 5.4, 5.5, 5.5.1, 5.12), entrega de silla/insumos ergonómicos (5.7,
  salvo su registro vía RD-06), mantenimiento de equipos (5.8), capacitación
  anual (5.9 y numeral 8), exámenes médicos y avisos de accidente (5.11),
  violencia familiar (5.13, salvo su efecto de reversibilidad vía RD-11),
  participación en comisiones (5.14), obligaciones del trabajador (numeral
  6), organismos y dictámenes de evaluación de la conformidad (numerales 9,
  10.1 y 10.2) y apéndices informativos 1–5.
- Los límites de jornada son de `jornada-laboral`; el registro electrónico,
  de `registro-jornada`; la retención LFT, de `conservacion-y-prueba`; los
  reposos de lactancia se auditan aquí solo en su efecto sobre el registro
  (la skill dedicada `lactancia-y-descansos-especiales` está en el backlog).
- No resuelve los CL abiertos (CL-01, CL-02, CL-04 a CL-07): los reporta
  como INFORMATIVO.
- No es asesoría legal formal; lo declara en cada salida.
- Se revisa si se reforma el Capítulo XII Bis de la LFT o se modifica la
  NOM-037 (los hashes de D3/D4 en FUENTES.md detectan el cambio), o cuando
  el abogado resuelva los CL (fase 3).

## 8. Estructura de archivos (cambios sobre la skill v1)

```
skills/teletrabajo/
  SKILL.md                 <- ACTUALIZAR: frontmatter v2 (abajo), alcance
                              LFT+NOM, capa interpretativa (sección 3),
                              procedimiento (sección 5), árbol (5.1),
                              formato de salida (6), límites (7), estado del
                              contenido
  references/
    texto-legal.md         <- AGREGAR sección "NOM-037-STPS-2023 (D3/D4)"
                              con F-08 a F-19 tal cual la sección 2 (doc y
                              página por cita); F-01 a F-07 intactas; la
                              tabla de documentos suma D3 y D4
    reglas.md              <- REEMPLAZAR tabla por RD-01 a RD-12 (sección 4)
                              y tabla CL por CL-01 a CL-07 (4.1, CL-03
                              resuelta)
  assets/                  <- sin cambios (plantilla de la librería)
```

Regla de construcción: en `texto-legal.md` los únicos corchetes permitidos
son la omisión `[...]` (el validador lo exige); las citas de la sección 2 ya
lo cumplen.

### 8.1 Frontmatter del SKILL.md v2

```yaml
---
name: teletrabajo
description: Clasifica teletrabajadores (umbral legal >40 % del tiempo en domicilio) y audita sus obligaciones especiales en la LFT mexicana y la NOM-037-STPS-2023 — registro de jornada remota con los mismos máximos, listado NOM de teletrabajadores con % de tiempo, desconexión también en vacaciones/permisos/pausas, supervisión proporcional a la intimidad, pausas y lactancia, modalidad y reversibilidad documentadas, insumos y conservación de evidencias ≥1 año. Usar al auditar plantillas híbridas o remotas.
metadata:
  version: "2.0.0"
  owner: "Juan Pablo"
  reviewed_at: "[fecha del cierre de fase 2]"
  ley: "LFT Arts. 330-A a 330-K (Capítulo XII Bis) + NOM-037-STPS-2023"
  fuente: "LFT consolidada (última reforma DOF 2026-05-14), pp. 95-97; NOM-037-STPS-2023 (DOF 08-06-2023 ed. vespertina, pp. 3-50; vigente desde 05-12-2023)"
---
```

## 9. Casos de prueba

| # | Entrada | Debe detectar | Severidad esperada |
|---|---------|---------------|--------------------|
| 1 | Empresa con 20 teletrabajadores y sin listado NOM (ni % de tiempo por persona, ni lugares convenidos registrados) | Falla RD-08: listado 5.1 inexistente; el sistema no produce ni alimenta sus campos operativos | ALTO |
| 2 | Desconexión configurada solo al fin de jornada; el sistema manda recordatorios de checada y asigna tareas a un teletrabajador durante sus vacaciones y un permiso | Falla RD-09: la desconexión NOM cubre vacaciones, permisos y licencias, no solo el término de jornada; anotar CL-02 | ALTO |
| 3 | Teletrabajadora en periodo de lactancia sin forma de registrar los dos reposos de media hora (el sistema los marca como "salidas no autorizadas") | Falla RD-10: reposos de lactancia dentro del horario pactado deben registrarse sin computar como incumplimiento | MEDIO |
| 4 | Trabajador pasó de híbrido a 100 % remoto: el admin solo cambió un toggle, sin documento, fecha ni calendario de asistencia al centro | Falla RD-11 (y RD-05): cambio de modalidad sin proceso documentado ni historial | MEDIO |
| 5 | El sistema purga automáticamente los registros de pausas y actividad de teletrabajadores a los 6 meses | Falla RD-12: evidencias NOM se conservan al menos un año (y la jornada, el plazo mayor de la LFT) | MEDIO |
| 6 | Empleado que trabaja exactamente 2 de 5 días en casa (40.0 %) y la empresa le exige todas las obligaciones NOM como teletrabajador | Caso límite: 40.0 % NO supera "más del cuarenta por ciento" (RD-01) → no es teletrabajador LFT; si la NOM le aplica de todos modos es CL-05; reportar la ventana usada (CL-01) | INFORMATIVO |
| 7 | Sistema que clasifica >40 %, registra jornada remota igual que presencial, mantiene el listado digital con % y altas/bajas, cruza desconexión contra vacaciones/permisos/pausas, registra lactancia, documenta cambios de modalidad y conserva ≥1 año | Ninguna falla firme; INFORMATIVO por CL-01, CL-02 y CL-05 a CL-07 abiertos | CUMPLE |

## 10. Kickoff prompt (para la fase 2)

> Sube la skill `teletrabajo` a v2 en el repo skills-leyes-mx a partir de
> `specs/teletrabajo-v2-nom037-spec.md` (leyendo también la v1,
> `specs/teletrabajo-spec.md`, que sigue vigente para F-01 a F-07 y RD-01 a
> RD-06). Aplica EXACTAMENTE los cambios de la sección 8; solo contenido de
> las dos specs. Corre los 7 casos de la sección 9 y reporta. Cierra el loop
> según CLAUDE.md (validador en verde, índices, bitácora, commit+push).

---

## Estado del research

Citas F-08 a F-19 transcritas por Claude el 2026-07-08 del texto íntegro de
la NOM-037-STPS-2023 descargado de dof.gob.mx en la misma sesión: nota
5691672 en HTML (`nom037_dof.html`, D4) y PDF oficial de la edición
vespertina del 08-06-2023 (`dof_ves_08062023.pdf`, D3, 61 pp.; la NOM en
pp. 3–50). Verificación cruzada palabra por palabra entre ambos documentos
en las pp. 5–26 de D3 (numerales 1–10.4 y Transitorio). Integridad: SHA-256
idéntico en doble descarga de cada archivo, registrado en FUENTES.md.
Búsqueda web del 2026-07-08: sin modificaciones ni aclaraciones posteriores
de la NOM en el DOF. Calendarios graduales: no aplica — el único transitorio
es la entrada en vigor (F-19; 08-06-2023 + 180 días naturales = 05-12-2023).
Columna "Riesgo" de la tabla del PEC (10.3): viene VACÍA en la edición
oficial (verificado en D3 pp. 14–25); por eso ninguna regla cita severidades
del PEC. No se citaron criterios de memoria.

**Pendiente para el visto bueno de JP:** contrastar F-08 a F-19 contra las
páginas citadas de D3 (o D4); decidir si el alcance checador (sección 7) es
el correcto para Klokk.
**Pendiente para el abogado (fase 3):** CL-01 (ventana del 40 %), CL-02
(actos que violan la desconexión), CL-05 (umbral de aplicación de la NOM),
CL-06 (historial del listado), CL-07 (pausas "adecuadas" vs. supervisión
proporcional).
