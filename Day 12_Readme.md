Today's Question:

A collector wants to identify the top 3 snow globes with the highest number of figurines. Write a query to rank them and include their globe_name, number of figurines, and material.

Table name: snow_globes

globe_id	globe_name	volume_cm3	material
1	Winter Wonderland	500	Glass
2	Santas Workshop	300	Plastic
3	Frozen Forest	400	Glass
4	Holiday Village	600	Glass
Table name: figurines

figurine_id	globe_id	figurine_type
1	1	Snowman
2	1	Tree
3	2	Santa Claus
4	2	Elf
5	2	Gift Box
6	3	Reindeer
7	3	Tree
8	4	Snowman
9	4	Santa Claus
10	4	Tree
11	4	Elf
12	4	Gift Box


```sql
select
    n.globe_id,
    n.globe_name,
    n.material,
    count(f.globe_id) as number_of_figurines
from snow_globes n
join figurines f
    on n.globe_id = f.globe_id
group by 1, 2, 3
order by 4 desc
limit 3
```