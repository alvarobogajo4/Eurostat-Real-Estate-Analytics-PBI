#  Análisis de E-commerce: Amazon India



En este proyecto he trabajado con un dataset de ventas de Amazon India. El objetivo principal ha sido transformar datos brutos  en un modelo analítico profesional, aplicando técnicas de ETL, limpieza de datos y modelado multidimensional en Power BI para posteriormente aplicar diferentes soluciones o patrones comerciales.



##  1. Limpieza y Transformación (Power Query)

Para empezar, puse orden en la estructura de los datos para que el modelo fuera escalable y eficiente:



* **Anexión de Datos:** Consolidé las tablas de diferentes categorías en una única tabla de hechos.

* **Cambio en las columnas de Precios:** Eliminé el símbolo de moneda (₹) y las comas de los miles. Después, pasé las columnas a **Número Decimal** para poder operar con ellas y poder aplicar diferentes operaciones matemáticas.



##  2. Estrategia de Calidad (Ratings y Nulos)

En las métricas de feedback (`ratings` y `no_of_ratings`) encontré bastantes valores nulos. Aquí aplique:



* **Decisión sobre Nulos:** Opté por mantener los nulos en lugar de borrar las filas para consegiuir mantener la mayor información posible del dataset.

* **Justificación:** Si borramos los nulos perderíamos información de productos nuevos o con pocas ventas que siguen formando parte del inventario. 

* Las notas las configuré como **Decimal** y el volumen de votos como **Número Entero**, ya que no existen "medias personas" votando.



##  3. Ingeniería de Características (Feature Engineering)

Para realizar mas completo el analisis incluimos columnas importantes: 



1. **Extracción de Marca:** Saqué el primer nombre de cada producto para identificar al fabricante y poder comparar marcas entre sí.

  

2. **Cálculo de Ahorro:** Creé la columna `Ahorro_Total` (actual_price - discount_price) para ver el beneficio real que recibe el cliente al comprar el producto.

   

3. **Niveles de Descuento:** Implementé una columna condicional para segmentar los productos y mas adelante poder aplicar esta segmentación para observar posibles patrones en el mercado:

   * **Bajo:** Ahorro < 10.000 rupias.

   * **Medio:** Ahorro 10.000 - 20.000 rupias.

   * **Alto:** Ahorro > 20.000 rupias.

   * **Sin descuento:** Para los valores nulos. ME QUEDA
