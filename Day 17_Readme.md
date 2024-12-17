The Grinch is planning out his pranks for this holiday season. Which pranks have a difficulty level of “Advanced” or “Expert"? List the prank name and location (both in descending order).

Table name: grinch_pranks

prank_id	prank_name	location	difficulty
1	Stealing Stockings	Whoville	Beginner
2	Christmas Tree Topple	Whoville Town Square	Advanced
3	Present Swap	Cindy Lous House	Beginner
4	Sleigh Sabotage	Mount Crumpit	Expert
5	Chimney Block	Mayors Mansion	Expert


```sql
select
    prank_name,
    location
from grinch_pranks
where
    difficulty in ('Advanced', 'Expert')
order by 1 desc, 2 desc
```