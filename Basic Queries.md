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
### Distinct
```sql
SELECT DISTINCT branch_id  -- only selects distinct values
FROM employee;
```
