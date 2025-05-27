# SupermercadoVida
## 🛒 Proyecto de análisis de datos - Ventas de supermercado  

## 🎖️ Objetivo: El objetivo general del proyecto consta en optimizar la toma de decisiones comerciales mediante el análisis de datos, permitiendo entender de mejor manera el desempeño del negocio, el comportamiento de los clientes, la rentabilidad de los productos y las tendencias temporales de ventas. Este análisis permitira ser mas eficientes en el desempeño de la empresa, a su vez, fomentará el pensamiento estratégico y la toma de decisiones basadas en datos.

## ⚙️ Herramientas utilizadas: 
  Python - Canva - PowerBI - Github

## 🐍 Codigo de datos: 
### import pandas as pd
### import numpy as np

### Número de filas
num_filas = 200_000

#### Generar IDs de productos con ventas diferenciadas
productos = ['Arroz', 'Leche', 'Pan', 'Carne', 'Huevos', 'Aceite', 'Frutas', 'Verduras', 'Cereal', 'Galletas']
producto_ids = np.arange(1, len(productos) + 1)

#### Asignar probabilidades a los productos (algunos tendrán muchas más ventas)
probabilidades_productos = [0.30, 0.10, 0.05, 0.07, 0.15, 0.05, 0.12, 0.08, 0.03, 0.05]

#### Generar datos de clientes con diferencias en compras por género
cliente_ids = np.arange(1, int(num_filas / 8) + 1)  # Menos clientes para aumentar el gasto por cliente
generos = np.random.choice(['Masculino', 'Femenino'], size=len(cliente_ids), p=[0.65, 0.35])  # Hombres compran más
edades = np.random.randint(18, 70, size=len(cliente_ids))

#### Generar fechas distribuidas a lo largo del año 2025, con más ventas en fines de semana y meses de alta demanda
fechas = pd.date_range(start='2025-01-01', end='2025-12-31', freq='D')
fechas_venta = np.random.choice(fechas, size=num_filas)

#### Simular ventas más diferenciadas por cantidad y gasto
cantidades_random = np.random.randint(1, 15, size=num_filas)  # Mayor rango en la cantidad vendida
precios_random = np.random.uniform(5.0, 100.0, size=num_filas).round(2)  # Más variación en los precios

#### Generar datos de ventas con estas diferencias
ventas = {
    'Venta_ID': np.arange(1, num_filas + 1),
    'Cliente_ID': np.random.choice(cliente_ids, size=num_filas),
    'Producto_ID': np.random.choice(producto_ids, size=num_filas, p=probabilidades_productos),
    'Producto': np.random.choice(productos, size=num_filas, p=probabilidades_productos),
    'Cantidad': cantidades_random,
    'Precio_Unitario': precios_random,
    'Fecha_Venta': fechas_venta
}

#### Crear DataFrame de ventas
df_ventas = pd.DataFrame(ventas)

#### Calcular el total correctamente
df_ventas['Total'] = df_ventas['Cantidad'] * df_ventas['Precio_Unitario']

#### Crear DataFrame de clientes
df_clientes = pd.DataFrame({
    'Cliente_ID': cliente_ids,
    'Genero': generos,
    'Edad': edades
})

#### Guardar como archivo CSV
df_ventas.to_csv('ventas_supermercado.csv', index=False)
df_clientes.to_csv('clientes_supermercado.csv', index=False)

print("Dataset actualizado: ventas_supermercado.csv y clientes_supermercado.csv con más diferencias entre columnas.")



## 📊 Conclusión del proyecto: 
  - Ventas estables: La tendencia en las ventas de la compañía muestran un patrón estable, en el rango mensual de 6.5 millones de pesos en volumen de ventas y 120mil productos consumidos por 16mil clientes. 
  - Segmentación de clientes:  Del total de 200mil clientes, el 25% corresponden a jovenes entre 18 y 30 años, mientras que el 75% son adultos entre 30 y 70 años, con un promedio de 44 años. Además se observó que el 65% de las ventas proviene del genero masculino. 
  - Análisis de productos: Manteniendo una utilidad del 96% en todas las categorías el producto que lidera en volumen de ventas y rentabilidad es el arroz, seguido por los huevos y tercero las frutas. Estos alimentos son versátiles y se utilizan para multiples recetas, indispensables en la dieta familiar. Es probable que los consumidores estén priorizando compras de productos para su alimentación diaria e indican una clara preferencia por alimentos naturales en lugar de los procesados. Estos alimentos suelen ser asequibles y tienen buena relación precio-rendimiento, lo que puede indicar que los consumidores están buscando optimizar el presupuesto familiar, sobre todo en tiempos de incertidumbre económica.
	
 
 ## Este proyecto es un ejemplo de como el análisis de datos puede revelar insights estratégicos para la gestión y el crecimiento de una empresa, permitiendo desarrollar soluciones más focalizadas y efectivas 



## 📩 Contacto: Este proyecto forma parte de mi proceso de aprendizaje en ciencia de datos. Si tienesn sugerencias o colaboraciones, puedes contactarme por este perfil. 


