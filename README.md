# Pizza sales Dashboard
Análisis interactivo del volumen de ventas y rendimiento del menú de una pizzería para identificar patrones de comportamiento del consumidor, horarios pico y optimizar el inventario.

<img width="1718" height="970" alt="{CA12DE69-9BFF-4FD0-A013-EAAB5505A7CB}" src="https://github.com/user-attachments/assets/fd05dc69-6c69-4357-8290-eeb2714d0138" />


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


