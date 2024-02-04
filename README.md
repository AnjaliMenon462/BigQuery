1.	Find the total number of products.
   ```SQL
SELECT COUNT(*) AS total_products FROM `bigquery-public-data.thelook_ecommerce.products`;
```
![image](https://github.com/AnjaliMenon462/BigQuery/assets/154262040/30637c65-04f4-4598-8220-4c24b4f81b44)

2.	Find the average retail price of all products.
   ```SQL
SELECT AVG(retail_price) AS average_price FROM `bigquery-public-data.thelook_ecommerce.products`;
```
![image](https://github.com/AnjaliMenon462/BigQuery/assets/154262040/d9aa7337-8811-4392-bf6f-fd1a674cca72)

3.	List the names and retail prices of the top 10 most expensive products.
```SQL
SELECT name, retail_price
FROM `bigquery-public-data.thelook_ecommerce.products`
ORDER BY retail_price DESC
LIMIT 10;
```
![image](https://github.com/AnjaliMenon462/BigQuery/assets/154262040/f35b7820-c7e1-492e-8c16-b477d7952131)

4.  List the names of products that have a price between $50 and $100.
```SQL
SELECT name
FROM `bigquery-public-data.thelook_ecommerce.products`
WHERE retail_price BETWEEN 50 AND 100;
```
![image](https://github.com/AnjaliMenon462/BigQuery/assets/154262040/f9ec906d-2c13-4b5c-94c5-989f87106c7c)

5. Calculate the total revenue from all order items.
```SQL
SELECT SUM(sale_price) AS total_revenue FROM `bigquery-public-data.thelook_ecommerce.order_items`;
```
![image](https://github.com/AnjaliMenon462/BigQuery/assets/154262040/b74af7f0-1387-40fd-b23b-111a83af3783)

6. Find the total number of products in each category.
```SQL
SELECT category, COUNT(*) AS product_count
FROM `bigquery-public-data.thelook_ecommerce.products`
GROUP BY category;
```
![image](https://github.com/AnjaliMenon462/BigQuery/assets/154262040/a6397b43-a090-420c-9df1-2e27a5120c0a)

7. Find the total number of order items.
```SQL
SELECT COUNT(*) AS total_order_items FROM `bigquery-public-data.thelook_ecommerce.order_items`;
```
![image](https://github.com/AnjaliMenon462/BigQuery/assets/154262040/e8bf7ccc-cb98-4141-a9d6-e079727f7448)

8.  Find total revenue for each product category.
```SQL
SELECT p.category, SUM(oi.sale_price) AS total_revenue
FROM `bigquery-public-data.thelook_ecommerce.products` AS p
JOIN `bigquery-public-data.thelook_ecommerce.order_items` AS oi
ON p.id = oi.product_id
GROUP BY p.category
ORDER BY total_revenue DESC;
```
![image](https://github.com/AnjaliMenon462/BigQuery/assets/154262040/a6c861d7-c5c2-4653-8e84-1ea4b1d9db30)

9. List the top 10 most profitable products based on total revenue.
```SQL
SELECT p.name, SUM(oi.sale_price) AS total_revenue
FROM `bigquery-public-data.thelook_ecommerce.products` AS p
JOIN `bigquery-public-data.thelook_ecommerce.order_items` AS oi
ON p.id = oi.product_id
GROUP BY p.name
ORDER BY total_revenue DESC
LIMIT 10;
```
![image](https://github.com/AnjaliMenon462/BigQuery/assets/154262040/9e8a2c81-4195-4151-a344-edfba0215477)

10.  Find the 5 most frequently ordered products:
```SQL
SELECT p.name, COUNT(oi.product_id) AS order_count
FROM `bigquery-public-data.thelook_ecommerce.products` AS p
JOIN `bigquery-public-data.thelook_ecommerce.order_items` AS oi
ON p.id = oi.product_id
GROUP BY p.name
ORDER BY order_count DESC
LIMIT 5;
```
![image](https://github.com/AnjaliMenon462/BigQuery/assets/154262040/aaa4ca1f-4824-4fa8-8bad-0dbc4de5054d)


















