# SQL-basic-query
### hello guys my name is gopal this is for yours
This is a dbms basic query like create table, add column, add value in table

###### Create table with some columns
```
create table student (
    student_id int primary key,
    name varchar(20),
    classic varchar(20)
);
```
> +------------+--------------+------+-----+---------+-------+
> | Field      | Type         | Null | Key | Default | Extra |
> +------------+--------------+------+-----+---------+-------+
> | student_id | int          | NO   | PRI | NULL    |       |
> | name       | varchar(20)  | YES  |     | NULL    |       |
> | classic    | varchar(20)  | YES  |     | NULL    |       |
> | cgpa       | decimal(2,2) | YES  |     | NULL    |       |
> +------------+--------------+------+-----+---------+-------+
###### Show tabel
```
describe student;
```

###### Show databases
```
show databases;
```

###### Add column
```
alter table student add cgpa decimal(2,2);
```

###### Drop column
```
alter table student drop column cgpa;
```

###### Drop table
```
drop table student;
```
