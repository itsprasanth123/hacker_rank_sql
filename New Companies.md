- https://www.hackerrank.com/challenges/the-company/problem?isFullScreen=false


```
select c.company_code, c.founder, count(distinct e.lead_manager_code), count(distinct e.senior_manager_code), count(distinct e.manager_code), count(distinct e.employee_code) 
from Company c left join Employee e on c.company_code = e.company_code 
group by c.company_code, c.founder 
order by c.company_code asc;
```

```
SELECT DISTINCT 
    e.company_code, 
    c.founder, 
    COUNT(DISTINCT e.lead_manager_code), 
    COUNT(DISTINCT e.senior_manager_code),
    COUNT(DISTINCT e.manager_code), 
    COUNT(DISTINCT e.employee_code)
FROM 
    employee e 
LEFT JOIN
    manager m
ON 
    e.company_code = m.company_code 
LEFT JOIN 
    senior_manager sm 
ON
    e.company_code = sm.company_code 
LEFT JOIN 
    lead_manager lm 
ON 
    e.company_code = lm.company_code 
LEFT JOIN
    company c 
ON 
    e.company_code = c.company_code
GROUP BY 
    e.company_code, 
    c.founder
ORDER BY 
    company_code;


```