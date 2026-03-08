## Unions (Combining Selects)
```sql
-- Find a list of all clients & branch suppliers' names  
SELECT client.client_name, client.branch_id  
FROM client  
UNION  
SELECT branch_supplier.supplier_name, branch_supplier.branch_id  
FROM branch_supplier;  
  
-- Find a list of all money spent or earned by the company  
SELECT employee.salary  
FROM employee  
UNION  
SELECT works_with.total_sales  
from works_with;
```