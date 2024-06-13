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
               =='variables'==,'OBS','NERC.REGION','POSTAL.CODE','ANOMALY.LEVEL','POPPCT_URBAN',
               'POPPCT_UC','POPDEN_URBAN','POPDEN_UC','POPDEN_RURAL','AREAPCT_URBAN','AREAPCT_UC',
               'PCT_LAND','PCT_WATER_TOT','PCT_WATER_INLAND','IND.CUST.PCT','PC.REALGSP.STATE',
               'PC.REALGSP.USA','PC.REALGSP.REL','PC.REALGSP.CHANGE','UTIL.REALGSP','TOTAL.REALGSP',
               'UTIL.CONTRI','PI.UTIL.OFUSA','RES.PERCEN','COM.PERCEN','IND.PERCEN','RES.CUST.PCT','COM.CUST.PCT',
               'TOTAL.PRICE','RES.SALES','COM.SALES','IND.SALES','TOTAL.SALES','DEMAND.LOSS.MW','RES.PRICE',
              'COM.PRICE','IND.PRICE','CAUSE.CATEGORY.DETAIL'
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





## Assessment of Missingness


## Hypothesis Testing


## Framing a Prediction Problem


## Baseline Model


## Final Model


## Fairness Analysis

