# VHP_Fashions_SQL_CaseStudy
"SQL queries for analyzing sales, profit, and marketing data in fashions case study"


## 🌟 Introduction
VHP_Fashion is a leading retailer with a vast customer base and a team of dedicated sales representatives.  
This project simulates their **Sales Order Processing System** using SQL.  
The goal: manage customer orders, enforce constraints, and analyze sales performance.

---

## 🧩 Problem Statement
- Track salesmen, customers, and orders.  
- Enforce **primary keys, foreign keys, defaults, and not null constraints**.  
- Analyze top performers, monthly sales trends, and customers without orders.

---

## 🚀 My Approach
I created a database `VHP_FASHIONS` with three tables:
- **Salesman** → SalesmanId, Name, Commission, City, Age  
- **Customer** → CustomerId, CustomerName, SalesmanId, PurchaseAmount  
- **Orders** → OrderId, CustomerId, SalesmanId, OrderDate, Amount  

Constraints applied:
- Primary keys on IDs  
- Foreign keys linking tables  
- Default values for City  
- Not null on CustomerName  

---

## 🔑 Query Highlights

### 1️⃣ Top Performing Salesman
```sql
SELECT s.Name, SUM(o.Amount) AS TotalSales
FROM Salesman s
JOIN Orders o ON s.SalesmanId = o.SalesmanId
GROUP BY s.Name
ORDER BY TotalSales DESC;
```
2️⃣ Top 5 Customers by Purchase Amount
```
SELECT TOP 5 CustomerName, PurchaseAmount
FROM Customer
ORDER BY PurchaseAmount DESC;
```
3️⃣ Monthly Sales Trend
```
SELECT FORMAT(OrderDate, 'yyyy-MM') AS Month, SUM(Amount) AS TotalRevenue
FROM Orders
GROUP BY FORMAT(OrderDate, 'yyyy-MM')
ORDER BY Month;
```
4️⃣ Customers with No Orders
```
SELECT c.CustomerName
FROM Customer c
LEFT JOIN Orders o ON c.CustomerId = o.CustomerId
WHERE o.OrderId IS NULL;
```
💡 Insights
```
Ranking salesmen by revenue highlights top performers.

Monthly trend analysis shows seasonality in orders.

Identifying customers without orders helps target marketing.
```
🔮 Future Work
```
Add dashboards in Power BI/Tableau.

Extend schema with product categories.

Automate reporting pipelines with AWS Glue + Athena.

