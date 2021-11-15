# SQL-basic-query
This is a dbms basic query like create table, add column, add value in table
### hello guys my name is Gopal, this is for yours
_______
###### software for run sql commands 
- https://popsql.com
- https://dev.mysql.com/downloads/mysql/


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
After datatype add `auto_increment` or `default '0.0'` [for more](https://www.w3schools.com/sql/sql_constraints.asp).
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




