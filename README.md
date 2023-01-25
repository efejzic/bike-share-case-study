## 📍 Bike Share Case Study 🚲 🚲 🚲

🔹 **_Introduction_**  

In 2016, Cyclistic launched a successful bike-share offering in Chicago that has become a popular form of travel. Until now, Cyclistic's marketing strategy relied on building general awareness and appealing to broad consumer segments.

Cyclistic’s financial analytics have observed that annual members are much more profitable than casual riders and concluded that maximizing the number of annual members will be key to future growth. **The purpose of this case study is to analyze data over a 12-month period to design a marketing strategy aimed at converting casual riders into annual members.**

🔹 **_Identifying the business task_** 


Cyclistic has grown to a fleet of **5,824 bicycles** that are geotracked and locked into a network of **692 stations** across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime. The majority of riders opt for traditional bikes; about **8%** of riders use the assistive options inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. Cyclistic users are more likely to ride for leisure, but about **30%** use them to commute to work each day. Customers who purchase single-ride or full-day passes are referred to as _casual riders_, while customers who purchase annual memberships are _Cyclistic members_. 

In order to design effective marketing strategies, the marketing analyst team needs to better understand _**how** annual members and casual riders differ, **why** casual riders would buy a membership, and **how** digital media could affect their marketing tactics._


## 💡 Our business task at hand is to answer:

 
**How do annual members and casual riders use Cyclistic bikes differently?**

In this presentation I will:

 〰️ Document any cleaning and data manipulation

 〰️ Present trends after analyzing data for 2021 and provide a summary of my analysis

 〰️ Showcase visualizations and key findings

 〰️ And present recommendations based on my analysis 

🔹 _**Stakeholders**_

**Primary stakeholders:** The director of marketing **Lily Moreno** and **Cyclistic executive team** who decides whether to approve the
recommended marketing program.

**Secondary stakeholders:** **Cyclistic marketing analytics team**, my team who are responsible for collecting, analyzing, and
reporting data that helps guide Cyclistic marketing strategy.


## 🔗 Data Analysis process: 

🔘 **Ask**

How do annual members and casual riders use Cyclistic bikes differently?

🔘 **Prepare**


🔹 _**Data sources**_
 
🏳 Data source for this case study is publicly available information: 12 Month (Jan 2021 to Dec 2021) of Cyclistic trip Data from Motivate International Inc: (https://www.divvybikes.com/system-data)
I am using SQL for data cleaning and transformation and Tableau Public for data visualization. This data source is **ROCCC** compliant.

**Reliable** – Data is internal. Chicago Department of Transportation (CDOT), city program responsible for Divvy.

**Original** – Motivate International Inc, which operates the City of Chicago’s Divvy bicycle sharing service.

**Comprehensive** – Data contains 13 columns of extensive information to review including stations, ride id, & bike type.

**Current** – Data is collected in 2021.

**Cited** – Data is cited with license agreement

No identifiable patient information is documented in this dataset.

**_Limitations_** include NULL values, missing start and end station names in some datasets, and it is not an option to connect pass purchases to credit card numbers to determine if casual riders live in the Cyclistic service area or if they have purchased multiple single passes due to privacy concerns.


_____________________________________
🔘 **Process**

- Download 12 .zip files for each each month in 2021 from the Cyclistic Case Study dataset and convert them to .csv files.
- Upload each .csv file into a storage bucket labeled 2021_bikeshare.
- New table for each individual file into a dataset titled bikeshare_2021_dataset.
- After I’ve imported my dataset, I moved on to tidying my data. I merged all my tables together into a data frame called **"union_df"** using UNION ALL to make it easier to work with and prepare for analysis.
- Dataset has **13 columns** and **5,594,410 rows**.

![1](https://user-images.githubusercontent.com/119814593/214396522-afdb051c-fdd1-447d-aef4-ecae158fde55.jpg)

_Table schema: **union_df**_

![2 (1)](https://user-images.githubusercontent.com/119814593/214397075-6ed30271-6471-40e0-b1ed-02d5ff74e093.jpg)

_Rows visual_

![image](https://user-images.githubusercontent.com/119814593/214118078-06c9bca6-f8fa-4713-af51-e6ecc7f1a915.png)

➡️ _TABLE:_ **union_df** - assigning numerics to day of week, concat to merge stations, and ride_length (in minutes) column created

_Code visual_

![4](https://user-images.githubusercontent.com/119814593/214397896-ebd8a930-eee8-413b-9ca6-9efd58a9a31f.jpg)


--**CALCULATING SIZE OF DATASET** 

--_Total trips_ = **5,595,063**


 ➡️ New temp table created labeled **union_RL** for later analysis. Includes **6** columns: 
 

_Table schema: **union_RL**_

![unionm](https://user-images.githubusercontent.com/119814593/214119381-ab5f5a24-5ac5-42fa-b726-1bf2acbe1c22.png)

_Organizing by ascending and deleting negatives rows_
  
_Negative values_

![1 (1)](https://user-images.githubusercontent.com/119814593/214410037-d71dd1e9-4680-4aad-8e55-575ffb0095dd.jpg)
  
_Code visual_
  
  ![rl](https://user-images.githubusercontent.com/119814593/214124469-cc084648-5cf4-45ab-a34d-1c46901eb522.png)
  
- This statement removed _85,233_ rows from **union_RL**

--_Calculating size count: **union_RL**_

--_Total:_ **5,509,830**

_Column name ride_id duplicate count check_

_Code visual_

 ![duplicates](https://user-images.githubusercontent.com/119814593/214128151-3f28bc1b-e983-46ed-97ad-af704acdfb26.png)
 
_**union_RL** concatenated route + count of appearance_
 
 ![station](https://user-images.githubusercontent.com/119814593/214133123-b0418200-793e-4843-8b6f-081c47280e40.png)



🔘 **Analyze**

- Identifying nulls (ride_id,rideable_type,started_at,ended_at,member_casual,ride_length for analyis ONLY)

- There is none

_Code visual_

![nulls](https://user-images.githubusercontent.com/119814593/214141945-572b4e5c-6c6a-47d9-8d23-ed5e7f94e21a.png)

--# of rides per bike type

![member rides](https://user-images.githubusercontent.com/119814593/214147784-c9207983-9529-41c2-8c9d-fe338e24a16c.png)

--# of member vs casual rides

![row](https://user-images.githubusercontent.com/119814593/214148079-452f1c39-d317-414b-b2c2-74ba6195f741.png)

----Total, AVG, Max Duration of Casual & Member Types

![jdpm](https://user-images.githubusercontent.com/119814593/214148841-9c7e338f-758d-464a-ac5c-e499f1210bec.png)

--# of user types per month in 2021

![2 (1)](https://user-images.githubusercontent.com/119814593/214410639-c35ab6f5-35ff-4153-a22d-fc7b5bc7b583.jpg)

--# of user type rides per weekday

![week](https://user-images.githubusercontent.com/119814593/214150212-168a77a1-48b8-464a-8752-7644bf50767c.png)

--top 20 most popular routes

![3](https://user-images.githubusercontent.com/119814593/214410996-da848645-4c58-45cd-8313-62399e32a9b6.jpg)


➡️ **_Visualizations: Tableau (link)_**


🔘 **Act**

