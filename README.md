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


## Assessment of Missingness


## Hypothesis Testing


## Framing a Prediction Problem


## Baseline Model


## Final Model


## Fairness Analysis

