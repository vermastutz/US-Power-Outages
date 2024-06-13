# US Power Outages
Project for DSC 80 at UCSD

**Authors:** Stuti Verma and Prithvi Kochhar

## Introduction

Our goal for this project, is to analyze a dataset of major power outages in the U.S. spanning from January 2000 to July 2016. The dataset is made available by Purdue University’s Laboratory for Advancing Sustainable Critical Infrastructure (LASCI), and can be accessed at [Purdue LASCI](https://engineering.purdue.edu/LASCI/research-data/outages).

The dataset provides extensive information on the outages themselves as well as geographical and climatic characteristics, electricity consumption patterns, and economic traits of the affected states.

Our analysis will progress through several key stages. Initially, we will clean the dataset and perform exploratory data analysis to understand the data's structure and trends. 

The core research question we aim to explore is: What factors contribute to the frequency and duration of major power outages across different regions in the U.S.?  This analysis is crucial as it helps in identifying the key factors influencing power outages, which can aid in improving power outage frequencies and response strategies.

The original dataset consists 1,534 rows and 57 columns, corresponding to 1,534 power outages and 57 features respectively. For this analysis, our focus will be on the following key columns:

| Column      | Description |
| :---   | ----: |
| YEAR        | The year when the outage occurred  |
| MONTH       | The month when the outage occurred     |
| U.S._STATE  | The state where the outage occurred
| CLIMATE.REGION      | The climate region of the state       |
| CLIMATE.CATEGORY   | The climate category (cold, normal, warm) during the outage |
|OUTAGE.START.DATE| The start date of the outage|
|OUTAGE.START.TIME| The start time of the outage|
|OUTAGE.RESTORATION.DATE| The restoration date of the outage|
|OUTAGE.RESTORATION.TIME| The restoration time of the outage|
|CAUSE.CATEGORY| The category of the cause of the outage (severe weather, intentional attack etc.)|
|OUTAGE.DURATION| The duration of the outage in minutes|
|CUSTOMERS.AFFECTED| The number of customers affected by the outage|
|TOTAL.CUSTOMERS| The total number of customers in the area|
|POPULATION |The population of the area|


## Data Cleaning and Exploratory Data Analysis
1. **Dropping Irrelevant Columns:**
    - The columns we dropped were: 
               - **variables**, **OBS**, **NERC.REGION**, **POSTAL.CODE**, **ANOMALY.LEVEL**, **POPPCT_URBAN**, **POPPCT_UC**,         **POPDEN_URBAN**, **POPDEN_UC**, **POPDEN_RURAL**, **AREAPCT_URBAN**, **AREAPCT_UC**, **PCT_LAND**, **PCT_WATER_TOT**, **PCT_WATER_INLAND**, **IND.CUST.PCT**, **PC.REALGSP.STATE**, **PC.REALGSP.USA**, **PC.REALGSP.REL**, **PC.REALGSP.CHANGE**, **UTIL.REALGSP**, **TOTAL.REALGSP**, **UTIL.CONTRI**, **PI.UTIL.OFUSA**, **RES.PERCEN**, **COM.PERCEN**, **IND.PERCEN**, **RES.CUST.PCT**, **COM.CUST.PCT**, **TOTAL.PRICE**, **RES.SALES**, **COM.SALES**, **IND.SALES**, **TOTAL.SALES**, **DEMAND.LOSS.MW**, **RES.PRICE**, **COM.PRICE**, **IND.PRICE**, **CAUSE.CATEGORY.DETAIL**
    - These columns were not relevant to the research question focused on the causes and characteristics of major power outages. Removing them helped streamline the dataset and focus on the important variables.
    

2. **Converting data types:**
    - OUTAGE.START.DATE and OUTAGE.RESTORATION.DATE were converted to datetime format for accurate date-time operations.
    
    -Ensuring that these columns were in the correct data types allowed for precise calculations of the duration of outages and accurate time-based analysis.
    


**Note:** We did not assess or impute the missing values during this step, so that we could impute the missingness mechanisms and dependencies later in our analysis. 

| U.S._STATE   | CLIMATE.REGION     | CLIMATE.CATEGORY   | OUTAGE.START.DATE   | OUTAGE.RESTORATION.TIME   | CAUSE.CATEGORY     |   OUTAGE.DURATION |   CUSTOMERS.AFFECTED |
|:-------------|:-------------------|:-------------------|:--------------------|:--------------------------|:-------------------|------------------:|---------------------:|
| Minnesota    | East North Central | normal             | 2011-07-01 00:00:00 | 20:00:00                  | severe weather     |              3060 |                70000 |
| Minnesota    | East North Central | normal             | 2014-05-11 00:00:00 | 18:39:00                  | intentional attack |                 1 |                  nan |
| Minnesota    | East North Central | cold               | 2010-10-26 00:00:00 | 22:00:00                  | severe weather     |              3000 |                70000 |
| Minnesota    | East North Central | normal             | 2012-06-19 00:00:00 | 23:00:00                  | severe weather     |              2550 |                68200 |
| Minnesota    | East North Central | warm               | 2015-07-18 00:00:00 | 07:00:00                  | severe weather     |              1740 |               250000 |
        
###Univariate Analysis

<iframe
  src="assets/plot1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

This histogram plot shows the number of major power outages in each climate region.
This plot reveals that certain regions experience outages more frequently. We wanted to see this relation to interpret whether regions with harsh weather conditions or older infrastructure might see a higher number of outages.
Understanding which regions are more prone to outages can help in targeting infrastructure improvements and preventative measures.

Each region consists of the following states:

| Region               | States                                                                                   |
|:----------------------|------------------------------------------------------------------------------------------|
| Central              | Tennessee, West Virginia, Indiana, Illinois, Kentucky, Ohio, Missouri                      |
| East North Central   | Minnesota, Wisconsin, Michigan, Iowa                                                      |
| Northeast            | Maryland, Pennsylvania, New Jersey, District of Columbia, Delaware, New York, Vermont, Connecticut, Massachusetts, Maine, New Hampshire |
| Northwest            | Washington, Oregon, Idaho                                                                |
| South                | Texas, Mississippi, Louisiana, Arkansas, Oklahoma, Kansas                                 |
| Southeast            | Alabama, North Carolina, South Carolina, Florida, Virginia, Georgia                        |
| Southwest            | Arizona, Utah, New Mexico, Colorado                                                      |
| West                 | California, Nevada                                                                       |
| West North Central   | Montana, Nebraska, Wyoming, North Dakota, South Dakota                                    |


Refer to the map plot below for further information on state-wise breakdown of number of power outages. 


<iframe
  src="assets/plot2univariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

This plot shows the number of outages occurring in each month across the data's timeframe (January 2000 to July 2016).
The plot allows us to interpret any seasonal trends, such as an increase in outages during winter months when storms are more frequent or during summer months when high electricity demand can lead to failures.
Identifying seasonal trends can help in preparing for periods with higher risks of outages and planning maintenance accordingly.


### Bivariate Analysis

<iframe
  src="assets/plot1bivariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

This scatter plot illustrates the relationship between the duration of power outages (in minutes) and the number of customers affected.
The scatter plot suggests a positive correlation, indicating that longer outages usually tend to impact more customers.
This trend highlights the importance of quickly restoring power to minimize the number of affected customers. It also suggests that more severe outages, which take longer to fix, tend to impact larger populations, possibly due to the complexity of the issues causing the outages.


<iframe
  src="assets/plot2bivariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

This box plot shows the distribution of average outage durations for different causes behind power outages.
The plot indicates that certain causes, such as fuel supply emergency or severe weather, lead to longer outages compared to others.
Understanding which causes result in longer outages can help prioritize resources for prevention and quicker response. For instance, if equipment failure causes longer outages, investing in better maintenance and upgrading infrastructure could reduce outage durations.

| CLIMATE.REGION     |     cold |   normal |    warm |
|:-------------------|---------:|---------:|--------:|
| Central            | 2841.27  | 2708.7   | 2413.84 |
| East North Central | 6568.79  | 5271.22  | 3022.12 |
| Northeast          | 3657.25  | 2273.96  | 4175.91 |
| Northwest          |  874.681 |  733.612 | 3063.54 |
| South              | 1969.57  | 3630.79  | 1861.4  |

This pivot table shows the average duration of outages for different climate categories and regions.
The table reveals variations in outage durations based on climate and geographical location, with some climates and regions experiencing significantly longer outages on average. For example we see that the average outage duration in the Northeast region during warm climate is comparatively high (4176 minutes).
These insights can help in developing targeted strategies for outage prevention and response. For example, regions with longer outage durations might benefit from enhanced infrastructure resilience measures.


## Assessment of Missingness


## Hypothesis Testing


## Framing a Prediction Problem


## Baseline Model


## Final Model


## Fairness Analysis

