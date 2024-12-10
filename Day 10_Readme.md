You are tracking your friends' New Year’s resolution progress. Write a query to calculate the following for each friend: number of resolutions they made, number of resolutions they completed, and success percentage (% of resolutions completed) and a success category based on the success percentage:
- Green: If success percentage is greater than 75%.
- Yellow: If success percentage is between 50% and 75% (inclusive).
- Red: If success percentage is less than 50%.

Table name: resolutions

resolution_id	friend_name	resolution	is_completed
1	Alice	Exercise daily	1
2	Alice	Read 20 books	0
3	Bob	Save money	0
4	Bob	Eat healthier	1
5	Charlie	Travel more	1
6	Charlie	Learn a new skill	1
7	Diana	Volunteer monthly	1
8	Diana	Drink more water	0
9	Diana	Sleep 8 hours	1


```sql
select
    friend_name,
    count(resolution) as resolution_count,
    count(Case when is_completed = 1 then 1 else null end) as resolution_completed,
    round(cast(count(Case when is_completed = 1 then 1 else null end) as float) / count(resolution) * 100, 2) as success_percentage,
    Case    
        when round(cast(count(Case when is_completed = 1 then 1 else null end) as float) / count(resolution) * 100, 2) > 75 then 'Green'
        when round(cast(count(Case when is_completed = 1 then 1 else null end) as float) / count(resolution) * 100, 2) between 50 and 75 then 'Yellow'
        else 'Red'
    end as success_category
from resolutions
group by 1
```