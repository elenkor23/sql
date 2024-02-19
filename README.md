# sql
## 577. Employee Bonus
`Create table If Not Exists Employee (empId int, name varchar(255), supervisor int, salary int);`  
`Create table If Not Exists Bonus (empId int, bonus int);`  
`insert into Employee (empId, name, supervisor, salary) values (3, 'Brad', 0, 4000), (1, 'John', 3, 1000), (2, 'Dan', 3, 2000), (4, 'Thomas', 3, 4000);`  
`insert into Bonus (empId, bonus) values (2, 500), (4, 2000);`  

<b> Write a solution to report the name and bonus amount of each employee with a bonus less than 1000. Return the result table in any order.</b>  
`select name, bonus`    
`from employee`  
`left join bonus using(empId)`  
`where bonus < 1000 or bonus is Null;`

## 584. Find Customer Referee  
Table: Customer  

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |
| referee_id  | int     |

In SQL, id is the primary key column for this table. Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.  

Find the names of the customer that are not referred by the customer with id = 2. Return the result table in any order.  

`select name`  
`from Customer`  
`where referee_id<>2 OR referee_id is null;`

## 586. Customer Placing the Largest Number of Orders
Table: Orders
| Column Name     | Type     |
|-----------------|----------|
| order_number    | int      |
| customer_number | int      |

order_number is the primary key (column with unique values) for this table.  

This table contains information about the order ID and the customer ID.   

Write a solution to find the customer_number for the customer who has placed the largest number of orders.

The test cases are generated so that exactly one customer will have placed more orders than any other customer.

The result format is in the following example.

`select customer_number`  
`from orders`  
`group by customer_number`  
`order by count(customer_number) desc`
`limit 1;`
