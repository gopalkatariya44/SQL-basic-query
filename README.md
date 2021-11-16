# SQL-basic-query
This is a dbms basic query like create table, add column, add value in table
### hello guys, My name is Gopal👨🏻‍💻, 
### This is for yours😊
_______
###### software for run sql commands 
- https://popsql.com
- https://dev.mysql.com/downloads/mysql/
______

###### Show databases
```
show databases;
```
_____________________
### Create or Drop table
###### Create table
```
create table student (
    student_id int primary key,
    name varchar(20),
    classic varchar(20),
    cgpa decimal(2,2)
);
```
>Output
```
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| student_id | int          | NO   | PRI | NULL    |       |
| name       | varchar(20)  | YES  |     | NULL    |       |
| division   | varchar(20)  | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```


###### Drop table
```
drop table student;
```
_____________________
### Add or Drop Column
###### Add singal column
```
alter table student add cgpa decimal(10,10);
```

###### Drop single column
```
alter table student drop column cgpa;
```

###### Describe tabel
```
describe student;
```
_____________________
### Inserting Data

###### Insert values **_method 1_**
```
insert into student values(1, 'Gopal', 'B', 7.10);
```

###### Insert values **_method 2_**
```
insert into student(student_id, name, division) values(2, 'Gopal', 'B', 9.41);
```

###### Grab all table values
```
select * from student;
```
> Output
```
+------------+-------+----------+-------+
| student_id | name  | division | cgpa  |
+------------+-------+----------+-------+
|          1 | Gopal | B        | 7.100 |
|          2 | Gopal | B        | 9.410 |
+------------+-------+----------+-------+
```

_____________________
### Constraints
###### After datatype add `auto_increment` or `default '0.0'` [for more](https://www.w3schools.com/sql/sql_constraints.asp).
```
create table student (
    student_id int auto_increment,
    cgpa decimal(10,3) default '0.0'
);
```
```
CREATE TABLE table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    column3 datatype constraint,
    ....
);
```
_____________________
### Update and Delete
###### Update
```
update student
set division = 'A'
where student_id = 2;
```
```
update student
set division = 'b' or cgpa = 9.41
where student_id = 2;
```
###### Delete
```
delete from student 
where cgpa = 9.41;
```
```
delete from student 
where name = 'Gopal' and cgpa = 9.41;
```

_______

### Select querys
###### we can use this type of constraint `--`, `<`, `>`, `<=`, `>=`,`<>`,`AND`,`OR` ect.
###### filter the student name
```
select name from student;
```
> Output
```
+---------+
| name    |
+---------+
| parth   |
| jainam  |
| jainma1 |
| kata    |
| gopa    |
| opa     |
| goooopa |
| oopa    |
+---------+
```

###### CGPA in ascending order
```
select name, cgpa from student
order by cgpa asc;
```
> Output
```
+---------+------+
| name    | cgpa |
+---------+------+
| jainma1 | 1.41 |
| kata    | 2.41 |
| parth   | 3.41 |
| jainam  | 3.41 |
| gopa    | 3.41 |
| goooopa | 5.41 |
| oopa    | 5.41 |
| opa     | 6.41 |
+---------+------+
```

###### Print CGPA in descending order three values 
```
select name, cgpa from student
order by cgpa desc
limit 3;
```
> Output
```
+---------+------+
| name    | cgpa |
+---------+------+
| opa     | 6.41 |
| oopa    | 5.41 |
| goooopa | 5.41 |
+---------+------+
```

###### CGPA greater than 5.00
```
SELECT * FROM student
where cgpa > 5.00;
```
> Output
```
+------------+---------+---------+------+
| student_id | name    | classic | cgpa |
+------------+---------+---------+------+
|          8 | opa     | Z       | 6.41 |
|          9 | goooopa | X       | 5.41 |
|         10 | oopa    | G       | 5.41 |
+------------+---------+---------+------+
```

###### Very specific condition
```
select * from student 
where name in ('gopal','jainam','parth');
```
> Output
```
+------------+--------+---------+------+
| student_id | name   | classic | cgpa |
+------------+--------+---------+------+
|          2 | parth  | A       | 3.41 |
|          3 | jainam | B       | 3.41 |
|         14 | gopal  | G       | 9.99 |
+------------+--------+---------+------+
```
### Creating Company Database

```
CREATE TABLE employee (
  emp_id INT PRIMARY KEY,
  first_name VARCHAR(40),
  last_name VARCHAR(40),
  birth_day DATE,
  sex VARCHAR(1),
  salary INT,
  super_id INT,
  branch_id INT
);
```
```
CREATE TABLE branch (
  branch_id INT PRIMARY KEY,
  branch_name VARCHAR(40),
  mgr_id INT,
  mgr_start_date DATE,
  FOREIGN KEY(mgr_id) REFERENCES employee(emp_id) ON DELETE SET NULL
);
```
```
ALTER TABLE employee
ADD FOREIGN KEY(branch_id)
REFERENCES branch(branch_id)
ON DELETE SET NULL;
```
```
ALTER TABLE employee
ADD FOREIGN KEY(super_id)
REFERENCES employee(emp_id)
ON DELETE SET NULL;
```
```
CREATE TABLE client (
  client_id INT PRIMARY KEY,
  client_name VARCHAR(40),
  branch_id INT,
  FOREIGN KEY(branch_id) REFERENCES branch(branch_id) ON DELETE SET NULL
);
```
CREATE TABLE works_with (
  emp_id INT,
  client_id INT,
  total_sales INT,
  PRIMARY KEY(emp_id, client_id),
  FOREIGN KEY(emp_id) REFERENCES employee(emp_id) ON DELETE CASCADE,
  FOREIGN KEY(client_id) REFERENCES client(client_id) ON DELETE CASCADE
);
```
CREATE TABLE branch_supplier (
  branch_id INT,
  supplier_name VARCHAR(40),
  supply_type VARCHAR(40),
  PRIMARY KEY(branch_id, supplier_name),
  FOREIGN KEY(branch_id) REFERENCES branch(branch_id) ON DELETE CASCADE
);
```
________

###### Corporate
```
INSERT INTO employee VALUES(100, 'David', 'Wallace', '1967-11-17', 'M', 250000, NULL, NULL);
```
```
INSERT INTO branch VALUES(1, 'Corporate', 100, '2006-02-09');
```
```
UPDATE employee
SET branch_id = 1
WHERE emp_id = 100;
```
```
INSERT INTO employee VALUES(101, 'Jan', 'Levinson', '1961-05-11', 'F', 110000, 100, 1);
```
###### Scranton
```
INSERT INTO employee VALUES(102, 'Michael', 'Scott', '1964-03-15', 'M', 75000, 100, NULL);
```
```
INSERT INTO branch VALUES(2, 'Scranton', 102, '1992-04-06');
```
```
UPDATE employee
SET branch_id = 2
WHERE emp_id = 102;
```

```
INSERT INTO employee VALUES(103, 'Angela', 'Martin', '1971-06-25', 'F', 63000, 102, 2);
INSERT INTO employee VALUES(104, 'Kelly', 'Kapoor', '1980-02-05', 'F', 55000, 102, 2);
INSERT INTO employee VALUES(105, 'Stanley', 'Hudson', '1958-02-19', 'M', 69000, 102, 2);
```

###### Stamford
```
INSERT INTO employee VALUES(106, 'Josh', 'Porter', '1969-09-05', 'M', 78000, 100, NULL);
```
```
INSERT INTO branch VALUES(3, 'Stamford', 106, '1998-02-13');
```
```
UPDATE employee
SET branch_id = 3
WHERE emp_id = 106;
```
```
INSERT INTO employee VALUES(107, 'Andy', 'Bernard', '1973-07-22', 'M', 65000, 106, 3);
INSERT INTO employee VALUES(108, 'Jim', 'Halpert', '1978-10-01', 'M', 71000, 106, 3);
```

###### BRANCH SUPPLIER
```
INSERT INTO branch_supplier VALUES(2, 'Hammer Mill', 'Paper');
INSERT INTO branch_supplier VALUES(2, 'Uni-ball', 'Writing Utensils');
INSERT INTO branch_supplier VALUES(3, 'Patriot Paper', 'Paper');
INSERT INTO branch_supplier VALUES(2, 'J.T. Forms & Labels', 'Custom Forms');
INSERT INTO branch_supplier VALUES(3, 'Uni-ball', 'Writing Utensils');
INSERT INTO branch_supplier VALUES(3, 'Hammer Mill', 'Paper');
INSERT INTO branch_supplier VALUES(3, 'Stamford Lables', 'Custom Forms');
```
###### CLIENT
```
INSERT INTO client VALUES(400, 'Dunmore Highschool', 2);
INSERT INTO client VALUES(401, 'Lackawana Country', 2);
INSERT INTO client VALUES(402, 'FedEx', 3);
INSERT INTO client VALUES(403, 'John Daly Law, LLC', 3);
INSERT INTO client VALUES(404, 'Scranton Whitepages', 2);
INSERT INTO client VALUES(405, 'Times Newspaper', 3);
INSERT INTO client VALUES(406, 'FedEx', 2);
```
###### WORKS_WITH
```
INSERT INTO works_with VALUES(105, 400, 55000);
INSERT INTO works_with VALUES(102, 401, 267000);
INSERT INTO works_with VALUES(108, 402, 22500);
INSERT INTO works_with VALUES(107, 403, 5000);
INSERT INTO works_with VALUES(108, 403, 12000);
INSERT INTO works_with VALUES(105, 404, 33000);
INSERT INTO works_with VALUES(107, 405, 26000);
INSERT INTO works_with VALUES(102, 406, 15000);
INSERT INTO works_with VALUES(105, 406, 130000);
```

### More Basic Queries
###### Find all employees
```
SELECT *
FROM employee;
```
###### Find all clients
```
SELECT *
FROM clients;
```
###### Find all employees ordered by salary
```
SELECT *
from employee
ORDER BY salary ASC/DESC;
```
###### Find all employees ordered by sex then name
```
SELECT *
from employee
ORDER BY sex, name;
```
###### Find the first 5 employees in the table
```
SELECT *
from employee
LIMIT 5;
```

###### Find the first and last names of all employees
```
SELECT first_name, employee.last_name
FROM employee;
```

###### Find the forename and surnames names of all employees
```
SELECT first_name AS forename, employee.last_name AS surname
FROM employee;
```

###### Find out all the different genders
```
SELECT DISCINCT sex
FROM employee;
```

###### Find all male employees
```
SELECT *
FROM employee
WHERE sex = 'M';
```

###### Find all employees at branch 2
```
SELECT *
FROM employee
WHERE branch_id = 2;
```

###### Find all employee's id's and names who were born after 1969
```
SELECT emp_id, first_name, last_name
FROM employee
WHERE birth_day >= 1970-01-01;
```

###### Find all female employees at branch 2
```
SELECT *
FROM employee
WHERE branch_id = 2 AND sex = 'F';
```

###### Find all employees who are female & born after 1969 or who make over 80000
```
SELECT *
FROM employee
WHERE (birth_day >= '1970-01-01' AND sex = 'F') OR salary > 80000;
```

###### Find all employees born between 1970 and 1975
```
SELECT *
FROM employee
WHERE birth_day BETWEEN '1970-01-01' AND '1975-01-01';
```

###### Find all employees named Jim, Michael, Johnny or David
```
SELECT *
FROM employee
WHERE first_name IN ('Jim', 'Michael', 'Johnny', 'David');
```

### Functions
###### Find the number of employees
```
SELECT COUNT(super_id)
FROM employee;
```
###### Find the average of all employee's salaries
```
SELECT AVG(salary)
FROM employee;
```
###### Find the sum of all employee's salaries
```
SELECT SUM(salary)
FROM employee;
```
###### Find out how many males and females there are
```
SELECT COUNT(sex), sex
FROM employee
GROUP BY sex
```
###### Find the total sales of each salesman
```
SELECT SUM(total_sales), emp_id
FROM works_with
GROUP BY client_id;
```
###### Find the total amount of money spent by each client
```
SELECT SUM(total_sales), client_id
FROM works_with
GROUP BY client_id;
```

### Wildcards
- `%` = any # characters, `_` = one character

###### Find any client's who are an LLC
```
SELECT *
FROM client
WHERE client_name LIKE '%LLC';
```
###### Find any branch suppliers who are in the label business
```
SELECT *
FROM branch_supplier
WHERE supplier_name LIKE '% Label%';
```
###### Find any employee born on the 10th day of the month
```
SELECT *
FROM employee
WHERE birth_day LIKE '_____10%';
```
###### Find any clients who are schools
```
SELECT *
FROM client
WHERE client_name LIKE '%Highschool%';
```

### Union


###### Find a list of employee and branch names
```
SELECT employee.first_name AS Employee_Branch_Names
FROM employee
UNION
SELECT branch.branch_name
FROM branch;
```
###### Find a list of all clients & branch suppliers' names
```
SELECT client.client_name AS Non-Employee_Entities, client.branch_id AS Branch_ID
FROM client
UNION
SELECT branch_supplier.supplier_name, branch_supplier.branch_id
FROM branch_supplier;
```