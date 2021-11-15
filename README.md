# SQL-basic-query
This is a dbms basic query like create table, add column, add value in table

###### Create table with some columns
```
create table student (
    student_id int primary key,
    name varchar(20),
    classic varchar(20)
);
```
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

######c Drop table
```
drop table student;
```
