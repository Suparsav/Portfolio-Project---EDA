
# Project Title

A brief description of what this project does and who it's or

---
# **Table of Contents**
---

**1.** [**Introduction**](#Section1)

**2.** [**Problem Statement**](#Section2)<br>

**3.** [**Installing & Importing Libraries**](#Section3)<br>
  - **3.1** [**Installing Libraries**](#Section31)
  - **3.2** [**Upgrading Libraries**](#Section32)
  - **3.3** [**Importing Libraries**](#Section33)

**4.** [**Data Acquisition & Description**](#Section4)<br>
  - **4.1** [**Data Description**](#Section41)
  - **4.2** [**Data Information**](#Section42)

**5.** [**Data Pre-Profiling**](#Section5)<br>

**6.** [**Data Cleaning**](#Section6)<br>

**7.** [**Data Post-Profiling**](#Section7)<br>

**8.** [**Exploratory Data Analysis**](#Section8)<br>
 - **8.1** [**Top 10 Cities Of US Having Maximum Accident.**](#Section81)
  - **8.2** [**Density of High Accident city and low accident city?**](#Section82)
  - **8.3** [**At what time during the day accidents are more?**](#Section83)
  - **8.4** [**How do different environmental factors affect the car accidents differently?**](#Section84)
  - **8.5** [**What time during the season/month are accidents highest?**](#Section85)
  - **8.6** [**Which time zone has highest no of accidents?**](#Section86)
  - **8.7** [**What is the yearly trend of accidents occuring?**](#Section87)
  - **8.8** [**Sevierty Of accidents with respect to the weather condition ?**](#Section88)
  - **8.9** [**Frequency of accident with respect to street,airportcode,zipcode,city,country,state?**](#Section89)
  - **8.10** [**Accidents hotspot streets according to latitude and logitude By taking 20% of the actual dataframe**](#Section810)
  - **8.11** [**Accidents Sevierity with respect to various enironmental factors?**](#Section811)
**9.** [**Summary and **Conclusion****](#Section9)<br>
  - **9.1** [**Actionable Insights**](#Section92)

---

# **1. Introduction**
---
- The **economic and societal impact** of traffic accidents cost U.S. citizens **hundreds of billions of dollars every year.**
- A large part of **losses** is **caused** by a **small number of serious accidents.**
- This is a countrywide **car accident dataset**, which covers **49 states of the USA**. The accident data are collected from **February 2016 to Dec 2021**

- **Accident analysis** is carried out in order to **determine** the cause or causes of an accident (that can result in single or multiple outcomes).
- The **proactive approach**, one of the two main approaches for dealing with traffic safety problems, focuses on **preventing potential unsafe road** conditions from occurring in the first place.

-  To **prevent** further accidents of a similar kind. It is part of accident investigation or incident investigation.
- If we can **identify the patterns** of how these serious accidents happen and the key factors, we might be able to **implement well-informed actions** and **better allocate financial and human resources**.


- By **analyzing** the accident data we can prevent accidents by introducing **new speed limits**. 

- Also By **analyzing** we can **recommend smart traffic surveliance system** for minimising the risk of accidents due to traffic lighs issue.

- US-Accidents can be used for numerous applications such as **real-time accident prediction**, studying **accident hotspot locations**, casualty analysis and extracting cause and effect rules to **predict accidents**, or studying the **impact of precipitation or other environmental stimuli on accident occurrence**.

---

# **2. Problem Statement**
---

- The main purpose of analyzing the data within this dataset, is to first fully understand what is going on. 

- US car accidents; causality analysis; the environmeantla casue behind car accidents; the traffic behavior and accidents during COVID-19.

- How do different environmental factors affect the car accidents differently? Does COVID-19 have any impact on traffic behavior and accidents?

- What is the current trend of yearly car accidents?

- What times are accidents most likely to occur within a day? What about weekly? Yearly?


- What time during the season/month are accidents highest?

- What is the percentage of accident occurances during the day? How about during the night?
- What are the actionable Insights we can gather from Dataset.

---

# **3. Installing & Importing Libraries**
---
<a name = Section31></a>
### **3.1 Installing Libraries**
!pip install -q datascience                                           
!pip install opendatasets

!pip install pandas-profiling==3.2.0

!pip install visions==0.7.4

!pip install markupsafe==2.0.1 


### **3.2 Upgrading Libraries**

- **After upgrading** the libraries, you need to **restart the runtime** to make the libraries in sync. 

- Make sure not to execute the cell above (3.1) and below (3.2) again after restarting the runtime.

!pip install -q --upgrade yellowbrick

!pip install opendatasets --upgrade --quiet            


### **3.3 Importing Libraries**


import pandas as pd 

import numpy as np

import matplotlib.pyplot as plt

import seaborn as sns

import opendatasets as od

from pandas_profiling import ProfileReport

import plotly.graph_objs as go  

import calendar

import folium

from folium.plugins import HeatMap

from collections import Counter

import warnings

warnings.filterwarnings("ignore")




---
# **4. Data Acquisition & Description**
---

- This dataset is obtained from a survey in 2014.

- It describes the attitudes towards mental health and frequency of mental health disorders in the tech workplace.

| Records | Features | Dataset Size |
| :-- | :-- | :-- |
| 2845342  | 47 | 773.4+ MB| 


| Id | Features | Description |
| :-- | :--| :--| 
|01|**ID**|This is a unique identifier of the accident record.|
|02|**Severity**|Shows the severity of the accident, a number between 1 and 4, where 1 indicates the least impact on traffic (i.e., short delay as a result of the accident) and 4 indicates a significant impact on traffic (i.e., long delay).| 
|03|**Start_Time**|Shows start time of the accident in local time zone.|
|04|**End_Time**|Shows end time of the accident in local time zone. End time here refers to when the impact of accident on traffic flow was dismissed.|
|05|**Start_Lat**|Shows **latitude** in GPS coordinate of the start point.|
|06|**Start_Lng**|Shows **longitude** in GPS coordinate of the start point.Shows longitude in GPS coordinate of the start point.|
|07|**End_Lat**|Shows **latitude** in GPS coordinate of the end point.|
|08|**End_Lng**|Shows **longitude** in GPS coordinate of the end point.|
|09|**Distance(mi)**|The length of the road extent affected by the accident.|
|10|**Description**|Shows natural language description of the accident.|
|11|**Number**|Shows the street number in address field.|
|12|**Street**|Shows the street name in address field.|
|13|**Side**|Shows the relative side of the street (Right/Left) in address field.|
|14|**City**|Shows the city in address field.|
|15|**County**|Shows the county in address field.|
|16|**State**|Shows the state in address field.|
|17|**Zipcode**|Shows the zipcode in address field.|
|18|**Country**|Shows the country in address field.|
|19|**Timezone**|Shows timezone based on the location of the accident (eastern, central, etc.).|
|20|**Airport_Code**|Denotes an airport-based weather station which is the closest one to location of the accident.|
|21|**Weather_Timestamp**|Shows the time-stamp of weather observation record (in local time).|
|22|**Temperature(F)**|Shows the temperature (in Fahrenheit).|
|23|**Wind_Chill(F)**|Shows the wind chill (in Fahrenheit).|
|24|**Humidity(%)**|Shows the humidity (in percentage).|
|25|**Pressure(in)**|Shows the air pressure (in inches).|
|26|**Visibility(mi)**|Shows visibility (in miles).|
|27|**Wind_Direction**|Shows wind direction.|
|28|**Wind_Speed(mph)**|Shows wind speed (in miles per hour).|
|29|**Precipitation(in)**|Shows precipitation amount in inches, if there is any.|
|30|**Weather_Condition**|Shows the weather condition (rain, snow, thunderstorm, fog, etc.)|
|31|**Amenity**|A POI annotation which indicates presence of amenity in a nearby location.|
|32|**Bump**|A POI annotation which indicates presence of speed bump or hump in a nearby location.|
|33|**Crossing**|A POI annotation which indicates presence of crossing in a nearby location.|
|34|**Give_Way**|A POI annotation which indicates presence of give_way in a nearby location.|
|35|**Junction**|A POI annotation which indicates presence of junction in a nearby location.|
|36|**No_Exit**|A POI annotation which indicates presence of no_exit in a nearby location.|
|37|**Railway**|A POI annotation which indicates presence of railway in a nearby location.	|
|38|**Roundabout**|A POI annotation which indicates presence of roundabout in a nearby location.|
|39|**Station**|A POI annotation which indicates presence of station in a nearby location.|
|40|**Stop**|A POI annotation which indicates presence of stop in a nearby location.|
|41|**Traffic_Calming**|A POI annotation which indicates presence of traffic_calming in a nearby location.|
|42|**Traffic_Signal**|A POI annotation which indicates presence of traffic_signal in a nearby loction.|
|43|**Turning_Loop**|A POI annotation which indicates presence of turning_loop in a nearby location.|
|44|**Sunrise_Sunset**|Shows the period of day (i.e. day or night) based on sunrise/sunset.|
|45|**Civil_Twilight**|Shows the period of day (i.e. day or night) based on civil twilight.|
|46|**Nautical_Twilight**|Shows the period of day (i.e. day or night) based on nautical twilight.|
|47|**Astronomical_Twilight**|Shows the period of day (i.e. day or night) based on astronomical twilight.|


- **Note:** For easy reference I am  sharing a <a href="https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents/download">**link**</a> which you can keep handy while analyzing the data.If opendataset don't work .You can Download DataSet from this Link and then use it to run it from local system drive.

#If this dont't Work you can downlaod dataset from link provided above and use dataset and run it from local system drive.
download_url = 'https://www.kaggle.com/sobhanmoosavi/us-accidents'
od.download(download_url)


---
# **9. Summary and Conclusion**
---


- Miami is the city with the most number of car accidents.
- The Temperature is almost normally distributed.
- Wind Speed, Visibility, Precipitation all follow a right skewed distribution.
- Humidity on the other hand follows a left skewed distribution.
- There are 127 types of weather condition in the dataset.
- There are 137 data rows that have no city mentioned.
- The severity of a car accident is described by a scale from 1 to 4. where 1 indicates the least impact on traffic (i.e., short delay as a result of the accident) and 4 indicates a significant impact on traffic (i.e., long delay).
- 89% of the car accidents are considered a severity of 2. Only 0.9% of car accidents have a severity score of 1.
- Temperature does not have much of an impact on the severity of the accident. However, extreme weather temperature, like below - -50 F degree, usually only causes accidents that have a severity score of 2.
- Car accidents are most likely to happen at the temperature around 50-80 F degree.
- The number of car accidents increases as the humidity increases. The majority of accidents due to humidty has a severity score of 2.
- Severe car accidents are mostly accompanied with a low visibility (below 50 mi). Meanwhile, The least severe car accidents tend to have the poorest visibility (below 20 mi).
- Precipitation and the number of accidents have a simple inverse relationship. The heavier the rain, the fewer the number of car accidents.
- Precipitation does not affect the severity of the accidents as much as the previous factors. However, during heavy rain(25inch), accidents mostly have a severity score of 2.
- Wind Speed affects the severity of the accidents almost equally.
- 76% of the accidents occur on fairly normal weather conditions (Fair, Mostly Cloudy, Cloudy, Partly Cloudy, Clear).
- 76% of the accident occur during the day
- Only 26% of the accidents occured close to any of the road elements considered.
- Junctions are the road element where occur more accidents with 9.9%
- Severity 2 is the most recurrent with 89% of the accidents.
- Accidents with bad weather doesn't have a higher severity.
- Accidents are not more frequent on bad weather conditions.
- A high percentage of accidents occur between 15 to 18. Probably people’r hurry to get home. The next highest one is around 6 to 8.
- On weekends the number of accidents happened at 0 o’clock is higher than weekdays’.
- Weekday accidents distribution is almost the same as the overall accidents distribution.
- For every year from 2016-2021, the number of reported car accidents increases. 2021 has the most number of car accidents.
- Temperature of accident trends of every year are stable.
- For every year from 2016-2021, humidity trends are stable except during Oct 2019.
- 2017 being the year with the most precipitation has fewer accidents than 2021 being the year with moderate precipitation.
- 2021 still has the most number of accidents at every hour. Nevertheless, this may not reflect the reality because 2021 has - significantly more reported accidents than in 2016 or previous year. Interestingly, the pattern of each year looks almost - identical. Each year's line is just higher than the previous one.
- During covid 19 months, the number of car accidents has increased significantly. Feb 2020 is the start of COVID.
- During covid 19 months, though most jobs become work from home. The number of car accidents happened at every hour has the same pattern as previous years though much higher.
- Cities with the most Covid-19 cases have more car accidents.


### **9.1 Actionable Insight**

- There should be functional traffic lights as we have seen in data most of them are not working.
- Majority accidents happen because of not presence of roundabout, bump , crossing etc. 
- Roundabout,Crossing , Speedlimit sings Should be repaired and re-printed with new speed limits in an accident hotspot areas.
- Smaller City need to have smart surveillance system.
- Smart surveillance system help in this as it could recognize where there is more traffic so it could increase the green light time by 15-20 sec more then that of standard limit.
- It could reduce the speed by 10-15mph when the weather forecast it to be cloudy and rainy and in low visibilty conditions.
- Heavy penalty should be imposed on people rushing their cars in city traffic speed limits and also who were using cell phones while driving
- As smaller city seems to have less no of accidents (< 100 accidents) but overall they consist of 74.7% of total accident happen in US. 

- During rush hour there should be enough green lights given to the majority of straight lanes which are connected to majority of offices.
- .
- There should be proper warning system to the people over radio/FM when there is prediction of hevay snow or hailstroms.
- Most of the people drive on all terrain tyres so whever there is chances of snow/hailstrom proper warning should be given over Radio/FM so that people should be aware about it.
- Government should encourage vehicles proving good safety and have scored > (4-5 stars) in Global NCAP/ EuroNCAP.
- Proper Bump/speedbraked should be made as by seeing bump/speedbraker people tends to slow down their vehicle which can also led to less accidents. 
- As in slow speed it is much more likely to avoid accident.
