![alt text](image-9.png)
![alt text](image-10.png)

```
SELECT 
    MAX(CASE WHEN occupation = 'Doctor' THEN name END) AS "Doctor",
    MAX(CASE WHEN occupation = 'Professor' THEN name END) AS "Professor", 
    MAX(CASE WHEN occupation = 'Singer' THEN name END) AS "Singer", 
    MAX(CASE WHEN occupation = 'Actor' THEN name END) AS "Actor"
    FROM(select Name , Occupation, row_number() over( partition by Occupation order by Name) as Row_num From OCCUPATIONS) as ord group by Row_num
```
- need to understand this better,

```
Select 
min(if ( Occupation='Doctor',Name,Null)) as doctor ,
min(if ( Occupation='Professor',Name,Null)) as prof ,
min(if ( Occupation='Singer',Name,Null)) as singer,
min(if ( Occupation='Actor',Name,Null)) as actor
from
(select  Name , Occupation,
row_number() over( partition by Occupation order by Name) as Row_num 
From OCCUPATIONS) as ord
group by Row_num ;

```