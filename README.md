# DAX
Este proyecto presenta un análisis completo de las ventas de la tienda ficticia,  dedicada a la comercialización de productos electrónicos (celulares, notebooks y accesorios).   El objetivo principal es aplicar **DAX (Data Analysis Expressions)** en Power BI para obtener métricas clave del negocio y visualizar resultados de forma interactiva.

## 🎯 Objetivos del Análisis
1. Calcular las métricas principales: **ventas totales, costos, ganancia y margen (%)**.  
2. Analizar la **rentabilidad por categoría de producto**.  
3. Identificar **clientes únicos y promedio de venta por cliente**.  
4. Visualizar la **distribución geográfica de ventas** por ciudad (Argentina).  
5. Observar la **evolución temporal de ventas y ganancias**.

---

## 🧮 Medidas DAX Principales

| Medida | Código DAX | Descripción |
|--------|-------------|-------------|
| **Total Ventas** | `SUM(Ventas[Monto])` | Suma total de las ventas realizadas |
| **Total Costos** | `SUM(Ventas[Costo])` | Suma total de los costos |
| **Ganancia** | `[Total Ventas] - [Total Costos]` | Margen bruto en valor |
| **Margen %** | `DIVIDE([Ganancia], [Total Ventas])` | Porcentaje de margen de ganancia |
| **Clientes Únicos** | `DISTINCTCOUNT(Ventas[Cliente])` | Cantidad de clientes únicos |
| **Venta Promedio Cliente** | `DIVIDE([Total Ventas], [Clientes Únicos])` | Promedio de compra por cliente |
| **Ventas Mensuales** | `CALCULATE([Total Ventas], DATESMTD(Ventas[Fecha]))` | Ventas acumuladas por mes |
| **Ventas Celulares** | `CALCULATE([Total Ventas], Ventas[Categoria] = "Celulares")` | Ventas filtradas por categoría |

---

## 🗺️ Visualizaciones en Power BI

| Tipo | Descripción | Campos utilizados |
|------|--------------|------------------|
| **Tarjetas** | Métricas clave: Total Ventas, Ganancia, Margen % | Medidas principales |
| **Gráfico de barras** | Ventas por Categoría | Eje: Categoría / Valor: [Total Ventas] |
| **Gráfico de líneas** | Evolución de ventas en el tiempo | Eje: Fecha / Valor: [Total Ventas] |
| **Mapa geográfico** | Distribución de ventas por ciudad | Ubicación: `Ubicacion = Ciudad & ", Argentina"` |
| **Tabla resumen** | Producto, Ventas, Ganancia, Margen % | Producto + Medidas DAX |

---

## 🧭 Solución al problema de geolocalización
Para evitar errores de ubicación (ej. “Córdoba, España”), se creó una nueva columna:

```DAX
Ubicacion = Ventas[Ciudad] & ", Argentina"
Esto garantiza que Power BI muestre correctamente las ciudades dentro del territorio argentino.

🧰 Tecnologías Utilizadas
Power BI Desktop

Lenguaje DAX

Microsoft Excel / CSV

GitHub (para documentación y versionado)

📈 Insights Principales

📊 Las notebooks representan el mayor ingreso y margen de ganancia.

🧭 Buenos Aires concentra la mayoría de las ventas.

👥 El 40% de los clientes realizaron más de una compra.

📆 Febrero y marzo muestran un crecimiento sostenido en ventas.
