The Grinch tracked his weight every day in December to analyze how it changed daily. Write a query to return the weight change (in pounds) for each day, calculated as the difference from the previous day's weight.

Table name: grinch_weight_log

log_id	day_of_month	weight
1	1	250
2	2	248
3	3	249
4	4	247
5	5	246
6	6	248


```sql
select
    day_of_month,
    (weight - lag(weight) over (order by day_of_month)) as rn
from grinch_weight_log
```