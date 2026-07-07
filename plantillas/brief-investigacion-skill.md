# Brief de investigación — skill legal [nombre-de-la-skill]

Plantilla de la **fase 1** del pipeline (ver BACKLOG.md). El resultado de este
brief es la especificación de la que Claude Code construye la skill — el mismo
formato que la spec de `registro-jornada`. **Sin una spec que cumpla este
brief, la skill no se construye.**

## Qué investigar

- **Tema operativo:** [la pregunta que la skill responde]
- **Alcance:** [qué cubre y qué NO cubre]
- **Fuentes objetivo (por verificar):** [leyes / capítulos / NOMs a localizar]

## Requisitos NO negociables de la spec resultante

1. **Texto legal íntegro y textual** de cada artículo relevante, copiado del
   documento oficial (PDF de diputados.gob.mx o edición del DOF), con: fecha
   de la última reforma que tocó el artículo, edición del DOF donde se
   publicó, y link oficial. Cero paráfrasis, cero "según recuerdo".
2. **Verificación palabra por palabra** contra el documento oficial descargado
   en esa misma sesión de investigación (citar el nombre del archivo usado).
3. **Capa jurisprudencial separada del texto legal**, con el origen de cada
   criterio (sala, tribunal o análisis profesional citado con fuente).
4. **Reglas derivadas numeradas**, cada una con estado FIRME / FIRME*
   (interpretación) / PENDIENTE (regulación aún no publicada), riesgo y
   fuente.
5. **Consistencia de severidad** — lección del caso R5 de registro-jornada:
   la rama del árbol de decisión, la columna de riesgo de la tabla de reglas
   y la severidad esperada de los casos de prueba deben decir LO MISMO antes
   de entregar la spec. Checklist por regla: ¿árbol, tabla y casos coinciden?
6. **Mínimo 5 casos de prueba** con entrada y resultado esperado, incluyendo
   al menos un caso que CUMPLE y al menos un caso límite.
7. **Calendarios graduales explícitos** cuando el tema los tenga (p. ej.
   jornada 48→40 en 2026–2030; horas extra 9→12 desde 2028): tabla año por
   año, nunca "el límite actual" a secas.
8. **Límites de la skill** y todo lo que queda PENDIENTE de autoridad.
9. **Sección "Estado del research"** al final: qué se verificó contra qué
   documento, y qué requiere validación del abogado en la fase 3.

## Formato de entrega

Las 10 secciones de la spec de `registro-jornada`: (1) resumen ejecutivo,
(2) fuente legal verificada, (3) capa jurisprudencial, (4) reglas derivadas,
(5) instrucciones de auditoría o cálculo, (6) formato de salida, (7) límites,
(8) estructura de archivos, (9) casos de prueba, (10) kickoff prompt.
