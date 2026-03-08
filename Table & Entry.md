## Table
### Create Table
```SQL
CREATE TABLE student (
	student_id INT AUTO_INCREMENT,
	name VARCHAR(20) NOT NULL,
	major VARCHAR(20) DEFAULT 'undecided',
	PRIMARY KEY(student_id)
);
```
#### Keywords
- `NOT NULL`: attribute cannot be null
- `UNIQUE`: attribute cannot contain duplicate
- `DEFAULT 'something'`: attributes defaults to something if not declared
- `AUTO_INCREMENT`: if not declared, highest index + 1
### Describe Table
```sql
DESCRIBE student;
```
Outputs the description of the table (fields, key, etc.)

### Drop Table
```sql
DROP TABLE student;
```

### Alter Table
```sql
ALTER TABLE student ADD gpa DECIMAL(3, 2);
ALTER TABLE student DROP COLUMN gpa;
```

## Values

### Insert Entry
```sql
INSERT INTO student VALUES(1, 'Jack', 'Biology');

-- When some values are unknown
INSERT INTO student(student_id, name) VALUES(3, 'Claire');
```

### Get Table
```sql
SELECT * FROM student;
```

### Update Entry
```sql
-- major가 Biology인 학생들의 major를 Bio로 변환
UPDATE student  
SET major = 'Bio'  
WHERE major = 'Biology';

-- student_id 4인 학생의 minor를 Biology로 변환
UPDATE student  
SET minor = 'Biology'  
WHERE student_id = 4;

-- major 가 Biology 나 Chemistry인 학생들의 major를 Biochemistry로 변환
UPDATE student  
SET major = 'Biochemistry'  
WHERE major = 'Biology' OR major = 'Chemistry';

-- student_id 1인 학생의 name을 Tom으로, major를 Biochemistry로 변환
UPDATE student  
SET name = 'Tom', major = 'Biochemistry'  
WHERE student_id = 1;

-- (WHERE가 없으면) 모두의 major를 undecided로 변환
UPDATE student
SET major = 'undecided';
```
세미콜론을 뒤에찍으면 윗줄들까지 다 하나의 명령어로 인식됨.

### Delete Entry
```sql
-- Delete entry with student_id of 5
DELETE FROM student
WHERE student_id = 5;

-- Delete entry with name Tom AND major undecided
DELETE FROM student
WHERE name = 'Tom' AND major = 'undecided';

-- Delete every entry
DELETE FROM student
```

## Basic Queries
```sql
SELECT student.name, student.major -- Print 2 columns (name, major)
FROM student -- From table 'student'
WHERE name <> 'Kate' AND major > 'Biology' -- among whose name is not 'Kate' AND major is lexicographically later than 'Biology'
ORDER BY major, student_id DESC; -- In descending order by 1) major, 2) student_id
LIMIT 2; -- only print first 2 entries
```

```sql
WHERE name IN ('Claire', 'Kate', 'Mike') -- 이런식으로도 사용 가능
```
