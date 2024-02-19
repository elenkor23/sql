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
