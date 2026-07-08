# BACKLOG — Catálogo de skills legales

El tablero de producción de la librería. El índice del README lista lo ya
construido; aquí vive lo que falta y en qué fase va cada skill.

**Meta:** todas las skills del catálogo construidas y consistentes
(`en-verificacion`), para pasarlas JUNTAS con un abogado laboralista y
subirlas a `verificada`.

## Pipeline de producción (por skill)

| Fase | Qué pasa | Gate para avanzar |
|------|----------|-------------------|
| 1. Investigación verificada | Se produce la spec con el texto legal contrastado contra fuente oficial (DOF / diputados.gob.mx), cumpliendo `plantillas/brief-investigacion-skill.md` | La spec cumple el brief y JP la aprueba |
| 2. Construcción | Claude Code transcribe la spec al formato Agent Skills y corre sus casos de prueba | Todos los casos pasan; árbol, tabla de riesgos y casos consistentes |
| 3. Validación legal | Un abogado laboralista revisa la librería completa | El estado sube a `verificada` |

**Definición de "lista" (antes del abogado):** construida + citas textuales
tomadas de documento oficial (con fecha y link) + reglas FIRME/PENDIENTE
consistentes + casos de prueba pasando + estado `en-verificacion`. Ninguna
skill se declara "perfecta" antes de la fase 3 — ese candado protege al
negocio.

## P1 — Núcleo: tiempo de trabajo (la propuesta de valor del Art. 132)

| Skill | Pregunta operativa | Fuentes a investigar* | Fase |
|-------|--------------------|-----------------------|------|
| `registro-jornada` | ¿El sistema cumple el registro electrónico del Art. 132 Fr. XXXIV? | Decreto DOF 2026-05-01 (ya citado en el repo) | ✅ 2 completada — espera fase 3 |
| `jornada-laboral` | ¿Cuánto puede durar la jornada por tipo de turno y por año (calendario 48→40, 2026–2030)? | LFT consolidada pp. 21–22 (Arts. 58–68) + decreto DOF 2026-05-01 | ✅ 2 completada — espera fase 3 |
| `horas-extra` | ¿Cuándo una hora es extra, cuántas caben por semana (9/9/10/11/12 en 2026–2030) y cómo se pagan? | LFT consolidada p. 22 (Arts. 65–68) + Transitorio Cuarto del decreto 2026 | ✅ 2 completada — espera fase 3 |
| `dias-de-descanso` | ¿Qué descanso semanal corresponde, qué prima aplica y qué pasa si se trabaja? | LFT consolidada p. 23 (Arts. 69–73, localizados 2026-07-07) | ✅ 2 completada — espera fase 3 |
| `dias-festivos` | ¿Qué días son descanso obligatorio y cómo se paga trabajarlos? | LFT consolidada pp. 23–24 (Arts. 74–75, localizados 2026-07-07) | ✅ 2 completada — espera fase 3 (batch aprobado por JP 2026-07-08) |

## P2 — Lo que el registro debe poder probar o cubrir

| Skill | Pregunta operativa | Fuentes a investigar* | Fase |
|-------|--------------------|-----------------------|------|
| `vacaciones` | ¿Cuántos días tocan por antigüedad y cómo se registran como ausencia justificada? | LFT consolidada p. 24 (Arts. 76–81, localizados 2026-07-07; reforma "vacaciones dignas" DOF 27-12-2022) | ✅ 2 completada — espera fase 3 (batch aprobado por JP 2026-07-08) |
| `teletrabajo` | ¿Qué obliga el teletrabajo en registro de jornada y desconexión? | LFT pp. 95–97 (Arts. 330-A–330-K, localizados 2026-07-07) ✓; NOM-037-STPS PENDIENTE (D-12) | ✅ 2 completada v1-LFT — espera NOM-037 (D-12) + fase 3 (batch aprobado por JP 2026-07-08) |
| `conservacion-y-prueba` | ¿Qué documentos conservar, cuánto tiempo, y qué pasa en juicio si faltan? | LFT pp. 335 y 340 (Arts. 784, 804 y 805, transcritos 2026-07-07) | ✅ 2 completada — espera fase 3 (batch aprobado por JP 2026-07-08) |
| `asistencia-y-faltas` | ¿Qué efectos legales tienen faltas y retardos, y qué debe quedar registrado? | LFT pp. 15–16 y 39 (Arts. 46–47, 134-V, 135-II, transcritos 2026-07-07) | ✅ 2 completada — espera fase 3 (batch aprobado por JP 2026-07-08) |

## P3 — Perímetro (decisión D-15: ENTRAN, 2026-07-08)

| Skill | Pregunta operativa | Fuentes a investigar* | Fase |
|-------|--------------------|-----------------------|------|
| `trabajo-de-menores` | ¿Qué jornadas, descansos y prohibiciones aplican a trabajadores de 15–17 años? | LFT, título del trabajo de los menores (localizar en fase 1) | pendiente |
| `lactancia-y-descansos-especiales` | ¿Qué pausas y reposos especiales debe reconocer y registrar el checador? | LFT, título del trabajo de las mujeres (localizar en fase 1) | pendiente |

## Fuera de alcance (decidido 2026-07-07)

Aguinaldo, PTU y cálculo de nómina: Klokk correlaciona horas con nómina
(regla R9 de registro-jornada) pero no calcula pagos. Si el producto cambia,
se reabre.

## Ruta a v1.0 — profesionalización (2026-07-08, tras la aprobación en bloque)

Meta: llegar a la fase 3 con TODO consolidado — la hora del abogado es cara y
debe rendir — y salir de ella con la librería `verificada` y el tag v1.0.0.

### Etapa 1 — Infraestructura de calidad (barata, protege todo lo que sigue)

1. **CI de validación** (GitHub Action): frontmatter completo y estados
   válidos en toda skill, IDs F/RD/CL únicos, links internos sin romper,
   cero `[corchetes]` fuera de `borrador`, alerta si `reviewed_at` supera el
   umbral de caducidad.
2. **Plantilla v2**: actualizar `plantillas/plantilla-skill-legal.md` al
   formato real de la librería (Agent Skills: SKILL.md + references/) — la
   plantilla v1 describe el formato viejo y es deuda desde S2.

### Etapa 2 — Completar el contenido (para que el abogado revise UNA vez)

3. **Loop NOM-037-STPS** → `teletrabajo` v2 (cierra D-12): descargar del DOF,
   transcribir los requisitos aplicables al registro/checador.
4. **Loops P3** (D-15: entran ambas): `trabajo-de-menores` y
   `lactancia-y-descansos-especiales` — fase 1 + fase 2 con el pipeline
   normal.

### Etapa 3 — Blindaje pre-abogado

5. **Auditoría de transcripción independiente**: sesión limpia que
   re-descargue los PDFs y contraste TODAS las citas F-xx carácter por
   carácter (las citas se transcribieron de imágenes de página; una segunda
   pasada caza errores de dedo).
6. **Matriz de consistencia cruzada**: reglas compartidas (techo 12h), CL
   heredados y fronteras entre skills — sin contradicciones ni referencias
   rotas entre las 9.
7. **Paquete del abogado**: `CASOS-LIMITE-CONSOLIDADO.md` con los ~35 CL-xx
   de toda la librería, priorizados por impacto en dinero (al frente:
   784-VIII vs topes 2026, concursos de pago doble, base del tope +4h,
   ventana del 47-X).

### Etapa 4 — Fase 3 y v1.0.0

8. Sesión con el abogado laboralista sobre el paquete: resolver CL,
   confirmar o corregir reglas FIRME*.
9. Aplicar resoluciones: CL → resueltos, FIRME* → FIRME, estados →
   `verificada`, versión de cada skill ↑.
10. **Tag `v1.0.0`** = librería verificada; desde ahí, Klokk puede decir con
    honestidad en qué se basa cada cálculo.

### Hallazgos de la revisión integral (2026-07-08) — room for improvement

- [ ] **M-01 (alta)** `registro-jornada` usa el formato pre-convención:
      reglas R1–R10 sin tabla CL, texto legal sin IDs F-xx ni página del PDF
      por cita, secciones con nombres propios (sin "Capa interpretativa") y
      criterios SCJN sin número de tesis/registro digital. Migrar el formato
      SIN tocar el contenido aprobado; las tesis exactas se piden al abogado.
- [x] **M-02** Fuentes sin ancla de integridad → `FUENTES.md` con SHA-256 de
      los PDFs oficiales (hecho en esta revisión).
- [ ] **M-03** `plantilla-reporte.md` compartida vive dentro de
      `registro-jornada/assets/`; moverla a `plantillas/` y actualizar los
      links de las 8 skills que la referencian.
- [ ] **M-04** Capa jurisprudencial deliberadamente vacía en 8 de 9 skills;
      poblarla con criterios verificados (Semanario Judicial de la
      Federación) en la fase 3 o en un loop dedicado.
- [ ] **M-05** Umbral de caducidad provisional (180 días, aviso — D-17);
      definir el formal con el abogado.
- [ ] **M-06** Los casos de prueba viven solo en las specs (no ejecutables);
      harness de evals por skill, post-v1.0.
- [ ] **M-07** Sin tags de release; tag `v0.9.0` al cerrar la Etapa 2
      (catálogo de 11 completo) y `v1.0.0` tras la fase 3.
- [x] **M-08** Auditoría de transcripción — pasada completa 2026-07-08:
      las citas F-xx de las 9 skills contrastadas contra las páginas
      oficiales (D1/D2, integridad confirmada por SHA-256): **0
      discrepancias**; valores duros verificados (calendarios, límites,
      porcentajes, plazos). Nota: el agente en background para la pasada se
      colgó y se reemplazó por auditoría directa en sesión. Queda como
      escalón OPCIONAL pre-fase 3: una pasada 100 % independiente (sesión
      limpia, PDFs re-descargados, lector distinto).

### En paralelo (no bloquea ninguna etapa)

- **Dogfooding**: correr las 9 skills contra el diseño actual de Klokk — los
  hallazgos son el backlog de compliance del producto.
- **Mecanismo de consumo** desde el repo principal — decisión diferida con
  dueño: Luis la resuelve e implementa al integrar (D-16).
- **Vigilancia de reformas**: rutina programada que revise DOF/diputados;
  fecha crítica conocida: disposiciones STPS del 132-XXXIV entran en vigor
  el 2027-01-01 (Transitorio Quinto).

---

\* Las referencias de este backlog son **objetivos de investigación, no
contenido verificado**. El artículo exacto, su texto vigente y su fecha de
reforma se confirman en la fase 1 — nunca se citan de memoria.
