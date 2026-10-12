# Vivienda en España · Panel interactivo por CCAA y ciudades

Panel interactivo, en un único archivo HTML y sin dependencias, que combina datos de **INE, CGPJ y el Ministerio de Vivienda y Agenda Urbana** para explorar la vivienda en España desde 2008: hogares en alquiler, precio de la vivienda, lanzamientos (desahucios) y precio del alquiler por comunidad autónoma y en las 15 mayores ciudades.

**Demo:** <https://josepe04.github.io/vivienda-espana-dashboard/>

## Qué muestra

| Pestaña | Indicador | Fuente | Años |
|---|---|---|---|
| Hogares en alquiler | % de hogares en alquiler a precio de mercado | INE, Encuesta de Condiciones de Vida (tabla 76845) | 2008–2025 |
| Precio de la vivienda | Variación anual del Índice de Precios de Vivienda | INE, IPV (tabla 80271) | 2009–2025 |
| Lanzamientos | Lanzamientos practicados (total) por TSJ | CGPJ, Efectos de la crisis en los órganos judiciales | 2013–2025 |
| Precio del alquiler CCAA | Mediana €/m² al mes y su variación anual | Ministerio de Vivienda, SERPAVI | 2011–2024 |
| Precio del alquiler ciudades | Ídem, 15 mayores municipios | Ministerio de Vivienda, SERPAVI + INE (padrón 2025) | 2011–2024 |

Las pestañas de precio del alquiler y de precio de la vivienda tienen además una vista **Acumulado en un rango**: eliges dos años y ves cuánto ha subido o bajado el precio entre ambos (cambio total del periodo, no suma de variaciones anuales).

Cada pestaña tiene mapa de casillas por territorio, selector de año con reproducción, ficha del territorio, ranking y gráfico de evolución frente a la referencia nacional.

## Uso en local

No requiere instalación: abre `index.html` en el navegador. Solo necesita conexión para cargar las tipografías de Google Fonts (sin ella usa las del sistema).

## Estructura

```
index.html                 Panel (datos incrustados)
datos_raw/                 CSV descargados de las fuentes
  ine/                     ECV, IPV, IPVA, compraventas, hipotecas
  cgpj/                    Lanzamientos practicados por TSJ
  mivau_serpavi/           Alquiler SERPAVI por CCAA y para 15 ciudades
  transportes_vivienda/    Parque de viviendas, viviendas libres terminadas, protegidas
docs/INFORME_VALIDACION_DATOS.md   Cobertura, avisos y fuentes
CHANGELOG.md
LICENSE                    Creative Commons Attribution 4.0
```

Los CSV usan `;` como separador. El panel actual incrusta los datos de las cinco pestañas; los de compraventas, hipotecas, parque de viviendas, viviendas terminadas y protegidas ya están descargados y se incorporarán en próximas versiones.

## Avisos importantes sobre los datos

- **SERPAVI** procede de declaraciones de IRPF de arrendadores cruzadas con el Catastro: solo recoge alquileres de vivienda habitual declarados. Publica **medianas**, no medias. Navarra solo tiene datos desde 2021 y el País Vasco solo 2024 (Bilbao, igual).
- La referencia nacional del alquiler y la de las ciudades (media de medianas ponderada por número de contratos) es un **cálculo propio**, no un dato oficial.
- **Lanzamientos:** la serie del CGPJ empieza en 2013; Ceuta y Melilla están incluidas en Andalucía. Pendiente confirmar si la cifra se limita a vivienda habitual.
- **IPV** base 2025 = 100; la variación anual se calcula sobre las medias anuales del índice y se muestra redondeada.
- **ECV:** muestras pequeñas en Ceuta, Melilla y comunidades pequeñas; las series son irregulares.
- Detalle completo en [`docs/INFORME_VALIDACION_DATOS.md`](docs/INFORME_VALIDACION_DATOS.md).

## Licencia y atribución

Este trabajo (código del panel, documentación y datos tratados) se publica bajo **[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)**. Puedes copiarlo, redistribuirlo y adaptarlo, también con fines comerciales, citando la autoría y los cambios realizados.

Los datos originales pertenecen a sus organismos: Instituto Nacional de Estadística (INE), Consejo General del Poder Judicial (CGPJ), Ministerio de Vivienda y Agenda Urbana (SERPAVI) y Ministerio de Transportes y Movilidad Sostenible. Cada organismo tiene sus propias condiciones de reutilización; consúltalas antes de reutilizar los datos originales.

## Próximos pasos

- Mapa geográfico real en lugar de casillas.
- Pestañas de viviendas construidas, compraventas, hipotecas y vivienda protegida.
- Lectura de los datos desde los CSV en lugar de incrustarlos.
