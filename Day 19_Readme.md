Scientists are studying the diets of polar bears. Write a query to find the maximum amount of food (in kilograms) consumed by each polar bear in a single meal December 2024. Include the bear_name and biggest_meal_kg, and sort the results in descending order of largest meal consumed.

Table name: polar_bears

bear_id	bear_name	age
1	Snowball	10
2	Frosty	7
3	Iceberg	15
Table name: meal_log

log_id	bear_id	food_type	food_weight_kg	date
1	1	Seal	30	2024-12-01
2	2	Fish	15	2024-12-02
3	1	Fish	10	2024-12-03
4	3	Seal	25	2024-12-04
5	2	Seal	20	2024-12-05
6	3	Fish	18	2024-12-06



```sql
with cte as (
select
    p.bear_name,
    l.food_type,
    food_weight_kg,
    row_number() over (partition by bear_name order by food_weight_kg desc) as rn
from polar_bears p
join meal_log l
    on p.bear_id = l.bear_id
where
    l.date between '2024-12-01' and '2024-12-31'
)

select
    bear_name,
    food_weight_kg as biggest_meal_kg
from cte
where rn = 1
order by 2 desc
```