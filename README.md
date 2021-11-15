# SQL-basic-query
### hello guys my name is gopal this is for yours
This is a dbms basic query like create table, add column, add value in table

###### Create table with some columns
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

###### Describe tabel
```
describe student;
```

###### Show databases
```
show databases;
```

###### Add column
```
alter table student add cgpa decimal(10,10);
```

###### Drop column
```
alter table student drop column cgpa;
```

###### Drop table
```
drop table student;
```

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