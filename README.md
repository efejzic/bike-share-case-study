# Cyclistic Case Study
How Does a Bike-Share Navigate Speedy Success?
Data used from Divvy Bikes (https://www.divvybikes.com/system-data) for the Capstone Project of the Google Data Analytics Professional Certificate.



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



Act
_____________________
