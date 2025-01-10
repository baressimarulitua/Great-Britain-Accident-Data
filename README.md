# Great-Britain-Accident-Data


## Introduction
From the metropolitan police, a reportable road traffic collision is a collision that involving a mechanically propelled vehicle and can be happened in a road or the public area, that can cause: (1) injury or damage to anybody, (2) injury or damage to an animal, (3) damage to a vehicle, and (4) damage to property build on (Report a Crime, 2024). There are many reasons why accidents occur, and these reasons can be used as a characteristic to understand accident patterns and forecast their risk. To understand any information about the accident, some data from road traffic accident reports are essential. This project’s main goal is to offer some recommendations to improving the road safety. To contribute to a better-informed approach to accident prevention and mitigation, it entails developing models that can predict accident probability and the related injuries.

## Methodology
Before processing the dataset, exploratory data analysis and data cleaning are necessary. After cleaning the data, the Apriori algorithm was employed to implement association mining and clustering to better understand the causes of accidents. In this study, the decision tree was used to predict accident severity.
Data Description and Data Cleaning
The UK Road Accident database was given by the Department of Transport. The accident database from 2020 was used in this study, containing four tables: accident, vehicle, casualty, and Lower Layer Super Output (LSOA) of the accident location. For the accident table, there are 91.199 accident data with 14 missing values. These missing values are from the column that indicate where the accidents were happened. For the casualty table, there are 115.584 rows. For vehicle data, there are 167.375 rows. And for LSOA table, there are 34.378 rows. 
The interpolation method was applied for missing value in latitude and longitude columns. For the age of driver column, there are some drivers that still underage. Since the minimum driver age in UK is 17 years old, is it necessary to change their age value with median. There are also some missing entries that addressed as “-1” in accident table, vehicle table, and casualty table. To change it, these negative values are imputed into a median value. 
  

## Accident Demography
 
Figure 1. Driver Age Pyramid
There was more male driver that happened to be involved with an accident compared to females. The age group most liable to involved with accident was between 30 and 39 years old. 

## Data Insight
### Significant hours of the day and days of the week for accidents occurrence
 
Figure 2. Accident occurence during the hours of a day
From this graph, many accidents started to rising around 8 AM in the morning. Started from 3 PM until 6 PM, the frequency of accidents is abnormally high and peaks at 5 PM.

 
Figure 3. Accident occurence per weekday
From this graph, most accident peaks during weekend, especially on Saturday.

### Significant hours of the day and days of the week for accidents occurrence for motorbikes

The vehicle type that analysed in this case is motorcycle. Specifically, there are morotcycle 50cc and under (2), motorcycle over 50cc and up to 125cc (3), motorcycle over 125cc and up to 500cc (4), and motorcycle over 500cc (5).
 
Figure 4. Significant hour for accident occurence based on type of motorbikes
Like the previous chart, motorcycles accidents are intense between 3 PM and 6 PM and peaked around 5 PM. The group of bikes with 50cc to 125cc (3) has the greatest accident involvement among the several motorcycle kinds (50cc and less, 50cc to 125cc, 125cc to 500cc, and over 500cc).

 
Figure 5. Significant day for accident occurence based on type of motorbikes
From this chart, the accident occurred mostly on Weekend, especially on Saturday. Like the previous chart, the group of bikes with 50cc to 125cc (3) has the greatest accident involvement among the several motorcycle kinds except for the group of motorcycle with over 500cc that experiences it is peak on Monday.

### Significant hours of the day and days of the week when pedestrian accidents occur.
 
Figure 6. Accident occurrence per hour for pedestrians
From this chart, there are significant percentage of these accidents occurred between 3 PM and 6 PM. With a peak at around 3 PM. There are also significant accidents happened during the early rush hour, which began at 8 AM.

 
Figure 7. Accident occurrence per day for pedestrians
From this chart, it was accounted that weekdays have most pedestrians’ accidents. The most accidents occurred on Saturday from this chart. It can be correlated with the vehicle incident that mostly occurred also peaked on Saturday.

### Exploring the impact of selected variables on accident severity using the apriori algorithm

In this part, this study is going to explore the impact of selected variables on accident that happened using Apriori algorithm. The variables that used in this part are the accident severity rate, the speed limit, and the weather conditions. Apriori algorithm was applied with minimum support of 0.2 and minimum threshold of 0.5. 
To generate some rules, the columns are contained with accident severity, speed limit, and the weather conditions. Each of these column are in categorical, that can be defined as:
-	Accident severity:
o	1 = Fatal
o	2 = Serious
o	3 = Slight
-	Speed limits = speed limit on the track/road.
-	Weather conditions :
o	1 = Fine without high winds
o	2 = Raining without high winds
o	3 = Snowing without high winds
o	4 = Fine with high winds
o	5 = Raining with winds
o	6 = Snowing with high winds
o	7 = Fog or mist
o	8 = Other
o	9 = Unknown

Table 1. Five associations by the Apriori algorithm
Rule	Antecedents	Consequents	Support	Confidence	Lift
1	(Fine)	(Slight)	0.603186	0.777746	0.992676
2	(Speed limit 30)]	(Slight)	0.460082	0.802705	1.024532
3	(Fine, speed limit 30)	(Slight)	0.359763	0.799094	1.019923

Rule 1 indicates the fine conditions correlate with slight conditions (60.31% support, 77.77% confidence, and 0.992676 lift). The results indicates that most accident while the weather was fine without any strong winds result in minor injuries. Rule 2 indicates the urban area based on the low-speed limit correlate with slight conditions (46.00% support, 80.27% confidence, and 1.024532 lift). The results indicates that most accident while the in the urban area result in minor injuries. Rule 3 indicates the fine condition in an urban area correlate with slight conditions (35.98% support, 79.91% confidence, and 1.019923 lift). The results indicates that most accident while the in the urban area while the weather was fine result in minor injuries.
Clustering Region
 
Figure 8. Cluster of accident occurrence in Humberside region

This study is using K-Means clustering to analyse the accident occurrence in Humberside region. 
 
Figure 9. The effect of speed limit and weather conditions on accident occurrence

To see the relation between the speed limit and weather condition, this study clustering speed limits and weather conditions in Humberside region. From the graph above, the most clusters are between weather conditions 1 (fine without high winds) and weather conditions 2 (raining without high winds).

### Outlier Detection
In this study, the outlier detection was performed on the age of the driver features using IQR.
 
Figure 10. Boxplot of the Age of the Driver
This boxplot represents the distribution of driver ages in our dataset. The central box represents the interquartile range (IQR), spanning from the first quartile (Q1) to the third quartile (Q3). The line inside the box indicates the median age. Outliers are the points that lie outside the whisker of the boxplot. In this case, there are a point at age 100, which is far above the upper whisker. In the age of the driver data, Q1 is 30, Q3 is 49, and the IQR is 19. This suggests that this data point is unusual compared to the rest of the dataset. Such outliers can affect the analysis by skewing the results.

### Fatal Injuries Prediction in Road Traffic Accidents

In this study, the decision tree classifier was implemented with the feature are sex of the casualty, the age of the casualty, and the casualty class. In this case, the casualty class contain the driver/rider, the passenger, and the pedestrian. The target on this classifier is the severity of casualty, that contain fatal casualty, serious casualty, and slight casualty.

 
Figure 11. Classification Report

From the classification report above, it is resulted that the accuracy rate is 99%. That’s means 9 out of 10 were correctly predicted. It might be good but can be indicate some issues like imbalance of data, data leakage, or overfitting.

 
Figure 12. Confusion Matrix
## Recommendations
The following recommendations are obtained from the thorough data analysis and forecast:
1.	Since the 50cc to 125cc motorcycle have the highest rate of accident, some policies to replace and implement the safer option are necessary.
2.	Optimize the traffic control while in rush hour, both in the morning and in the evening. Especially to prevent some accident happened to pedestrians.

Bibliography
Report a Crime. (2024, May 21). Retrieved from Metropolitan Police: https://www.met.police.uk/ro/report/ocr/af/how-to-report-a-crime/report-a-road-traffic-incident/

