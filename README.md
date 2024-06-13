# US Power Outages
Project for DSC 80 at UCSD

**Authors:** Stuti Verma and Prithvi Kochhar

## Introduction

Our goal for this project, is to analyze a dataset of major power outages in the U.S. spanning from January 2000 to July 2016. The dataset is made available by Purdue University’s Laboratory for Advancing Sustainable Critical Infrastructure (LASCI), and can be accessed at [Purdue LASCI](https://engineering.purdue.edu/LASCI/research-data/outages).

The dataset provides extensive information on the outages themselves as well as geographical and climatic characteristics, electricity consumption patterns, and economic traits of the affected regions.

Our analysis will progress through several key stages. Initially, we will clean the dataset and perform exploratory data analysis to understand the data's structure and trends. 

The core research question we aim to explore is: How do the number of customers affected and climate conditions impact the duration and frequency of power outages across different regions? This analysis is crucial as it helps in identifying the key factors influencing power outages, which can aid in improving power outage frequencies and response strategies.

The original dataset consists 1,534 rows and 57 columns, corresponding to 1,534 power outages and 57 features respectively. For this analysis, our focus will be on the following key columns:

| Column      | Description |
| :---   | :---- |
| YEAR        | The year when the outage occurred  |
| MONTH       | The month when the outage occurred     |
| U.S._STATE  | The state where the outage occurred
| CLIMATE.REGION      | The climate region of the state (Northeast, South etc.)       |
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

### Data Cleaning

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
        
### Univariate Analysis


The histogram plot below shows the number of major power outages in each climate region.
This plot reveals that certain regions experience outages more frequently. We wanted to see this relation to interpret whether regions with harsh weather conditions or older infrastructure might see a higher number of outages.
Understanding which regions are more prone to outages can help in targeting infrastructure improvements and preventative measures.

<iframe
  src="assets/plot1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


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




The plot below shows the number of outages occurring in each month across the data's timeframe (January 2000 to July 2016).
The plot allows us to interpret any seasonal trends, such as an increase in outages during winter months when storms are more frequent or during summer months when high electricity demand can lead to failures.
Identifying seasonal trends can help in preparing for periods with higher risks of outages and planning maintenance accordingly.

<iframe
  src="assets/plot2unireplace.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>




### Bivariate Analysis

The scatter plot below illustrates the relationship between the duration of power outages (in minutes) and the number of customers affected.
The scatter plot suggests a positive correlation, indicating that longer outages usually tend to impact more customers.
This trend highlights the importance of quickly restoring power to minimize the number of affected customers. It also suggests that more severe outages, which take longer to fix, tend to impact larger populations, possibly due to the complexity of the issues causing the outages.

<iframe
  src="assets/plot1bivariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The box plot below shows the distribution of average outage durations for different causes behind power outages.
The plot indicates that certain causes, such as fuel supply emergency or severe weather, lead to longer outages compared to others.
Understanding which causes result in longer outages can help prioritize resources for prevention and quicker response. For instance, if equipment failure causes longer outages, investing in better maintenance and upgrading infrastructure could reduce outage durations.

<iframe
  src="assets/plot2bivariate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


The pivot table below shows the average duration of outages for different climate categories and regions.
The table reveals variations in outage durations based on climate and geographical location, with some climates and regions experiencing significantly longer outages on average. For example we see that the average outage duration in the Northeast region during warm climate is comparatively high (4176 minutes).
These insights can help in developing targeted strategies for outage prevention and response. For example, regions with longer outage durations might benefit from enhanced infrastructure resilience measures.


| CLIMATE.REGION     |     cold |   normal |    warm |
|:-------------------|---------:|---------:|--------:|
| Central            | 2841.27  | 2708.7   | 2413.84 |
| East North Central | 6568.79  | 5271.22  | 3022.12 |
| Northeast          | 3657.25  | 2273.96  | 4175.91 |
| Northwest          |  874.681 |  733.612 | 3063.54 |
| South              | 1969.57  | 3630.79  | 1861.4  |




## Assessment of Missingness

### NMAR Analysis:

In the dataset, the 'OUTAGE.RESTORATION.DATE' and 'OUTAGE.RESTORATION.TIME' columns are likely Not Missing At Random (NMAR). This assessment is based on the nature of how this data is recorded and the circumstances under which it might be missing.
- The restoration date and time might be missing if the outage is ongoing. In such cases, it is impossible to record a restoration time because the outage has not yet been resolved.
- For particularly severe outages, the restoration information might not be promptly recorded due to the complexity and scale of the incident. This could include situations where the data recording systems are affected by the outage or where the restoration process is too chaotic to allow for immediate logging.

In both cases, the missing data is directly related to the values themselves (i.e., ongoing or unreported severe outages), making them NMAR.

To better understand the missingness and potentially reclassify it as Missing At Random (MAR), the following additional data might be useful:
- Detailed incident reports for each outage, which might provide context on whether the restoration was delayed or ongoing at the time of data recording.
- Real-time status updates or logs from the utility companies, indicating whether the restoration process was in progress or completed.

By incorporating such additional data, it might be possible to demonstrate that the missingness is related to observable factors, thus reclassifying it from NMAR to MAR.




### Analysis of missingness dependency:

##### Missingness of CUSTOMERS.AFFECTED column:

To assess whether the missingness in the 'CUSTOMERS.AFFECTED' column is dependent on the 'CLIMATE.CATEGORY' column, we performed a permutation test.

**Null Hypothesis:** The missingness of values in 'CUSTOMERS.AFFECTED' does not depend on the 'CLIMATE.CATEGORY'.

**Alternative Hypothesis:** The missingness of values in 'CUSTOMERS.AFFECTED' depends on the 'CLIMATE.CATEGORY'.

**Test Statistic:** Total Variation Distance (TVD)

<iframe
  src="assets/plot3missing.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The histogram below represents the empirical distribution of our test statistics with 500 permutations, the vertical red line marks the observed test statistic.

<iframe
  src="assets/plot4replace2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


Our observed TVD is 0.034, since that corresponds to a **p-value of 0.366** i.e greater than the typical significance level of 0.05, we **fail to reject the null hypothesis**. This indicates that the missingness in 'CUSTOMERS.AFFECTED' is **not significantly dependent** on 'CLIMATE.CATEGORY', or we can say that the distribution of climate category is the same when customers affected is missing and not missing




##### Missingness of OUTAGE.DURATION column:

Similarly, To assess whether the missingness of values in the 'OUTAGE.DURATION' column is dependent on the 'CLIMATE.CATEGORY' column, we performed a permutation test.

**Null Hypothesis:** The missingness of values in 'OUTAGE.DURATION' does not depend on the 'CLIMATE.CATEGORY'.

**Alternative Hypothesis:** The missingness of values in 'CUSTOMERS.AFFECTED' depends on the 'CLIMATE.CATEGORY'.

**Test Statistic:** Total Variation Distance (TVD)

<iframe
  src="assets/plot1missing.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The histogram below represents the empirical distribution of our test statistics with 500 permutations, the vertical red line marks the observed test statistic.

<iframe
  src="assets/plot2replace.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


Our observed TVD is 0.32, since that corresponds to a **p-value of 0.0**, we **reject the null hypothesis**. This suggests that the missingness in 'OUTAGE.DURATION' is **significantly dependent** on 'CLIMATE.CATEGORY', or, the distribution of Cliamte Category is different when Outage Duration is missing and not.




## Hypothesis Testing

For the hypothesis testing, we aimed to investigate whether severe weather causes lead to longer power outage durations compared to non-severe weather causes. The features we used to for the hypothesis test are: OUTAGE.DURATION and CAUSE.CATEGORY


**Null Hypothesis:** There is no difference in the mean power outage duration between severe weather causes and non-severe weather causes.

**Alternative Hypothesis:** Severe weather causes longer mean power outage durations.

**Test Statistic:** Difference in means.


We separated the dataset into two groups: one for severe weather causes and one for non-severe weather causes.
Calculated the mean outage durations for each group:
Mean duration for non-severe weather causes: 1309.18 minutes
Mean duration for severe weather causes: 3837.82 minutes
Observed difference in means: 2528.64 minutes

**Permutation Test:**
We combined the outage durations from both groups and performed 1000 permutations.
In each permutation, we randomly shuffled the combined durations and recalculated the mean difference between the two groups.


We calculated the p-value by comparing the observed difference with the distribution of the permuted differences.
The **p-value obtained was 0.0**

The results of the permutation test strongly suggest that the null hypothesis **can be rejected**. The p-value (0.0) indicates that it is highly unlikely that the observed difference in mean outage durations between severe and non-severe weather causes is due to random chance.

Therefore, the permutation test suggests that severe weather causes significantly longer power outage durations compared to non-severe weather causes.


To visualize the results of our permutation test, we created a histogram of the permuted differences in mean outage durations. The red dashed line represents the observed difference of 2528.64 minutes, which lies far outside the distribution of permuted differences, further illustrating the significance of our findings.


<iframe
  src="assets/plot1hyp.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>



## Framing a Prediction Problem

Our goal is to develop a prediction model to predict the **outage duration** of a power outage.  The prediction problem is a regression problem, as we are trying to predict a continuous variable (OUTAGE.DURATION) based on various features.

**Response variable:** OUTAGE.DURATION

Understanding and predicting outage duration is crucial for planning and resource allocation during power outages. By accurately predicting how long an outage will last, utility companies can better prepare and respond to minimize the impact on affected customers.

**Evaluation Metric:** Root Mean Sqaured Error (RMSE)

RMSE is chosen because it penalizes larger errors more than other metrics such as Mean Absolute Error (MAE). This makes RMSE particularly useful in regression when larger errors are especially undesirable, as is the case when predicting outage durations. RMSE provides a good measure of how well the model predicts the duration of outages by emphasizing the importance of minimizing large prediction errors, which can have significant operational implications for utility companies.

**Justification of features:**

To ensure that our model is practical and makes predictions based on information available at the time of prediction, we only use features that would be known or could be estimated at the onset of an outage. The features we use to train our model are: CAUSE.CATEGORY, CLIMATE.REGION, U.S. STATE, POPULATION, and CUSTOMERS.AFFECTED. These features are known at the time of the outage, and the number of customers affected can be quickly assessed early in the outage.


## Baseline Model


For the baseline model, we used a simple linear regression model to predict the **outage duration** of a power outage. The features chosen for this task were **Customers Affected** (numerical) and **Cause Category** (categorical). We used one-hot encoding to convert the categorical values into values suitable for our regression model. We also standardized the numerical columns.

We implemented the feature transformations and model training within a single sklearn Pipeline. We used the **ColumnTransformer** to handle standardization of the numerical features and one-hot encoding of the categorical features.

**Model Training:**
Train-Test Split: 80% training data and 20% test data
Preprocessing: StandardScaler for numerical features and OneHotEncoder for categorical features


###### Performance:

**Training Score:**
𝑅^2^ = 0.0595

**Test Score:** 
𝑅^2^ = 0.1197

**Training RMSE:** 4454.45
**Test RMSE:** 3546.66

The performance of the baseline model, evaluated using the R-squared metric and Root Mean Squared Error (RMSE), indicated that the model has **limited** predictive power with a low R-squared value of 0.1197 on the test data. A lower R-sqaured value suggests a higher RMSE value as seen above and for a good predictive model you would ideally want a low RMSE value. Despite this, the model provides a foundational understanding for predicting outage duration.


## Final Model

For the final model, we sought to improve upon the baseline model by engineering additional features and optimizing hyperparameters. We included more features to provide additional context and potentially improve the model's accuracy.

**Features Added:**
- Population (numerical)
: Including the population of the affected area can provide insights into the scale of impact and potential challenges in restoring power. Larger populations may correlate with longer outage durations due to the complexity of restoring services to more customers.
- U.S. State (categorical)
: Different states may have varying infrastructure, policies, and resources for dealing with power outages. By including the state, the model can capture these regional differences that might affect outage duration.
- Month (categorical)
: The time of year can significantly impact power outages. For example, certain months may be prone to severe weather conditions like hurricanes or snowstorms, which can cause longer outages. Including the month helps the model account for these seasonal variations.
- Year (categorical)
: Technological advancements and changes in infrastructure over time can influence how quickly outages are resolved. By including the year, the model can consider these temporal trends and improvements in outage management.
- Climate Category (categorical)
: Different climate regions can experience varying weather patterns and environmental conditions, impacting the frequency and duration of power outages. By incorporating the climate category, the model can better predict outage duration based on regional climate characteristics.

**Model Algorithm:**
We used a series of pipelines to test different combinations of these features and selected the best-performing one using k-fold cross-validation.

The best combination of features was then pre-processed using One-Hot-Encoding for categorical columns, and then fit to the training and test data using a **linear regression model**.


###### Best Model:

**Features:** Cause Category, U.S. State, Month, Climate Category
Preprocessing: FunctionTransformer for numerical features and OneHotEncoder for categorical features
Model: Linear Regression

###### Performance:

**Training Score:** 
𝑅^2^ = 0.3040

**Test Score:**
𝑅^2^ = 0.2748

**Training RMSE:** 3832.10
**Test RMSE:** 3219.11

After conducting a cross-validation with multiple pipelines, we found that the model incorporating all the mentioned features performed the best. The final model showed an improvement in performance compared to the baseline model, with an R-squared value of 0.2748 on the test data with an RMSE value of 3219.11. 

After analyzing our baseline model we came to the conclusion that the CUSTOMERS.AFFECTED feature was affecting the performance of our model negatively. Hence in our final model we chose to use other categorical columns such as MONTH, U.S.STATE, CAUSE.CATEGORY to predict the outage duration.



## Fairness Analysis

