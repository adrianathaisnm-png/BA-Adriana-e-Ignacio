# BA-Adriana-e-Ignacio
# Práctica: red de centros deportivos

**Autores:** Adriana e Ignacio
**Asignatura:** Python · Máster en Business Analytics (UAM)
**Notebook:** `Practica_centros_alumnado_v02.ipynb`

## Fuentes
- **Actividad y catálogo de centros:** datos sintéticos docentes del MABA.
- **Meteorología:** API histórica de Open-Meteo (temperatura máxima y mínima en °C y precipitación en mm), del 1 al 14 de septiembre de 2026, para Madrid, Barcelona y Valencia.

## Entradas (carpeta `datos`)
- `actividad.csv`: 504 sesiones deportivas, con centro, fecha, actividad, turno, duración, plazas y visitas.
- `centros.xlsx`, hoja `centros`: catálogo de los 6 centros, con nombre, ciudad y coordenadas.

## Cómo ejecutarlo en Google Colab
1. Abrir el notebook desde este repositorio con el botón *Open in Colab*.
2. Ejecutar las celdas en orden.
3. En la celda de carga, seleccionar a la vez `actividad.csv` y `centros.xlsx` de la carpeta `datos`.
4. La consulta a Open-Meteo necesita conexión a internet.
5. La última celda genera y descarga `resultados_centros.zip` con todas las salidas.

## Salidas (carpeta `salidas`, incluida en el ZIP)
- `actividad_preparada.csv`: sesiones unidas con centros y meteorología, con ocupación, duración en horas y nivel de ocupación.
- `meteo_diaria.csv`: meteorología por ciudad y día (42 filas).
- `resumen_centros.csv`: visitas totales por centro.
- `ocupacion_por_turno.csv`: ocupación media por actividad y turno.
- `visitas_diarias.csv`: visitas diarias por ciudad.
- `visitas_diarias.png` y `ocupacion_actividad.png`: gráficos.
- `fuentes.json`: ficha de las fuentes utilizadas.

## Decisiones de revisión con IA
1. **`clasificar_ocupacion`:** la IA detectó que el valor 80 se clasificaba como "media" y que las categorías iban en minúscula. Cambiamos el umbral a `< 80` y las categorías a `Baja`, `Media` y `Alta`. Lo comprobamos con 40, 50 y 80.
2. **`calcular_ocupacion`:** la llamada de prueba estaba dentro de la función, después del `return`, y no se ejecutaba. La movimos fuera y comprobamos que devuelve 75.0.

## Versiones

Lo más importante que cambiamos fue en T4: en la versión inicial la función de la API daba error porque usábamos `contenido['daily_units']` antes de crear `contenido`. Quitamos esa línea y ya funcionaba para las tres ciudades.

También corregimos T1, porque el 80 salía como "media" en vez de "Alta", y R1, porque la prueba estaba dentro de la función y no se ejecutaba. Además ajustamos la lectura de archivos en T2 para usar `DATOS` y la hoja `centros`.


