# Changelog

Formato basado en [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/) y versionado semántico.

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
