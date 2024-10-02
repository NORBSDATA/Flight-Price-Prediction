# Flight Price Prediction

## Project Overview
The Flight Price Prediction analysis seeks to understand how prices of flight are affected by different varying factors. The project will uncover how prices of flight are affected by **booking to date of departure**, **number of stops**, **type and class of airline**, **source and destination** as well as **time of departure**. This analysis at the end will help travelers to make informed decision in terms of budgeting for their trips.

## Data Sources
The dataset was extracted from [kaggle](https://www.kaggle.com/datasets/shubhambathwal/flight-price-prediction/data)

## Tools Used
The analysis made use of the following tools
- Excel spreadsheet
- SQL Server
- Power Bi desktop

## Data Cleaning and Preparation
The dataset was cleaned using Excel spreadsheet and the following steps was taken to arrive at a proper cleaning of the data.
- The cells were adjusted and text unwrapped.  
- The Excel function ```=IF(E2<TIME(6,0,0),"Late Night",IF(E2<TIME(12,0,0),"Early Morning",IF(E2<TIME(17,0,0),"Morning",IF(E2<TIME(18,0,0),"Afternoon",IF(E2<TIME(21,0,0),"Evening","Night")))))``` was used to convert time to time of the day.
- Cells not needed for analysis was removed
- Find and replace function was used to replace 1-stop, non-stop and 2+stop to one, zero and two or more respectively.
- The tables were later merged together.
- Merged dataset was uploaded to SQL Server.
### Note: The dataset contained 3 tables. The original datasets was duplicated and saved on another folder before this phase 

## Exploratory Phase
The following questons were asked inorder to help uncover the truth.
- Are there changes in price if ticket is bought in just 1 or 2 days before departure?
- Is there changes in price due to departure time and arrival time?
- Does price vary with Airlines?
- How does the ticket price vary between Economy and Business class?
- Does price vary due to change in Source and Destination?

## Analysis Phase
```select *
from Clean_Dataset

select avg(price) as avg_price
from [dbo].[Clean_Dataset]
where days_left = 1


select avg(price) as avg_price
from [dbo].[Clean_Dataset]
where days_left = 2


select price
from [dbo].[Clean_Dataset]
where days_left = 2

select price
from Clean_Dataset
where days_left = 1

select distinct airline, source_city
from Clean_Dataset

select count (*) as distinctcnt
from (
select distinct airline,source_city
from Clean_Dataset
) as subq

select price, airline
from Clean_Dataset

select price,source_city, departure_time
from Clean_Dataset
where departure_time = 'Evening'
or departure_time = 'Early_Morning'
or departure_time = 'Afternoon'
or departure_time = 'Morning'
or departure_time = 'Late_Night'
or departure_time = 'Night'
order by price desc

select price,source_city, arrival_time
from Clean_Dataset
where departure_time = 'Evening'
or departure_time = 'Early_Morning'
or departure_time = 'Afternoon'
or departure_time = 'Morning'
or departure_time = 'Late_Night'
or departure_time = 'Night'
order by price desc

select price,destination_city,departure_time
from Clean_Dataset
where departure_time = 'Evening'
or departure_time = 'Early_Morning'
or departure_time = 'Afternoon'
or departure_time = 'Morning'
or departure_time = 'Late_Night'
or departure_time = 'Night'
order by price desc

select price,destination_city,arrival_time
from Clean_Dataset
where departure_time = 'Evening'
or departure_time = 'Early_Morning'
or departure_time = 'Afternoon'
or departure_time = 'Morning'
or departure_time = 'Late_Night'
or departure_time = 'Night'
order by price desc

select price
from Clean_Dataset
where class = 'Economy'

select price
from Clean_Dataset
where class = 'Business'

select price,airline
from Clean_Dataset
where airline in ('Air_India','SpiceJet','Vistara', 'GO_FIRST', 'Indigo', 'AirAsia')

select price, airline
from clean_dataset
where airline = 'Air_india'

select price
from clean_dataset
where airline = 'spicejet'

select price
from clean_dataset
where airline = 'Indigo'

select price
from clean_dataset
where airline = 'Vistara'

select price
from clean_dataset
where airline = 'Go_first'

select price
from clean_dataset
where airline = 'Air_Asia'

select trim(upper(airline)) as airline, sum(cast(price as bigint)) as totalprice
--- sum(cast(price as bigint)) helps to change from int to bigint
from Clean_Dataset
group by airline
order by totalprice desc

select airline, max(price) as maxprice
from Clean_Dataset
group by airline
order by maxprice desc

select price,stops
from Clean_Dataset
where stops = 'one'

select price, stops
from Clean_Dataset
where stops = 'two_or_more'

select price, stops
from Clean_Dataset
where stops = 'zero'
```
