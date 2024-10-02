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
