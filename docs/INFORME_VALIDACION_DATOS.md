# Validación y descarga de datos — Dashboard vivienda (CCAA, desde 2008)
Descarga realizada el 2026-10-11. Los CSV están en `datos_raw/` (separador `;`, decimales con punto).

## Resumen de cobertura

| Indicador | Fuente | Archivo | Cobertura | Estado |
|---|---|---|---|---|
| Hogares en alquiler (% de hogares) | INE, ECV, tabla 76845 | `ine/ecv_tenencia_ccaa_tabla76845.csv` | 2008–2025, 17 CCAA + Ceuta + Melilla + Nacional | Completo |
| Precio de la vivienda (índice, base 2025=100) | INE, IPV, tabla 80271 | `ine/ipv_indice_general_ccaa_medias_anuales_tabla80271.csv` | 2007–2025 | Completo |
| Precio del alquiler (índice, base 2015=100) | INE, IPVA, tabla 59056 | `ine/ipva_alquiler_indice_total_ccaa_anual_tabla59056.csv` | 2011–2024 | Parcial: sin 2008–2010, sin 2025, **sin Navarra ni País Vasco** |
| Compraventas de viviendas | INE, ETDP, tabla 49280 | `ine/compraventas_viviendas_ccaa_anual_tabla49280.csv` | 2007–2025 | Completo |
| Hipotecas sobre viviendas | INE, Hipotecas, tabla 3223 | `ine/hipotecas_viviendas_ccaa_anual_tabla3223.csv` | 2007–2025 | Completo (Ceuta y Melilla solo desde 2010) |
| Lanzamientos (total, hipotecarios, LAU, otros) | CGPJ, Efectos de la crisis, serie por TSJ | `cgpj/lanzamientos_practicados_tsj_anual_2013_2025.csv` | 2013–2025 + 1T-2026 | Parcial: **empieza en 2013** |
| Viviendas libres terminadas | Min. Transportes, Boletín Online, tabla 3.2 | `transportes_vivienda/viviendas_libres_terminadas_ccaa_anual_tabla3.2.csv` | 2008–2025 | Completo, pero solo vivienda libre y datos estimados |
| Parque de viviendas (total / principales / no principales) | Min. Transportes, Boletín Online, tabla 2 | `transportes_vivienda/parque_viviendas_ccaa_anual_tabla2.csv` | 2008–2025 | Completo |
| Viviendas protegidas (calificaciones definitivas) | Min. Transportes, Boletín Online, tabla 1.6 | `transportes_vivienda/viviendas_protegidas_calificaciones_definitivas_ccaa_anual_tabla1.6.csv` | 2008–2025 | Completo salvo Canarias 2024 (ND en origen) |
| Alquiler: nº de viviendas arrendadas y precio (€/m² y €/mes) | Min. Vivienda, SERPAVI | `mivau_serpavi/serpavi_alquiler_ccaa_anual_2011_2024.csv` | 2011–2024 | Parcial: **Navarra solo desde 2021, País Vasco solo 2024** |

## Hallazgos y avisos para el diseño

1. **Lanzamientos desde 2013.** El CGPJ no publica la serie por territorio antes de 2013. El mapa y los gráficos de desahucios tendrán una nota "serie desde 2013". Los datos van por TSJ, que equivale a CCAA (Ceuta y Melilla están dentro de Andalucía). Total = hipotecarios + alquiler (LAU) + otros, con desajustes de ±1 por redondeo del origen en 4 celdas.
2. **Sin Navarra ni País Vasco en el IPVA.** El índice de alquiler del INE no cubre los territorios forales, y empieza en 2011. Alternativa para completar: SERPAVI (2011–2024).
3. **Alquiler en la ECV.** El indicador es el % de hogares en alquiler (a precio de mercado y por debajo de mercado), no el número de personas. Para Ceuta, Melilla y varias CCAA pequeñas la muestra es pequeña y la serie es muy irregular (por ejemplo, Navarra 2025: 8,8 % tras 13,8 %). Conviene mostrar una media móvil o un aviso.
4. **Dos bases en el IPV y en hipotecas.** El IPV está en base 2025=100; el IPVA en base 2015=100. No se pueden comparar los niveles entre ambos, solo las variaciones.
5. **Viviendas terminadas.** La tabla descargada solo cubre vivienda libre. Hay serie de vivienda protegida (calificaciones definitivas), pero está en mensual y no la he descargado todavía. El dato de Melilla 2025 (0) y algunos de los últimos años son estimaciones.
6. **Parque de viviendas.** Entre censos las cifras están interpoladas, y se ven saltos entre 2010 y 2011 y entre 2023 y 2024 (probable cambio de metodología o de referencia censal, sin confirmar). Úsalo con cautela para series temporales.
7. **Viviendas en alquiler (número).** No hay censo anual oficial. Dos aproximaciones: `n_VC + n_VU` de SERPAVI (2011–2024, solo alquileres declarados) o `viviendas principales * % en alquiler` (ECV + parque). Lo marcaríamos como estimación.

## Notas de las dos últimas descargas
- **SERPAVI** sale de declaraciones de IRPF (Modelo 100) cruzadas con el Catastro, solo alquiler de vivienda habitual. Hay dos tipologías (colectiva `VC` y unifamiliar/rural `VU`) con recuento, mediana y percentiles 25/75 del €/m²·mes y del alquiler mensual. `n_VC + n_VU` es una aproximación oficial al **número de viviendas en alquiler** por CCAA y año, aunque no cubre alquileres sin declarar. El Excel original tiene también municipio, distrito y sección censal por si se quiere bajar de nivel.
- **Viviendas protegidas:** son calificaciones definitivas (planes estatales y autonómicos), que se usan como aproximación de viviendas protegidas terminadas. Cae mucho desde 2013 y no es comparable con la serie libre en cuanto a cobertura.
- Descarga de SERPAVI: Excel de 71 MB, leído en el navegador sin guardarlo; solo se almacenó la hoja CCAA.

## Pendiente de tu decisión (resuelto)
- SERPAVI y vivienda protegida: descargados el 2026-10-12.

## Cómo se obtuvieron
INE: API Tempus (servicios.ine.es). CGPJ: Excel "Series - Efecto de la crisis ... por TSJ 1T-2026". Ministerio de Transportes: Boletín Online (apps.fomento.gob.es), tablas 32201000 y 33102000. Solo se guardaron los niveles CCAA (sin provincias) para mantener los archivos ligeros.

## Alquiler en las 15 mayores ciudades (añadido 2026-10-12)
- **Selección:** las 15 mayores por población (INE, cifras oficiales del padrón a 1-ene-2025): Madrid, Barcelona, València, Zaragoza, Sevilla, Málaga, Murcia, Palma, Las Palmas de Gran Canaria, Alicante, Bilbao, Córdoba, Valladolid, Vigo y L'Hospitalet de Llobregat (289.510 hab.; Gijón queda 16.ª con 269.894).
- **Fuente:** hoja "Municipios" del mismo Excel de SERPAVI (viviendas colectivas, mediana €/m²·mes y renta mensual mediana, nº de viviendas). Archivo: `datos_raw/mivau_serpavi/serpavi_alquiler_15_ciudades_anual_2011_2024.csv`.
- **Cobertura:** 2011–2024 para 14 ciudades; **Bilbao solo 2024** (Bizkaia no tiene serie anterior en SERPAVI).
- **Referencia en el panel:** media de las medianas de 14 ciudades (sin Bilbao) ponderada por nº de contratos; es un cálculo propio, no un dato oficial.
- **Corrección:** SERPAVI procede de declaraciones de IRPF de arrendadores (Modelo 100) cruzadas con el Catastro, no de fianzas de contratos como se indicó en un primer momento en el panel. Solo recoge alquileres de vivienda habitual declarados.
