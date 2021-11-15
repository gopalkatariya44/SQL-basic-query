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

###### Select querys
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

##### Print CGPA in descending order three values 
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