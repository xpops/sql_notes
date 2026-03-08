### Inner Join
```sql
-- Find all branches and the names of their managers  
SELECT employee.emp_id, employee.first_name, branch.branch_name  
FROM employee  
JOIN branch  -- order doesn't matter in inner joins
ON employee.emp_id = branch.mgr_id;
```
![[Pasted image 20260307223021.png]]
### Left Join
```sql
SELECT employee.emp_id, employee.first_name, branch.branch_name  
FROM employee  
LEFT JOIN branch  -- order matters here
ON employee.emp_id = branch.mgr_id;
```
![[Pasted image 20260307223443.png]]

> [!caution]
> What happens if the order is switched?

```sql
SELECT employee.emp_id, employee.first_name, branch.branch_name  
FROM branch  
LEFT JOIN employee
ON employee.emp_id = branch.mgr_id;
```
![[Pasted image 20260307223642.png]]
Actually, switched-order left join is equivalent to right join (rarely used)