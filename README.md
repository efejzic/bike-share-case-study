# Cyclistic Case Study
How Does a Bike-Share Navigate Speedy Success?

Introduction

In 2016, Cyclistic launched a successful bike-share offering in Chicago that has become a popular form of travel. Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. 
-
Cyclistic’s financial analytics have observed that annual members are much more profitable than casual riders and concluded that maximizing the number of annual members will be key to future growth. The purpose of this case study is to analyze data over a 12-month period to design a marketing strategy aimed at converting casual riders into annual members.


Identifying the business task


Cyclistic has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime. The majority of riders opt for traditional bikes; about 8% of riders use the assistive options inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. Cyclistic users are more likely to ride for leisure, but about 30% use them to commute to work each day. Customers who purchase single-ride or full-day passes are referred to as casual riders, while customers who purchase annual memberships are Cyclistic members. 

In order to design effective marketing strategies, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. 


Our business task at hand is to answer:

 
How do annual members and casual riders use Cyclistic bikes differently?

In this presentation I will:
Present trends after analyzing data for 2021 and provide a summary of my analysis
Document any cleaning and data manipulation
Showcase visualizations and key findings
And present recommendations based on my analysis 

Stakeholders
Primary stakeholders: The director of marketing Lily Moreno and Cyclistic executive team.

Secondary stakeholders: Cyclistic marketing analytics team

Data sources

Data source for this case study is publicly available information: 12 Month (Jan 2021 to Dec 2021) of Cyclistic trip Data from Motivate International Inc: (https://www.divvybikes.com/system-data)
I am using SQL for data cleaning and transformation and Tableau Public for data visualization. This data source is ROCCC compliant.

Reliable – Data is internal. Chicago Department of Transportation (CDOT), city program responsible for Divvy.
Original – Motivate International Inc, which operates the City of Chicago’s Divvy bicycle sharing service.
Comprehensive – Data contains 13 columns of extensive information to review including stations, ride id, & bike type.
Current – Data is collected in 2021.
Cited – Data is cited with license agreement

No identifiable patient information is documented in this dataset.

Limitations include NULL values, missing start and end station names in some datasets, and it is not an option to connect pass purchases to credit card numbers to determine if casual riders live in the Cyclistic service area or if they have purchased multiple single passes due to privacy concerns.


Data Analysis process: 

_________________________________________
Ask

How do annual members and casual riders use Cyclistic bikes differently?
_______________________________________
Prepare 

Data source for this case study is publicly available information: 12 Month (Jan 2021 to Dec 2021) of Cyclistic trip Data from Motivate International Inc: data source link with license.
I am using SQL for data cleaning and transformation and Tableau Public for data visualization. This data source is ROCCC compliant.

Reliable – Data is internal. Chicago Department of Transportation (CDOT), city program responsible for Divvy.
Original – Motivate International Inc, which operates the City of Chicago’s Divvy bicycle sharing service.
Comprehensive – Data contains 13 columns of extensive information to review including stations, ride id, & bike type.
Current – Data is collected in 2021.
Cited – Data is cited with license agreement

No identifiable patient information is documented in this dataset.

Limitations include NULL values, missing start and end station names in some datasets, and it is not an option to connect pass purchases to credit card numbers to determine if casual riders live in the Cyclistic service area or if they have purchased multiple single passes due to privacy concerns.


_____________________________________
Process

- Download 12 .zip files for each each month in 2021 from the Cyclistic Case Study dataset and convert them to .csv files.
- Upload each .csv file into a storage bucket labeled 2021_bikeshare.
- New table for each individual file into a dataset titled bikeshare_2021_dataset.
- After I’ve imported my dataset, I moved on to tidying my data. I merged all my tables together into a data frame called "union_df" using UNION ALL to make it easier to work with and prepare for analysis.
- Dataset has 13 columns and 5,594,410 rows.

(DATASET MONTHNAME_2021 VISUAL)
![image](https://user-images.githubusercontent.com/119814593/214117424-da462e40-7912-423a-a2c4-9e8cdf57d726.png)

  TABLE SCHEMA: union_df 

![image](https://user-images.githubusercontent.com/119814593/214117986-78395871-0e72-4a3a-8759-1f2d2bc15795.png)

(ROWS VISUAL)
![image](https://user-images.githubusercontent.com/119814593/214118078-06c9bca6-f8fa-4713-af51-e6ecc7f1a915.png)

 TABLE: union_df - assigning numerics to day of week, concat to merge stations, and ride_length (in minutes) column created

(CODE VISUAL)
![image](https://user-images.githubusercontent.com/119814593/214118658-a5cbf3c2-4334-4693-b25a-5ead21633ade.png)

--CALCULATING SIZE OF DATASET 
--TOTAL TRIPS = 5,595,063

  New temp table created labeled union_RL for later analysis. Includes 6 columns: 

(union_RL schema visual)

![unionm](https://user-images.githubusercontent.com/119814593/214119381-ab5f5a24-5ac5-42fa-b726-1bf2acbe1c22.png)

  union_RL ; filtering out negative values under ride_length column
  
(NEGATIVE VALUES)
 
 ![image](https://user-images.githubusercontent.com/119814593/214121598-9e54c94a-42fa-49b8-97ff-8d1f24302765.png)

  Organizing by ascending and deleting negatives rows
  
  (CODE VISUAL)
  
  ![rl](https://user-images.githubusercontent.com/119814593/214124469-cc084648-5cf4-45ab-a34d-1c46901eb522.png)
  
- This statement removed 85,233 rows from union_RL.


  union_RL COUNT
  
 TOTAL: 5,509,830


  union_RL - ride_id duplicate count
 
 (COUNT DUP CODE)
 
 ![duplicates](https://user-images.githubusercontent.com/119814593/214128151-3f28bc1b-e983-46ed-97ad-af704acdfb26.png)
 
 union_RL concatenated route + count of appearance
 
 ![station](https://user-images.githubusercontent.com/119814593/214133123-b0418200-793e-4843-8b6f-081c47280e40.png)



Analyze
_____________________

--IDENTIFYING NULLS (ride_id,rideable_type,started_at,ended_at,member_casual,ride_length for analyis ONLY)
--THERE IS NONE

(CODE VISUAL)

![nulls](https://user-images.githubusercontent.com/119814593/214141945-572b4e5c-6c6a-47d9-8d23-ed5e7f94e21a.png)

--# of rides per bike type

![member rides](https://user-images.githubusercontent.com/119814593/214147784-c9207983-9529-41c2-8c9d-fe338e24a16c.png)

--# of member vs casual rides

![row](https://user-images.githubusercontent.com/119814593/214148079-452f1c39-d317-414b-b2c2-74ba6195f741.png)

----Total, AVG, Max Duration of Casual & Member Types

![jdpm](https://user-images.githubusercontent.com/119814593/214148841-9c7e338f-758d-464a-ac5c-e499f1210bec.png)

--# of user types per month in 2021

![month](https://user-images.githubusercontent.com/119814593/214149645-9c7a7e0b-6fbf-4ff4-b7c6-d7dfd5ce7540.png)

--# of user type rides per weekday

![week](https://user-images.githubusercontent.com/119814593/214150212-168a77a1-48b8-464a-8752-7644bf50767c.png)

--top 20 most popular routes

![rides](https://user-images.githubusercontent.com/119814593/214151812-43718964-9c72-4cf7-9e1c-610e39b471c5.png)


Act
_____________________
