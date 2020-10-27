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
### UC7 - Ability to Find Min,Max,Avg,Sum

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
### UC8 - Ability to extend employee_payroll data to store employee information like employee phone, address and department
### adding phone number to table after name
```
ALTER TABLE employee_payroll ADD phone_number VARCHAR(250) AFTER name;
```
### adding address to table after phone number
```
ALTER TABLE employee_payroll ADD address VARCHAR(250) AFTER phone_number;
```
### adding department after address
```
 ALTER TABLE employee_payroll ADD department VARCHAR(150) NOT NULL AFTER address;
```
### setting default for address
```
ALTER TABLE employee_payroll ALTER address SET default 'TBD';
```
### adding into employee pay roll and checking if its throwing error if department is not mentioned 
```
INSERT INTO employee_payroll(name,salary,start) VALUES('BILL',1000000.00,'2018-01-03');
```
### UC9  -Ability to extend employee_payroll table to have Basic Pay, Deductions, Taxable Pay, Income Tax, Net Pay
### changing salary column to basic_pay
```
ALTER TABLE employee_payroll RENAME COLUMN salary TO basic_pay;
```
### adding deductions after basic_pay
```
ALTER TABLE employee_payroll ADD deductions Double NOT NULL AFTER basic_pay;
```
### adding taxable_pay after deductions
```
ALTER TABLE employee_payroll ADD taxable_pay Double NOT NULL AFTER deductions;
```
### adding tax after taxable_pay
```
ALTER TABLE employee_payroll ADD tax Double NOT NULL AFTER taxable_pay;
```
### adding net_pay after tax
```
ALTER TABLE employee_payroll ADD net_pay Double NOT NULL AFTER tax;
```
### updating department of Terisa to sales
```
update employee_payroll set department='Sales' where name='Terisa';
```
### insert Terisa's new payroll
```
INSERT INTO employee_Payroll(name,department,gender,basic_pay,deductions,taxable_pay,tax,net_pay,start) VALUES
    -> ('Terisa','Marketing','F',3000000.00,1000000.00,2000000.00,5000000.00,1500000.00,'2018-01-03');
```
### view payroll_data
```
SELECT *FROM employee_payroll;
```