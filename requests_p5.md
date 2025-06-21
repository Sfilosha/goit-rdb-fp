drop function if exists year_difference;

delimiter //

create function year_difference(year_value int)
returns int
deterministic
begin
declare start_date date;
set start_date = str_to_date(concat(year_value, '-01-01'), '%Y-%m-%d');
return timestampdiff(year, start_date, curdate());
end //

delimiter ;

select
id,
year,
year_difference(year) as years
from data;
