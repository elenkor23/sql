# sql
### 577. Employee Bonus
`Create table If Not Exists Employee (empId int, name varchar(255), supervisor int, salary int);`  
`Create table If Not Exists Bonus (empId int, bonus int);`  
`insert into Employee (empId, name, supervisor, salary) values (3, 'Brad', 0, 4000), (1, 'John', 3, 1000), (2, 'Dan', 3, 2000), (4, 'Thomas', 3, 4000);`  
`insert into Bonus (empId, bonus) values (2, 500), (4, 2000);`  

<b> Write a solution to report the name and bonus amount of each employee with a bonus less than 1000. Return the result table in any order.</b>  
```
select name, bonus    
from employee  
left join bonus using(empId)  
where bonus < 1000 or bonus is Null;
```

### 584. Find Customer Referee  
Table: Customer  

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |
| referee_id  | int     |

In SQL, id is the primary key column for this table. Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.  

Find the names of the customer that are not referred by the customer with id = 2. Return the result table in any order.  
```
select name  
from Customer  
where referee_id<>2 OR referee_id is null;
```

### 586. Customer Placing the Largest Number of Orders
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

```
select customer_number  
from orders  
group by customer_number  
order by count(customer_number) desc
limit 1;
```

### 595. Big Countries
Table: World
| Column Name | Type    |
|-------------|---------|
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | bigint  |


name is the primary key (column with unique values) for this table.  
Each row of this table gives information about the name of a country, the continent to which it belongs, its area, the population, and its GDP value.  
A country is big if:  
* it has an area of at least three million (i.e., 3000000 km2), or
* it has a population of at least twenty-five million (i.e., 25000000).
  
Write a solution to find the name, population, and area of the big countries. Return the result table in any order.
```
select name, population, area  
from world  
where area >= 3000000 or population >=25000000;
```

### 596. Classes More Than 5 Students
Table: Courses
| Column Name | Type    |
|-------------|---------|
| student     | varchar |
| class       | varchar |

(student, class) is the primary key (combination of columns with unique values) for this table. Each row of this table indicates the name of a student and the class in which they are enrolled.  
Write a solution to find all the classes that have at least five students. Return the result table in any order.  
```
select class  
from courses  
group by class having count(student) >= 5;
```

### 607. Sales Person  
Table: SalesPerson
| Column Name     | Type    |
|-----------------|---------|
| sales_id        | int     |
| name            | varchar |
| salary          | int     |
| commission_rate | int     |
| hire_date       | date    |
sales_id is the primary key (column with unique values) for this table. Each row of this table indicates the name and the ID of a salesperson alongside their salary, commission rate, and hire date.  

Table: Company
| Column Name | Type    |
|-------------|---------|
| com_id      | int     |
| name        | varchar |
| city        | varchar |
com_id is the primary key (column with unique values) for this table. Each row of this table indicates the name and the ID of a company and the city in which the company is located.  

Table: Orders
| Column Name | Type |
|-------------|------|
| order_id    | int  |
| order_date  | date |
| com_id      | int  |
| sales_id    | int  |
| amount      | int  |  

order_id is the primary key (column with unique values) for this table. com_id is a foreign key (reference column) to com_id from the Company table. sales_id is a foreign key (reference column) to sales_id from the SalesPerson table.
Each row of this table contains information about one order. This includes the ID of the company, the ID of the salesperson, the date of the order, and the amount paid.

Write a solution to find the names of all the salespersons who did not have any orders related to the company with the name "RED".  

```
select s.name from SalesPerson s
where s.sales_id not in (
    select o.sales_id from orders o join company c on c.com_id=o.com_id
    where c.name="RED"
);
```
