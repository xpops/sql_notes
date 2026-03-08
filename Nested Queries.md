```sql
-- Find names of all employees who have sold over 30,000 to a single client  
SELECT employee.first_name, employee.last_name  
FROM employee  
WHERE employee.emp_id IN (  
    SELECT works_with.emp_id  
    FROM works_with  
    WHERE works_with.total_sales > 30000  
);
```
The same IN keyword from before, but inside the parentheses we have results from another query (list of emp_id who sold more than 30000)

```sql
-- Find all clients who are handled by the branch that Michael Scott manages  
-- Assume you know Michael's ID (102)  
SELECT client.client_id, client.client_name  
FROM client  
WHERE client.branch_id = (  -- note equality here (single value)
    SELECT branch.branch_id  
    FROM branch  
    WHERE mgr_id = 102
    LIMIT 1 -- makes sure that only 1 value is returned
);
```
