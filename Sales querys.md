# KPI REQUIREMENTS	
1.	Total Revenue: The sum of the total price of all pizza orders.
2.	Average Order Value: The average amount spent per order, calculated by dividing the total revenue by the total number of orders.
3.	Total Pizzas Sold: The Sum of the quantities of all pizzas sold.
4.	Total Orders: The total number of orders placed.
5.	Average Pizzas Per Order: The average number of pizzas sold per order, calculated by dividing the total number of pizzas sold by the total number of orders.

## Querys Used
### 1. Total Revenue 
Sumo toda la columna con la función  `SUM` total_price y le asigno el alias Total_Revenue con `as`
```sql
SELECT SUM(total_price) as Total_Revenue 
FROM pizza_db;
```
<img width="168" height="73" alt="{731C85CA-6F0D-42F8-8DCD-DBA7892986AA}" src="https://github.com/user-attachments/assets/0e53ae2d-dcc8-46d0-a500-f8a4a7eda368" />

### 2. Average Order Value
Calculo el promedio de las ordenes como **total_revenue/total_orders**, utilizo `DISTINCT` porque una orden puede tener muchos productos y cuento cuantas ordenes hay con `COUNT`
```sql
SELECT SUM(total_price) / COUNT(DISTINCT order_id) as Average_Order_Value
FROM pizza_db
```
<img width="187" height="65" alt="{105924DC-A696-41FE-824A-A7ED04174503}" src="https://github.com/user-attachments/assets/1fc3d9da-1fd2-47bb-a058-3e43c5d2453e" />

### 3. Total Pizzas Sold


