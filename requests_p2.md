create table entities (
id int auto_increment primary key,
entity_name varchar(255),
entity_code varchar(5),
unique(entity_name, entity_code)
);

insert into entities (entity_name, entity_code)
select distinct Entity, Code
from infectious_cases;

create table diseases (
id int auto_increment primary key,
disease_name varchar(255) unique );

create table data (
id int auto_increment primary key,
entity_id int,
disease_id int,
year int,
number float,
foreign key (entity_id) references entities(id),
foreign key (disease_id) references diseases(id)
);

insert into diseases (disease_name)
VALUES
('yaw'),
('polio'),
('guinea_worm'),
('rabies'),
('malaria'),
('hiv'),
('tuberculosis'),
('smallpox'),
('cholera');

insert into data (entity_id, disease_id, year, number)

select e.id, d.id, ic.year, ic.Number_yaws
from infectious_cases ic
join entities e on ic.entity = e.entity_name and ic.Code = e.entity_code
join diseases d on d.disease_name = 'yaw'
where ic.Number_yaws is not null and ic.Number_yaws != ''

union all

select e.id, d.id, ic.year, ic.polio_cases
from infectious_cases ic
join entities e on ic.entity = e.entity_name and ic.Code = e.entity_code
join diseases d on d.disease_name = 'polio'
where ic.polio_cases is not null and ic.polio_cases != ''

union all

select e.id, d.id, ic.year, ic.cases_guinea_worm
from infectious_cases ic
join entities e on ic.entity = e.entity_name and ic.Code = e.entity_code
join diseases d on d.disease_name = 'guinea_worm'
where ic.cases_guinea_worm is not null and ic.cases_guinea_worm != ''

union all

select e.id, d.id, ic.year, ic.Number_rabies
from infectious_cases ic
join entities e on ic.entity = e.entity_name and ic.Code = e.entity_code
join diseases d on d.disease_name = 'rabies'
where ic.Number_rabies is not null and ic.Number_rabies != ''

union all

select e.id, d.id, ic.year, ic.Number_malaria
from infectious_cases ic
join entities e on ic.entity = e.entity_name and ic.Code = e.entity_code
join diseases d on d.disease_name = 'malaria'
where ic.Number_malaria is not null and ic.Number_malaria != ''

union all

select e.id, d.id, ic.year, ic.Number_hiv
from infectious_cases ic
join entities e on ic.entity = e.entity_name and ic.Code = e.entity_code
join diseases d on d.disease_name = 'hiv'
where ic.Number_hiv is not null and ic.Number_hiv != ''

union all

select e.id, d.id, ic.year, ic.Number_tuberculosis
from infectious_cases ic
join entities e on ic.entity = e.entity_name and ic.Code = e.entity_code
join diseases d on d.disease_name = 'tuberculosis'
where ic.Number_tuberculosis is not null and ic.Number_tuberculosis != ''

union all

select e.id, d.id, ic.year, ic.Number_smallpox
from infectious_cases ic
join entities e on ic.entity = e.entity_name and ic.Code = e.entity_code
join diseases d on d.disease_name = 'smallpox'
where ic.Number_smallpox is not null and ic.Number_smallpox != ''

union all

select e.id, d.id, ic.year, ic.Number_cholera_cases
from infectious_cases ic
join entities e on ic.entity = e.entity_name and ic.Code = e.entity_code
join diseases d on d.disease_name = 'cholera'
where ic.Number_cholera_cases is not null and ic.Number_cholera_cases != ''
