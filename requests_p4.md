select
id,
year,
str_to_date(concat(year, '-01-01'), '%Y-%m-%d') as full_date,
curdate() as today,
timestampdiff(
year,
str_to_date(concat(year, '-01-01'), '%Y-%m-%d'),
curdate()
) as years_difference
from data;
