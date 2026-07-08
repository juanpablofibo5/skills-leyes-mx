# Reglas derivadas — días de descanso

Lógica sin ambigüedad. Cada regla se ancla a las fuentes de
[texto-legal.md](texto-legal.md) por ID (F-xx). Estados: **FIRME** (el texto
lo exige hoy), **FIRME\*** (interpretación operativa razonable con pregunta
abierta registrada), **PENDIENTE** (regulación no publicada).

| ID | Regla | Riesgo | Estado | Fuente |
|----|-------|--------|--------|--------|
| RD-01 | Por cada seis días de trabajo debe existir al menos un día de descanso con goce de salario íntegro. El sistema debe detectar rachas de 7+ días trabajados consecutivos sin descanso. El método de cómputo (semana calendario vs ventana móvil) está abierto → CL-01. | Crítico | FIRME* | F-01; ver CL-01 |
| RD-02 | El descanso semanal se procura en domingo; en labor continua, los días de descanso se fijan de común acuerdo. El sistema debe registrar el día (o días) de descanso pactado de cada trabajador — sin ese dato no puede auditarse F-05. | Medio | FIRME | F-02, F-03 |
| RD-03 | Toda jornada laborada en domingo genera prima adicional de al menos +25 % sobre el salario de los días ordinarios; el sistema debe marcarla para nómina. | Alto | FIRME | F-03 |
| RD-04 | Trabajar el día de descanso no es obligatorio; si ocurre, el patrón paga salario doble por el servicio, además del salario que ya corresponde por el descanso. El sistema debe detectar todo descanso trabajado y marcar ambos conceptos. | Crítico | FIRME | F-05 |
| RD-05 | Semana incompleta o varios patrones: se acredita la parte proporcional del salario de los días de descanso, calculada sobre los días trabajados. La base con salario variable → CL-03. | Medio | FIRME | F-04; ver CL-03 |
| RD-06 | Cada domingo laborado y cada descanso trabajado deben quedar etiquetados de forma exportable, para que la nómina pague bien y la correlación horas-pagos sea verificable (R9 de registro-jornada). | Alto | FIRME* | F-03, F-05; interpretación operativa de la correlación |

\* FIRME por interpretación operativa: la obligación existe en el texto, pero
su aplicación exacta tiene una pregunta abierta registrada abajo.

## Casos límite y preguntas abiertas

| ID | Caso o pregunta | Por qué es ambiguo | Estado | Quién resuelve |
|----|-----------------|--------------------|--------|----------------|
| CL-01 | ¿El "por cada seis días de trabajo" se computa por semana calendario o por ventana móvil de días consecutivos? (P. ej.: 8 días seguidos repartidos entre dos semanas calendario, cada una con ≤ 6 trabajados.) | El texto no define el periodo de cómputo; para un checador cambia qué rachas disparan alerta. | abierta | abogado laboralista |
| CL-02 | Cuando el día de descanso del trabajador ES domingo y lo labora, ¿se acumulan la prima dominical (+25 %) y el pago doble del Art. 73? | Son artículos distintos con supuestos que se traslapan; el texto no dice si se suman. | abierta | abogado laboralista |
| CL-03 | ¿Cómo se calcula el "salario íntegro" del descanso y su proporcional con salario variable o por hora? | F-04 da la proporcionalidad por días, pero no la base para salarios variables. | abierta | abogado laboralista |
| CL-04 | Con la transición a 40 horas (semanas de 5 días), ¿el segundo día no trabajado es "descanso" con las protecciones del Art. 73 (pago doble si se labora) o día no laborable contractual? | La reforma redujo horas semanales sin tocar el esquema 6:1 del Art. 69; la naturaleza del día extra no está definida. | abierta | abogado laboralista |
