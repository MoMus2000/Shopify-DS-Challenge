# Shopify-DS-Challenge-2022

## Question 1

### Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 
### What metric would you report for this dataset?
### What is its value?


## SQL Questions
### How many orders were shipped by Speedy Express in total?

### SELECT COUNT(*) FROM Orders WHERE ShipperID == 1;

### Answer: 54

### What is the last name of the employee with the most orders?

### SELECT LastName FROM Employees WHERE EmployeeID in (SELECT EmployeeID FROM Orders GROUP BY EmployeeID  ORDER BY COUNT(*) DESC LIMIT 1);

### Answer: Peacock

### What product was ordered the most by customers in Germany?

### SELECT ProductName FROM Products WHERE ProductID == (SELECT ProductID FROM (SELECT * FROM Orders INNER JOIN Customers on Orders.CustomerID=Customers.CustomerID) as tb INNER JOIN OrderDetails on tb.OrderID=OrderDetails.OrderID WHERE COUNTRY=="Germany" GROUP BY ProductID ORDER BY SUM(OrderDetails.Quantity) DESC LIMIT 1 );

### Answer: Boston Crab Meat

## Contributor
- Mustafa Muhammad 
