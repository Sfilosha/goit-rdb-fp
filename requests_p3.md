select
e.entity_name,
e.entity_code,
floor(avg(data.number)) as avg_rabies,
floor(min(data.number)) as min_rabies,
floor(max(data.number)) as max_rabies,
floor(sum(data.number)) as sum_rabies
from data
join entities e on data.entity_id = e.id
join diseases d on data.disease_id = d.id
where d.disease_name = "rabies"
and data.number is not null
group by e.entity_name, e.entity_code
order by avg_rabies desc
limit 10;
