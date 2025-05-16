Project Description
This project includes a collection of SQL queries designed to analyze business data from various tables: orders, books, and sales. The queries demonstrate the use of aggregation, filtering, grouping, and sorting with functions like COUNT(), SUM(), AVG(), MAX(), along with GROUP BY, HAVING, WHERE, and ORDER BY clauses.

Query Overview
1. Order Analysis by Region


SELECT region, COUNT(*), COUNT(DISTINCT customer_id) 
FROM orders 
WHERE status = 'completed' 
GROUP BY region 
ORDER BY COUNT(*) DESC;
📌 Purpose: Count the total number of completed orders and unique customers per region. Results are sorted by total order count in descending order.

2. Top Authors of Expensive Books

SELECT author, COUNT(id) 
FROM books 
WHERE price > 700 
GROUP BY author 
HAVING COUNT(id) > 2 
ORDER BY COUNT(id) DESC;
📌 Purpose: Identify authors with more than two books priced over 700 units. Results are sorted by the number of qualifying books in descending order.

3. Low Volume Product Sales

SELECT product_id, SUM(price) AS total_sales, SUM(quantity_sold) AS total_quantity 
FROM sales 
WHERE quantity_sold < 30 
GROUP BY product_id 
HAVING SUM(price) < 2000 
ORDER BY total_quantity DESC, total_sales ASC;
📌 Purpose: Find products with fewer than 30 units sold and total revenue under 2000. Results are sorted by quantity sold (descending) and then total revenue (ascending).

4. Sales Performance by Salesperson (2024)

SELECT salesperson, 
       SUM(amount) AS total_sales, 
       AVG(amount) AS avg_sale, 
       MAX(amount) AS max_sale 
FROM sales 
WHERE year = 2024 
GROUP BY salesperson 
HAVING SUM(amount) > 10000 
ORDER BY avg_sale DESC;
📌 Purpose: Generate sales statistics per salesperson for the year 2024, including total, average, and maximum sale amounts. Only salespeople with total sales exceeding 10,000 are included.

🛠 SQL Features Used
	•	GROUP BY — group data by a specific column.
	•	HAVING — filter aggregated results.
	•	ORDER BY — sort the final output.
	•	Aggregate functions: COUNT(), SUM(), AVG(), MAX().
	•	WHERE — filter raw data before grouping.

📁 Assumed Table Structures
	•	orders(id, region, customer_id, status)
	•	books(id, author, price)
	•	sales(id, product_id, quantity_sold, price, amount, year, salesperson)

📌 Purpose
This SQL query set is useful for:
	•	Business reporting and insights
	•	KPI dashboards
	•	Interview practice for data analyst roles
	•	Learning and mastering SQL for analytics


