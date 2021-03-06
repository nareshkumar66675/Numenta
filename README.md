# Numenta

Project for anomaly detection

# What it Does?
  - It detects the anomalies in the given dataset
  
# Datset Used
- Product Demand : https://github.com/numenta/NAB/tree/master/data
- ###### It contains many Data Files. For our detection we are going to use the below file


        Machine_temperature_system_failure.csv: Temperature sensor data of an internal component of a large, industrial mahcine.

# Anomaly Detection
- We will be applying two types of anomaly detection on the data
   - **Isolation Forest**
   - **One Class SVM**
# Feature Engineering
- **Hours**
  - From the timestamp, new column to denote the hour of day. *For Ex : 9 am -> 9 and 9pm -> 21*
- **DayTime**
  - A new column to denotes, if the temperature has been recorded in daytime or at night.
- **Day of The Week**
  - A new column to denote day of the week. *For Ex: Mon -> 0*
- **Week Day**
  - This column is used to represent if the data has been recorded in Weekday or Weekend. *For Ex: Mon -> 1 and Sun -> 0*
- **Categories**
  - This column represent data if its recorded in WeekEnd/WeekDay and Day/Night. *For Ex: 2013-12-02 21:15:00 -> WeekDayNight*


# Analysis

- Below graph shows Machine Temperatures against Time Stamp.

![Temperature Vs Time](https://raw.githubusercontent.com/nareshkumar66675/Numenta/master/reports/TempVSTime.png "Temperature Vs Time")

- Below graph shows the Comparison of Temperatures during the created Categories (i.e) WeekEnd/Weekday and Day/Night
![Temperature Vs Time](https://raw.githubusercontent.com/nareshkumar66675/Numenta/master/reports/TempVSCategories.png "Temperature Vs Time")

#### Isolation Forest:
- Isolation Forest has been applied on the feature engineered dataset with contaimation fraction as **0.05**
- Below graph shows the anomalies.

![Isolation Forest - 1](https://raw.githubusercontent.com/nareshkumar66675/Numenta/master/reports/IsolationForest1.png "Isolation Forest - 1")    ![Isolation Forest - 2](https://raw.githubusercontent.com/nareshkumar66675/Numenta/master/reports/IsolationForest2.png " Isolation Forest - 2")

#### One Class SVM:
- Once CLass SVM has been applied on the feature engineered dataset with contaimation fraction as **0.05**
- Below graph shows the anomalies.

![One Class SVM - 1](https://raw.githubusercontent.com/nareshkumar66675/Numenta/master/reports/OneClassSVM1.png "One Class SVM")    ![One Class SVM - 2](https://raw.githubusercontent.com/nareshkumar66675/Numenta/master/reports/OneClassSVM2.png " One Class SVM - 2")

#### Results:
- Below are the count of anomalies for both the methods.

| Type             | Normal | Anomaly |
|------------------|--------|---------|
| Isolation Forest | 21556  | 1139    |
| Once Class SVM   | 21617  | 1078    |

- Below is the anomaly description from dataset given by the creator.

> The first anomaly is a planned shutdown of the machine. The second anomaly is difficult to detect and directly led to the third anomaly, a catastrophic failure of the machine.

- By looking at the graphs, it is evident that 
  - *First Planned Shutdown*: It happened during the time frame **2013-12-14 to 2013-12-20**
  - *Second Anomaly*: It must have happened during the time frame **2014-02-03 t0 2014-02-05**
  - *Third Anomaly*: It must have happened during the time frame **2014-02-08 t0 2014-02-14**

# Project Struture

##### Src
- Numenta.py - python file exported from Jupyter
##### Notebooks
- Numenta.ipynb - Jupyter notebook
##### Data
- External - Numenta Data
##### Reports
- Graphs - Comparisons

***

##### References

- https://www.kaggle.com/victorambonati/unsupervised-anomaly-detection
  
