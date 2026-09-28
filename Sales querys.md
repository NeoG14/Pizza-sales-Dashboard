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
```sql
SELECT SUM(quantity) as Total_Pizzas_Sold FROM pizza_db
```
<img width="168" height="69" alt="{18B06CE9-AFFD-40AC-A256-97A73C7478A9}" src="https://github.com/user-attachments/assets/0f41a14d-dcc9-4f95-85c9-fd0251126745" />

### 4. Total Orders
```sql
SELECT COUNT(DISTINCT order_id) as Total_orders FROM pizza_db
```
<img width="148" height="73" alt="{870E7C27-D334-4E09-9ADA-B88561954393}" src="https://github.com/user-attachments/assets/ac65da06-4d7e-40f9-a767-be5f8f575091" />

### 5.	Average Pizzas Per Order
```sql
SELECT ROUND((SUM(quantity)::numeric /
COUNT(DISTINCT order_id)), 2)
as Avg_Pizza_Per_Order
FROM pizza_db;
```
<img width="180" height="72" alt="{A62B60AE-D0F5-4CD8-8947-8828436AE65A}" src="https://github.com/user-attachments/assets/61fb520a-2c4d-4e2f-a629-f913300fff55" />

## Other Querys
### * Daily trend sales

```sql
SELECT  TO_CHAR(order_date, 'Day') as order_day, 
COUNT(DISTINCT order_id) as total_orders 
FROM  pizza_db
GROUP BY TO_CHAR(order_date, 'Day'
```

<img width="185" height="218" alt="{44EA803A-3439-450C-90B1-BB618C09DB2D}" src="https://github.com/user-attachments/assets/a67a3e7e-2fd0-43be-83e7-15adfccfcb0c" />

### * Hourly trend sales

```sql
SELECT  TO_CHAR(order_time, 'HH24') as order_hour, 
COUNT(DISTINCT order_id) as total_orders 
FROM  pizza_db
GROUP BY TO_CHAR(order_time, 'HH24')
```

<img width="190" height="418" alt="{EEA32F76-926E-49E1-B85B-1BE5570D57E2}" src="https://github.com/user-attachments/assets/cf91bd92-b082-47c3-8b7e-83a948ec294f" />

### * Orders per category

```sql
SELECT pizza_category as pizza_category, COUNT(DISTINCT order_id) as total_orders
FROM pizza_db
GROUP BY pizza_category
```

<img width="248" height="144" alt="{0CECDAF5-0139-4E35-A9CA-6690FDAB7D1B}" src="https://github.com/user-attachments/assets/af383c15-12dd-425b-a8ab-20be740c8372" />

### * Total pizzas sold per category

```sql
SELECT pizza_category as pizza_category, SUM(quantity) as total_orders
FROM pizza_db
GROUP BY pizza_category
```

<img width="248" height="145" alt="{509CA97B-98FB-46B3-BB2D-92989C3041D9}" src="https://github.com/user-attachments/assets/d4daf785-bdde-40cf-8a2c-ba6fa3527112" />

### * Top 5 ordered pizzas

```sql
SELECT pizza_name as pizza_name, COUNT(DISTINCT order_id) as total_orders
FROM pizza_db
GROUP BY pizza_name 
ORDER BY total_orders DESC
LIMIT 5
```

<img width="269" height="170" alt="{DDA8E835-D65E-45C2-A60E-00F9700BEB94}" src="https://github.com/user-attachments/assets/30ecaab0-e13b-48cb-b657-63c7975852d7" />

### * Top 5 pizzas sold

```sql
SELECT pizza_name, SUM(quantity) as total_pizzas_sols
from pizza_db 
GROUP BY pizza_name
ORDER BY total_pizzas_sols DESC
LIMIT 5
```

<img width="298" height="170" alt="{D4B6DA52-85C4-4207-B4AC-844A42D110A2}" src="https://github.com/user-attachments/assets/d67b269f-8d29-4184-a6eb-62f64f98969e" />

### * Worst 5 pizzas

```sql
SELECT pizza_name, SUM(quantity) AS total_pizza_sold FROM pizza_db
GROUP BY pizza_name
ORDER BY total_pizza_sold ASC
LIMIT 5
```

<img width="286" height="166" alt="{C1EA00CD-938D-45B5-A428-3A6328255533}" src="https://github.com/user-attachments/assets/35bbc500-b603-4bcf-9605-fe377971521a" />

### * Percentage of sales per category

```sql
SELECT pizza_category, 
ROUND((SUM(total_price) * 100 / 
(SELECT SUM(total_price) from pizza_db))::NUMERIC, 2) as percentage
from pizza_db
GROUP BY pizza_category
````

<img width="283" height="143" alt="{0FB22EEB-37ED-4604-8C55-638F8B3CBC3F}" src="https://github.com/user-attachments/assets/8a1580b3-e109-4fdd-86c1-1c968e4f9a0f" />

### * Percentage of sales per size

```sql
SELECT pizza_size, 
ROUND( SUM(total_price)::NUMERIC, 2) as Total_sales_category,
ROUND( (SUM(total_price) * 100 / 
(SELECT SUM(total_price) from pizza_db))::NUMERIC, 2) as percentage
from pizza_db
GROUP BY pizza_size
```
<img width="381" height="165" alt="{F66C4609-17DD-49F2-9EDC-4040051D179B}" src="https://github.com/user-attachments/assets/5bc52616-1b4e-4ae3-a011-29767fe70bae" />

---

NOTA: USAR WHERE CON LAS CLAUSULAS PARA FILTRAR POR MES, AÑO, QUARTER, ETC

WHERE EXTRACT(MONTH from order_date) = 1  FILTRA POR EL MES DE ENERO

WHERE EXTRACT(QUARTER from order_date) = 1  FILTRA POR LOS MESES DEL PRIMER CUARTO ENERO, FEBRERO, MARZO 
CONTAR EL NUMERO DE ORDENES

---

1 CREAR UNA NUEVA COLUMNA X y luego SEPARAR LAS ORDENES

<img width="273" height="647" alt="image" src="https://github.com/user-attachments/assets/0ca2cbf5-20f6-4a9d-8504-a98b2d3358c1" />

LUEGO HACER TODO 1/ Y TE DIVIDE EN PARTES DE 1

=1/COUNTIF(B:B;[@[order_id]])

<img width="184" height="221" alt="{EC93C7DB-F1FC-4D6F-BC78-4EC8243EF40D}" src="https://github.com/user-attachments/assets/f34c342c-52b8-4f3f-91a1-7d0a531230f1" />




