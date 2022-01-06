# Shopify-DS-Challenge-2022

## Question 1

### Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 

The calculation is being made in a very naive way. There are outlier values in the data that are driving the mean value of the order because of both the order amount and the number of items ordered. A better way is to look closely at the outlier shops and determine for each shop what the reason is for their high value and act accordingly.

### What metric would you report for this dataset?

It would make sense to use the pandas describe function. It provides the mean and the values for the percentiles (25%, 50% and 75%). 

### What is its value?
metric     order_amount Price_of_one
      
mean       300.155823	150.400163

25%        163.000000	132.000000

50%	       284.000000	153.000000

75%	       386.500000	166.000000

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
