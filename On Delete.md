Let's say an employee is deleted. What happens to the `branch.mgr_id`, which has been a foreign key that references that employee?
### Option 1: SET NULL
```sql
CREATE TABLE branch (  
    branch_id INT PRIMARY KEY,  
    branch_name VARCHAR(40),  
    mgr_id INT,  
    mgr_start_date DATE,  
    FOREIGN KEY(mgr_id) REFERENCES employee(emp_id) ON DELETE SET NULL  
);
```
*Simply set `branch.mgr_id` to null.*
(In this case, absence of a manager doesn't mean the branch is gone.)
### Option 2: CASCADE
```sql
CREATE TABLE branch_supplier (  
    branch_id INT,  
    supplier_name VARCHAR(40),  
    supply_type VARCHAR(40),  
    PRIMARY KEY (branch_id, supplier_name),  
    FOREIGN KEY (branch_id) REFERENCES branch(branch_id) ON DELETE CASCADE
);
```
*Delete the whole affected row.*
(In this case, branch_id is a primary key, which cannot be null.)