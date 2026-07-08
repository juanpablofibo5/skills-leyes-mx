# FUENTES — registro de documentos oficiales

Cadena de custodia de las fuentes contra las que se transcribió el contenido
legal de la librería. Los PDFs no se guardan en el repo (D-03); su integridad
se ancla por hash: si al re-descargar una URL el SHA-256 cambia, el documento
cambió (posible reforma) y las citas que dependen de él deben re-verificarse.

| Doc | Documento | Versión (portada) | Descargado | SHA-256 |
|-----|-----------|-------------------|------------|---------|
| D1 | LFT consolidada, Cámara de Diputados — https://www.diputados.gob.mx/LeyesBiblio/pdf/LFT.pdf | "Última Reforma DOF 14-05-2026" (457 pp.) | 2026-07-07 | `12f09393a1951a91c3f57f579bf611b034edf1a5f78cdbfb828e23ff3a9acbf7` |
| D2 | Decreto de reducción de la jornada laboral, DOF 1-may-2026 ed. vespertina — https://www.diputados.gob.mx/LeyesBiblio/ref/lft/LFT_ref52_01may26.pdf | pp. 3–4 de la edición (2 pp.) | 2026-07-07 | `3956ee7d5bae8f85249126e9b94e347c7598ac66384fff6d2d6dabea8d760241` |
| D3 | NOM-037-STPS-2023 (Teletrabajo — SST), DOF edición vespertina 08-06-2023, PDF oficial — https://www.dof.gob.mx/abrirPDF.php?archivo=08062023-VES.pdf&anio=2023&repo= | Edición vespertina 08-jun-2023 (61 pp.; la NOM en pp. 3–50) | 2026-07-08 | `4473e7f03fb112508e240807e75acea6d4bcf986e4209315585f38276b4de91b` |
| D4 | NOM-037-STPS-2023, texto íntegro de la nota del DOF (HTML, nota 5691672) — https://www.dof.gob.mx/nota_detalle.php?codigo=5691672&fecha=08/06/2023 | DOF: 08/06/2023 (texto original, sin reformas conocidas) | 2026-07-08 | `1782d54ca2b01b7cbcc97e197d2dc80c8aca0444318b89d272a37c16acf9ac4c` |

**Cómo verificar:** `curl -sL <URL> | shasum -a 256` — hash igual = misma
versión que la usada por la librería; hash distinto = revisar qué cambió
antes de confiar en las citas. (D3 y D4 se verificaron con doble descarga
en la sesión del 2026-07-08: hash idéntico en ambas.)
