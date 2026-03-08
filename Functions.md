### COUNT
```sql
-- Find the number of employees
SELECT COUNT(emp_id)  
FROM employee;

-- Find the number of female employees born after 1970  
SELECT COUNT(emp_id)  
FROM employee  
WHERE birth_date >= '1970-01-01' AND sex = 'F';
```
### AVG
```sql
SELECT AVG(employee.salary)  
FROM employee  
WHERE sex = 'M';
```
### SUM
```sql
SELECT SUM(employee.salary)  
FROM employee;
```
### GROUP BY (aggregation)
```sql
-- Average salaries by sex
SELECT AVG(salary), employee.sex  
FROM employee  
GROUP BY sex;

-- Find the total sales of each salesman
SELECT SUM(total_sales), works_with.emp_id  
FROM works_with  
GROUP BY emp_id;
```
