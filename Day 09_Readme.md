A community is hosting a series of festive feasts, and they want to ensure a balanced menu. Write a query to identify the top 3 most calorie-dense dishes (calories per gram) served for each event. Include the dish_name, event_name, and the calculated calorie density in your results.

Table name: events

event_id	event_name
1	Christmas Eve Dinner
2	New Years Feast
3	Winter Solstice Potluck
Table name: menu

dish_id	dish_name	event_id	calories	weight_g
1	Roast Turkey	1	3500	5000
2	Chocolate Yule Log	1	2200	1000
3	Cheese Fondue	2	1500	800
4	Holiday Fruitcake	3	4000	1200
5	Honey Glazed Ham	2	2800	3500


```sql
with cte as (
select
    e.event_name,
    m.dish_name,
    (m.calories / m.weight_g) as valu,
    row_number () over (partition by event_name order by (m.calories / m.weight_g) desc) as calo
from events e
join menu m
    on e.event_id = m.event_id
)

select 
    dish_name,
    event_name,
    valu as calorie_density
from cte
where calo < 4
```