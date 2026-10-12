# Changelog

Formato basado en [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/) y versionado semántico.

## [0.7.0] - 2026-10-12

### Añadido
- Pestaña **Accesibilidad alquiler ciudades**: esfuerzo de alquiler (precio mediano SERPAVI municipal × m² × 12 ÷ renta neta media del hogar) en las 15 mayores ciudades, con selector de superficie (40–100 m²). Renta: INE, Atlas de Distribución de Renta de los Hogares (2015–2023); para 2024 se usa la renta de 2023 (último dato) y así se indica.
- Nueva fuente en `datos_raw/ine/`: renta neta media por hogar de las 15 ciudades (series ADRH del INE).

## [0.6.0] - 2026-10-12

### Añadido
- Pestaña **Accesibilidad del alquiler**: esfuerzo = precio mediano del alquiler (SERPAVI) × superficie (40/60/80/100 m²) × 12 ÷ renta neta media del hogar (INE, ECV, tabla 49146), 2011–2024. La renta del año X procede de la encuesta de X+1, que pregunta por los ingresos del año anterior.
- Pestaña **Comparación**: gráfico de dispersión entre dos indicadores (valor en un año o cambio acumulado entre dos años), con recta de ajuste y correlación.
- Pestaña **Ranking acumulado**: tabla ordenable con una fila por comunidad y una columna por indicador (cambio porcentual acumulado entre dos años).
- Nueva fuente en `datos_raw/ine/`: renta neta media por hogar y comunidad (tabla 49146).

### Cambiado
- Al cambiar de pestaña, el año seleccionado se ajusta al rango disponible de esa serie.

## [0.5.0] - 2026-10-12

### Añadido
- Pestaña **Compraventas e hipotecas** (19 territorios, 2008–2025) con vistas de valor, variación anual y acumulado en un rango. Selector: compraventas de viviendas (total), vivienda nueva, vivienda de segunda mano, hipotecas sobre viviendas (número) e importe medio de la hipoteca.
- Nuevas fuentes en `datos_raw/ine/`: ETDP (tabla 6155: compraventas, nuevas y de segunda mano) y Estadística de Hipotecas (tabla 3223: número e importe en miles de euros).

### Notas
- Importe medio = capital prestado ÷ número de hipotecas (cálculo propio). Ceuta y Melilla no tienen dato de hipotecas en 2008–2009.

## [0.4.0] - 2026-10-12

### Añadido
- **Mapa geográfico real** (SVG) en todas las pestañas por comunidad autónoma, con valores sobre cada territorio, selección por clic o teclado, Canarias en recuadro y Ceuta/Melilla como círculos. Funciona también en la vista acumulada.
- Geometría simplificada en `datos_raw/geo/ccaa_mapa_simplificado.json` y atribución en el README.

### Sin cambios
- La pestaña de ciudades mantiene el mapa de casillas.

## [0.3.0] - 2026-10-12

### Añadido
- Pestaña **Vivienda pública**: viviendas protegidas con calificación definitiva por comunidad autónoma, con vistas de número, variación anual y acumulado en un rango. Selector de tipo: promotor público (2014–2025) o total de vivienda protegida (2008–2025).
- Nuevas fuentes en `datos_raw/transportes_vivienda/`: vivienda protegida de promotor público (tabla 1.6.2.2) y de promotor privado (tabla 1.6.2.1), sumadas de mensual a anual.

### Corregido
- `viviendas_protegidas_calificaciones_definitivas_ccaa_anual_tabla1.6.csv` no incluía la **Comunitat Valenciana** por un error de extracción; ahora está completo y la suma de comunidades coincide con el total nacional en todos los años.

## [0.2.0] - 2026-10-12

### Añadido
- Vista **Acumulado en un rango** en las pestañas Precio del alquiler CCAA, Precio del alquiler ciudades y Precio de la vivienda: eliges año de inicio y de fin y ves el cambio porcentual total entre ambos en el mapa, el ranking, las fichas y el gráfico (acumulado desde el año de inicio). La ficha incluye también el valor inicial y final y la tasa media anual.

## [0.1.0] - 2026-10-12

### Añadido
- Panel interactivo en un único archivo HTML con tema oscuro, selector de año con reproducción, mapa de casillas por territorio, ficha, ranking y gráfico de evolución.
- Pestaña **Hogares en alquiler** (INE, ECV): % de hogares en alquiler a precio de mercado por CCAA, 2008–2025.
- Pestaña **Precio de la vivienda** (INE, IPV): variación anual calculada sobre el índice, 2009–2025.
- Pestaña **Lanzamientos** (CGPJ): lanzamientos practicados por TSJ, 2013–2025.
- Pestaña **Precio del alquiler CCAA** (SERPAVI): mediana €/m² al mes y variación anual, 2011–2024, con selector precio / variación.
- Pestaña **Precio del alquiler ciudades** (SERPAVI + padrón INE 2025): 15 mayores municipios, 2011–2024.
- Definición del indicador y unidad visible en cada pestaña.
- Datos descargados en `datos_raw/` (INE, CGPJ, SERPAVI, Transportes y Vivienda) e informe de validación en `docs/`.
- Licencia CC BY 4.0.

### Notas
- Bilbao solo dispone de dato SERPAVI de 2024; la referencia de ciudades se calcula con las otras 14.
- Corregida la descripción de SERPAVI: procede de declaraciones de IRPF cruzadas con el Catastro, no de fianzas.
