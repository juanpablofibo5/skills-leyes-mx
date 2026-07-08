# Reglas derivadas — para auditar

Lógica sin ambigüedad. Cada regla se marca **FIRME** (ley o tribunales lo
exigen hoy) o **PENDIENTE** (disposiciones STPS 2027).

| #   | Regla que el sistema debe cumplir | Riesgo | Estado |
|-----|-----------------------------------|--------|--------|
| R1  | Registrar inicio y fin de jornada por cada trabajador individualmente. | Crítico | FIRME |
| R2  | Registro inalterable, o con log de auditoría de cualquier corrección (quién, cuándo, qué). | Alto | FIRME* |
| R3  | Exportable por trabajador y periodo, en formato entregable a la autoridad. | Crítico | FIRME |
| R4  | Evidencia de que el trabajador acordó el mecanismo (para prueba plena). | Alto | FIRME |
| R5  | Conservar histórico (mín. 12 meses; idealmente toda la relación laboral). | Alto | FIRME* |
| R6  | Registrar teletrabajadores con los mismos estándares que presenciales. | Medio | FIRME |
| R7  | Datos del trabajador consistentes con nómina, contrato, IMSS y CFDI. | Crítico | FIRME |
| R8  | Registro continuo y no selectivo (no permitir huecos convenientes). | Alto | FIRME* |
| R9  | Correlación verificable entre horas registradas y pagos de nómina. | Alto | FIRME* |
| R10 | Formato técnico exacto, campos adicionales y excepciones por sector. | — | PENDIENTE |

\* **FIRME por interpretación / tribunales:** no está en el texto con esas
palabras, pero se deriva del requisito de "prueba plena" o de criterios
judiciales sobre registros confiables. Las disposiciones de 2027 podrían
formalizarlo.

**Precisión 2026-07-07 (verificada contra el Art. 804 LFT, consolidada
p. 340):** el piso estatutario de conservación de controles de asistencia es
"durante el último año y un año después de que se extinga la relación
laboral" (Art. 804, fracc. III y último párrafo). R5 ("mín. 12 meses") queda
anclada a esa fuente — y el plazo posterior a la extinción, que R5 no
mencionaba, es exigible. El detalle completo vive en la skill
`conservacion-y-prueba`.
