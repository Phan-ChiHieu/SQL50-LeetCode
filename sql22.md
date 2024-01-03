```sql
Select  teacher_id ,count(distinct subject_id ) as cnt 
From Teacher
Group By teacher_id
```