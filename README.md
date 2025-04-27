# DBA Challenge 20240802 (This is a challenge by Coodesh)

## Solução das cinco consultas do projeto de selects em base dados na linguagem SQL

--Consulta 1
SELECT c.customer_id, c.first_name, c.last_name FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;

--Consulta 2
SELECT p.product_id, p.product_name
FROM  products p
LEFT JOIN order_items oi ON p.product_id = oi.product_id
WHERE oi.order_id IS NULL;

--Consulta 3
SELECT s.product_id
FROM stocks s
WHERE s.quantity = 0;

--Consulta 4
SELECT o.store_id, b.brand_name, SUM(oi.quantity) as total_sales
FROM orders o
JOIN order_items oi ON o.order_id = oi.order_id
JOIN products p ON oi.product_id = p.product_id
JOIN brands b ON p.brand_id = b.brand_id
GROUP BY o.store_id, b.brand_name
ORDER BY o.store_id, b.brand_name;

--Consulta 5
SELECT s.staff_id
FROM staffs s
LEFT JOIN orders o ON s.staff_id = o.staff_id
WHERE o.order_id IS NULL;
