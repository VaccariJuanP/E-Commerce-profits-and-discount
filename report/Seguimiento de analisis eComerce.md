

## **Informe Analítico**

### **Ventas, rentabilidad y política de descuentos por región y categoría de producto**

---

### **1\. Introducción**

Se trabajó con el dataset **Superstore Sales** disponible en Kaggle  
([https://www.kaggle.com/datasets/ishanshrivastava28/superstore-sales](https://www.kaggle.com/datasets/ishanshrivastava28/superstore-sales)).

El dataset contiene aproximadamente **10.000 registros**, donde cada fila representa **un producto individual dentro de una orden de compra**. Incluye información sobre ventas, ganancias (profit), descuentos aplicados, ubicación geográfica de los clientes, modos de envío y clasificación de productos.

El objetivo del análisis fue **evaluar la relación entre ventas, ganancias y política de descuentos**, identificando regiones y productos que generan pérdidas. Durante el análisis se detectó una proporción significativa de registros con **profit negativo a nivel producto**, lo que motivó una investigación más detallada para comprender dónde se producen estas pérdidas, cuáles podrían ser sus causas y qué acciones podrían recomendarse para mejorar la rentabilidad.

---

### **2\. Preparación y validación de datos**

La exploración y limpieza inicial de los datos se realizó en **Google Sheets**, utilizando validaciones y tablas dinámicas para detectar posibles errores o inconsistencias.

Las verificaciones realizadas fueron:

* Revisión de unicidad de identificadores  
* Búsqueda de filas duplicadas  
* Validación de formatos de fecha  
* Coherencia temporal entre fecha de orden y fecha de envío  
* Cálculo y revisión de días de demora en la entrega  
* Búsqueda de outliers  
* Control de valores inválidos:  
  * ventas negativas  
  * cantidades negativas  
  * descuentos mayores al 100%  
  * valores de profit vacíos  
* Identificación de registros con profit negativo

Tras estas validaciones, el dataset final quedó compuesto por **9.994 registros**, sin duplicados ni inconsistencias relevantes. Se identificaron **1.871 registros con profit negativo**, lo que representa **el 18,7% del total**.

---

### **3\. Visualizaciones y metodología de análisis**

Una vez validado el dataset, se exportó como CSV y se cargó en **Looker Studio** para la construcción de un informe interactivo.

🔗 **URL del dashboard:**  
[https://lookerstudio.google.com/reporting/3ed05329-6b5f-4f18-8cb0-da1d6ca28baf](https://lookerstudio.google.com/reporting/3ed05329-6b5f-4f18-8cb0-da1d6ca28baf)

#### **Niveles de agregación analizados**

* Estado (State)  
* Categoría de producto  
* Subcategoría de producto

#### **Métricas utilizadas**

* Suma de ventas (*sales*)  
* Suma de ganancias (*profit*)  
* % de ganancia sobre ventas (campo calculado)  
* Promedio de descuento aplicado

---

### **4\. Descripción del dashboard y principales hallazgos**

#### **Página 1 – Análisis por estado**

Se presenta una tabla general por estado con ventas, ganancias y porcentaje de ganancia sobre ventas, acompañada de filtros y KPIs.  
El gráfico de barras comparativo muestra que los estados con mayor profit coinciden con aquellos que aplican **menores descuentos promedio**, mientras que los estados con pérdidas presentan descuentos significativamente más altos.

---

#### **Página 2 – Relación entre ventas y ganancias**

El gráfico de dispersión permite observar la relación entre volumen de ventas y rentabilidad, incorporando el tamaño de burbuja como indicador de unidades vendidas.

Las tablas de *top 10* y *bottom 10* estados muestran una diferencia clara:

* Estados con pérdidas: **descuentos promedio entre 28% y 37%**  
* Estados con mayores ganancias: **descuentos entre 0% y 8%**

Esto indica que **mayor volumen de ventas no garantiza mayor rentabilidad**.

---

#### **Página 3 – Análisis por categoría de producto**

Las tres categorías generales presentan descuentos promedio similares (13%–17%). Sin embargo, una de ellas muestra un **margen de ganancia significativamente menor (≈2,5%)**, afectando negativamente el resultado global, independientemente del estado donde se venda.

---

#### **Página 4 – Análisis por subcategoría**

Al profundizar en las subcategorías, se observa que solo **dos subcategorías** concentran las mayores pérdidas:

* *Tables* (≈28% de descuento)  
* *Bookcases* (≈21% de descuento)

Otras subcategorías con descuentos similares no presentan pérdidas, lo que sugiere que **el problema no es únicamente el descuento, sino su interacción con el tipo de producto**.

---

#### **Página 5 – Subcategorías por estado**

Esta vista permite identificar en qué estados se concentra el consumo de las subcategorías deficitarias, facilitando decisiones de ajuste localizado de descuentos o de discontinuación de productos específicos.

---

### **5\. Conclusiones finales**

El análisis muestra que las pérdidas no se distribuyen de forma homogénea, sino que están fuertemente asociadas a **combinaciones específicas de productos y políticas de descuento**.

Una de las tres categorías generales reduce significativamente la rentabilidad total, y dentro de ella, las subcategorías *Tables* y *Bookcases* explican la mayor parte de las pérdidas. En contraste, subcategorías como *Copiers*, *Phones* y *Accessories* presentan altos niveles de rentabilidad incluso con descuentos moderados.

Un caso destacable es *Binders*, que combina **alto profit con descuentos elevados**, lo que refuerza la idea de que el descuento en sí no es el problema, sino el producto al que se aplica.

#### **Recomendaciones:**

* Reducir o eliminar descuentos en subcategorías deficitarias.  
* Evaluar la discontinuación de productos persistentemente no rentables.  
* Reorientar la estrategia comercial hacia productos con mayor margen.  
* Aplicar políticas de descuento diferenciadas según producto y región.

