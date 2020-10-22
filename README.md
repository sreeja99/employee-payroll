# employee-payroll

### UC1 - Create database for payroll_service
```
create database payroll_service;
```
### see the DB created using show database query
```
show databases;
```

### Go to the database created 
```
use payroll_service;
```

### UC2 - create a employee payroll table
```
CREATE TABLE employee_payroll
    -> (
    ->   id                  INT unsigned NOT NULL AUTO_INCREMENT,
    ->   name                VARCHAR(150) NOT NULL,
    ->   salary              Double NOT NULL,
    ->   start               DATE NOT NULL,
    ->   PRIMARY KEY         (id)
    -> );
```
### see the table by using database query
```
DESCRIBE employee_payroll;
```

### UC3 - Ability to create employee payroll data in the payroll service
```
 INSERT INTO employee_payroll(name , salary , start) VALUES
    -> ( 'Bill',1000000.00,'2018-01-03'),
    -> ( 'Terisa',2000000.00,'2019-11-13'),
    -> ('Charlie',3000000.00,'2020-05-21');
```

### UC4 - Ability to retrieve all the employee payroll
```
SELECT* FROM employee_payroll;
```

### UC5 - Ability to retrieve salary of particular person and employees who havejoined in a particular data range

### viewing salary of particular person
```
SELECT salary FROM employee_payroll WHERE name='Bill';
```
### checking employees who joined at particular date range 
```
SELECT *FROM employee_payroll
    -> WHERE start BETWEEN CAST('2018-01-01' AS DATE) AND DATE(NOW());
```

### UC6 - Ability to add gender to table

### adding gender
```
ALTER TABLE employee_payroll ADD gender CHAR(1) AFTER name;
```
### setting F gender for female employees
```
update employee_payroll set gender='F' where name='Terisa';
```
### setting M gender for male employees
```
update employee_payroll set gender='M' where name='Bill' or name='Charlie';
```
### viewing gender
```
SELECT *FROM employee_payroll;
```
### UC6 - Ability to add gender to table

### average salary of a female employee
```
SELECT AVG(salary) FROM employee_payroll WHERE gender='F' GROUP BY gender;
```
### average salary accoring to genders
```
SELECT gender,AVG(salary) FROM employee_payroll GROUP BY gender;
```
### number of employees in according to genders
```
SELECT gender,COUNT(name) FROM employee_payroll GROUP BY gender;
```
### total salary according to genders
```
SELECT gender,SUM(salary) FROM employee_payroll GROUP BY gender;
```
### minimum salaries accoring to genders
```
SELECT gender,MIN(salary) FROM employee_payroll GROUP BY gender;
```
### maximum salaries accoring to genders
```
SELECT gender,MAX(salary) FROM employee_payroll GROUP BY gender;
```