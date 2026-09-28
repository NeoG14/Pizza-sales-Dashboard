# Pizza sales Dashboard
Análisis interactivo del volumen de ventas y rendimiento del menú de una pizzería para identificar patrones de comportamiento del consumidor, horarios pico y optimizar el inventario.

## Problemas de negocio
- ¿Cuáles son los días y horarios con mayor volumen de pedidos?

- ¿Qué tamaño y categoría de pizza generan más ingresos?

- ¿Cuáles son las pizzas de mejor y peor rendimiento?

## insights
- Demanda: Los días con mayor cantidad de pedidos son los jueves y sábados. Los horarios pico se concentran entre las 12:00-13:00 y las 17:00-19:00.
- Ventas por Categoría: La categoría Classic Y el tamaño Large aporta el máximo de ventas e ingresos.
- Rendimiento de Producto: La Classic Deluxe y The Barbecue Chicken son las más vendidas, mientras que la Brie Carre tiene el peor rendimiento. 

[Dashboard](images/Dashboard.png)



## Dataset
1. pizza_id: Identificador único para cada registro individual de pizza vendida.
2. order_id: Identificador único del pedido o ticket (una orden puede contener múltiples pizza_id).
3. pizza_name_id: Código corto que abrevia el nombre y tamaño de la pizza.
4. quantity: Cantidad de pizzas de ese mismo tipo y tamaño compradas en la línea del pedido.
5. order_date: Fecha en la que se realizó el pedido.
6. order_time: Hora exacta en la que se registró el pedido.
7. unit_price: Precio unitario de la pizza según su tipo y tamaño.
8. total_price: Precio total de la línea (unit_price multiplicado por quantity).
9. pizza_size: Tamaño de la pizza.
10. pizza_category: Categoría a la que pertenece la receta de la pizza.
11. pizza_ingredients: Lista de ingredientes separados por comas utilizados en la preparación.
12. pizza_name: Nombre comercial completo de la pizza.


## Herramientas 
- Excel y Power Query para la limpieza - [Excel Dashboard](Pizza_Dashboard.xlsx)
- PostgreSQL para el analisis de los datos - [Querys SQL](https://github.com/NeoG14/Pizza-sales-Dashboard/blob/main/Sales%20querys.md)


