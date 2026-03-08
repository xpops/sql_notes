## Wildcards (% (any # characters), _ (one char))
```sql
SELECT *  
FROM client  
WHERE client_name LIKE '%LLC'; -- client_name ends with LLC

-- Select branch supplier whose name contains ~ Label~
SELECT *  
FROM branch_supplier  
WHERE supplier_name LIKE '% Label%';

-- Find any employee born in October  
SELECT *  
FROM employee  
WHERE birth_date LIKE '____-10-__';
-- or
SELECT *  
FROM employee  
WHERE birth_date LIKE '%-10-%'; -- year-month-date니까 hyphen을 잘 이용
```