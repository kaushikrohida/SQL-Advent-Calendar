Which ski resorts had snowfall greater than 50 inches?

Table name: snowfall

resort_name	location	snowfall_inches
Snowy Peaks	Colorado	60
Winter Wonderland	Utah	45
Frozen Slopes	Alaska	75


```sql
select
    resort_name
from snowfall
where
    snowfall_inches > 50
```