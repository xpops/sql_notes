```zsh
mysql -u root -p
use [database_name]
```

```sql
-- Before entry is inserted into employee table, insert the added entry's first_name into trigger_test table.
DELIMITER $$  
CREATE  
    TRIGGER my_trigger BEFORE INSERT  
    ON employee  
    FOR EACH ROW BEGIN  
        INSERT INTO trigger_test VALUES(NEW.first_name);  
    END$$  
DELIMITER ;
```
Automates things (do ~ when ~)

What's up with the `DELIMITER`?
- Allow us to use `$$` instead of `;` as the delimiter.
- Why? Since we have to put `;` in the trigger.

```sql
-- Can use if-else block!
DELIMITER $$  
CREATE  
    TRIGGER my_trigger_2 BEFORE INSERT  
    ON employee  
    FOR EACH ROW BEGIN  
        IF NEW.sex = 'M' THEN  
            INSERT INTO trigger_test VALUES('added male employee');  
        ELSEIF NEW.sex = 'F' THEN  
            INSERT INTO trigger_test VALUES('added female');  
        ELSE  
            INSERT INTO trigger_test VALUES('added other employee');  
        END IF;  
    END$$  
DELIMITER ;
```

To delete:
```sql
DROP TRIGGER trigger_name;
```
