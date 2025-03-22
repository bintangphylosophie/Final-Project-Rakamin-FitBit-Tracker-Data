# Improving Fitbit Retention Through Data Analysis
![Image](https://github.com/user-attachments/assets/39ecafa1-86d6-4640-96ed-f6ca9e6d0f2e)
The FItBit Tracker dataset utilized in this Final Project was obtained from Kaggle. 
<br>Dataset's Link : https://www.kaggle.com/datasets/arashnic/fitbit 

## 📚 Installation

This project requires Python and the following Python libraries installed:

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scipy
- Sklearn

If you don't have Python installed yet, it's recommended that you install [the Anaconda distribution](https://www.anaconda.com/distribution/) of Python, which already has the above packages and more included.

To install the Python libraries, you can use pip:

```bash
pip install numpy pandas matplotlib seaborn scipy sklearn imbalanced-learn
```
To run the Jupyter notebook, you also need to have Jupyter installed. If you installed Python using Anaconda, you already have Jupyter installed. If not, you can install it using pip:
```bash
pip install jupyter
```

Once you have Python and the necessary libraries, you can run the project using Jupyter Notebook:
```bash
jupyter notebook All EDA and Insight.ipynb
jupyter notebook Preprocessing_merged.ipynb
jupyter notebook Modelling_Merged.ipynb

```


## Problem
Fitbit is a digital health platform with over 38.5 million active users worldwide. Through wearable devices, Fitbit can record daily step counts, activity intensity, calories burned, and other data related to users' daily habits, among other things.

Despite its high popularity, Fitbit faces challenges, particularly a lack of long-term user engagement. Data shows that 62% of users stop using it after 6-12 months, with the main reasons being boredom and the lack of personalized and relevant insights 
source: Statista(2023), Gartner(2022)

## 🎯 Goals 
As a result, the F4 Team strives to improve user retention, which increases long-term usage.

## 🏁 Obective 
Our objective is to develop a machine learning predictive model that can predict a user's calorie burn rate based on their daily data, enabling a personalized experience.

## 🧩 Business Metrics 
Churn rate are the business metrics that we utilize as primary metrics.
<br>
<br>

# 🔎Stage 1: Exploratory Data Analysis (EDA)

<br>
<p align="center">
<img src="https://user-images.githubusercontent.com/74038190/212749726-d36b8253-74bb-4509-870d-e29ed3b8ff4a.gif" width="500">
</p>


This is the first stage of this project, focusing on exploratory data analysis (EDA) of the FitBit dataset. The main goal of this stage is to understand the data, find patterns, spot anomalies, test hypotheses, and check assumptions with the help of summary statistics and graphical representations.

The `All EDA and Insight.ipynb` notebook contains the initial data exploration, where we examine the basic metrics, distributions, and relationships between variables. This stage is crucial for familiarizing ourselves with the data and gaining insights that will help us decide how to handle preprocessing and modeling in the next stages.
<br>

## 📊 About Dataset 
### 📋Dataset consist :
- 940 rows and 14 columns from 32 user in dailyActivity_merged.csv dataset and minuteMETsNarrow_merged.csv dataset merged
- The target column in this dataset is "Calories"
- Dataset does not contain missing values
- The dataset have 1 duplicate values

### 📝Features

| Feature | Explanation |
|---------|-------------|
| Id| user inique ID|
| TotalSteps| daily total number of steps took|
| TotalDistance| daily total number of distance taken (in kilometers) |
| TrackerDistance | distance tracked by the device |
| LoggedActivity | logged distance from manually tracked activities |
| VeryActiveDistance | distance taken during very active physical activity |
| ModeratelyActiveDistance | distance taken during moderate activity |
| LightActiveDistance | distance taken during light activity |
| SedentaryActiveDistance | distance taken during sedentary activity |
| VeryActiveMinutes | number of minutes spent on highly active activities |
| FairlyActiveMinutes | number of minutes spent on fairly active activities |
| SedentaryactiveMinutes | number of minutes spent on sedentary active activities |
| Calories | the number of calories burned by user |
| AvgMET | daily average Metabolic Equivalents |
| TotalMET | total daily Metabolic Equivalents |

<br>
<br>

![image](https://github.com/user-attachments/assets/c0826b07-708c-41bd-b46f-103e675bf1c7)

![image](https://github.com/user-attachments/assets/f90be20f-42ea-4251-9a8b-e50f80a8f171)

![image](https://github.com/user-attachments/assets/2795dd19-95e4-4ba1-9859-3349f3d1accc)

![image](https://github.com/user-attachments/assets/c81fdefd-aeaa-429e-8e8d-3761b5b055f5)

![image](https://github.com/user-attachments/assets/89230a7a-65d0-41a3-ac73-5ac8b6290655)

![image](https://github.com/user-attachments/assets/763b2acb-7ee6-4d74-adab-a01ecca3ca6b)

![image](https://github.com/user-attachments/assets/5a6d22aa-90c1-4e0a-8e3f-812aa28fa6ca)

![image](https://github.com/user-attachments/assets/85eaba29-925a-4f2f-a885-90326585653d)




<br>
<br>

 Several significant variables have yielded insights into the attributes of candidates who tend to depart after training and those who continue to be employed by the organization after training. These variables include the candidate's location, status as an employee with relevant data science experience, educational attainment, and work experience.
<br>
<br>


# ⚙️ Stage 2: Data Preprocessing

<br>
<p align="center">
<img src="https://user-images.githubusercontent.com/74038190/221352995-5ac18bdf-1a19-4f99-bbb6-77559b220470.gif" width="400">
</p>


This is the second stage of  focusing on data preprocessing of the dataset. The main goal of this stage is to clean and transform the raw data to make it suitable for data analysis and modeling. 🧹🔄

The `Preprocessing_merged.ipynb` notebook contains the preprocessing steps, where we handle missing values, outliers, and categorical variables. This stage is crucial for improving the quality of the data and ensuring that the dataset is a correct and useful representation of the problem to be modeled. 📊

---
<br>

**Key steps in this stage include:**

## 1. **Missing Values Handling** 🕵️‍♀️<br>
The imputation method is used to populate the 0.64% missing values in 'Total_METs' and 'Avg_MERTs' feature.

## 2. **Feature Extraction** 🔄<br>
In order to enhance the future performance of the machine learning model, we extracted some feature from existed features
 ### a. extract name of the day
 ### b. extract new feature
 - 'DistancePerStep'
 - 'ActiveRatio'
 - 'TotalUsageMinutes'
 - 'VeryActiveMinutesRatio'
 - 'FairlyActiveMinutesRatio'
 - 'LightlyActiveMinutesRatio'
 - 'SedentaryMinutesRatio'
 - 'TotalDistance'
 - 'TotalActiveMinutes'
 - 'ActiveRatio'
 - 'AverageActiveMinutes'
 - 'AveragePace'
 - 'InactiveRatio'.
 ### c. Clustering
 - No clear distribution pattern was found in the boxplot. So we will try another method: Check cluster using heatmap.
![image](https://github.com/user-attachments/assets/a98314e8-dc31-4c50-ac63-c268aa999726)
On the heatmap, the pattern is clearly visible in 'TotalSteps' and 'Total_MET'. Therefore, it will be sorted based on these results. The result will be put into the 'ActivityRank' variable.
Since the clusters can be sorted, we will use the 'ActivityRank' column instead of 'Clusters'. This approach allows the machine learning model to capture the sequential patterns present in the data. However, a double-check will be performed during feature selection to ensure whether 'ActivityRank' or 'Clusters' yields a higher score. It is show that 'ActivityRank' is more usefull than 'Clusters', so we dropped 'Cluster' as well

## 3. **Feature Selection** 🎯<br>
Using SelectKBest test method from sklearn.feature_selection, It selects the top k features from a dataset based on statistical tests or scoring functions. This method is commonly used to reduce dimensionality by keeping only the most relevant features for predictive modeling. Using mutual info regression, we only keep those that have mutual information score above 0.1.

## 4. **Feature Encoding** 🏷️<br>
We encode all of our categorical features (strings) using the label encoding method. All features have been encoded at the feature extraction stage, given that our features are ordinal data and the majority of machine learning algorithms perform better with numerical data.

## 5. **Feature Transformation** 🔧<br>
Feature transformation is performed using StandardScaler because it is more robust to outliers and suitable for regression models.

## 6. **Handle Imbalance Data** ⚖️<br>
There is no class imbalance since we are working with a regression machine learning model..
<br>
<br>
<br>
## Prior to this, the dataset was split into training and testing sets. After completing all preprocessing steps, the data is clean and ready for machine learning to predict the target.🤖

<br>
<br>

# 🚀 Stage 3: Modelling

<br>
<p align="center">
<img src="https://media0.giphy.com/media/Y4PkFXkfTeEKqGBBsC/giphy.gif?cid=ecf05e47numetagrmbl2rxf6x0lpcjgq1s340dfdh1oi0x9w&ep=v1_gifs_related&rid=giphy.gif&ct=g" width="420">
</p>

This is the third stage of the project, focusing on the modelling of the  dataset. The main goal of this stage is to build and evaluate models that can predict the target variable based on the preprocessed data. 🎯

The `Modelling_Merged.ipynb` notebook contains the modelling steps, where we build, train, and evaluate various machine learning models. This stage is crucial for finding the best model that can accurately predict the target variable. 📊

## 📚 Installation

This project requires Python and the following Python libraries installed:

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scipy
- Sklearn
- shap

If you don't have Python installed yet, it's recommended that you install [the Anaconda distribution](https://www.anaconda.com/distribution/) of Python, which already has the above packages and more included.

To install the Python libraries, you can use pip:

```bash
pip install numpy pandas matplotlib seaborn scipy sklearn imbalanced-learn xgboost shap
```
To run the Jupyter notebook, you also need to have Jupyter installed. If you installed Python using Anaconda, you already have Jupyter installed. If not, you can install it using pip:
```bash
pip install jupyter
```

Once you have Python and the necessary libraries, you can run the project using Jupyter Notebook:
```bash
jupyter notebook Modelling_Merged.ipynb
```


**Key steps in this last stage include:**

## 1. **Models**: 🏗️<br>

Based on various studies, the models commonly used in calorie prediction include tree-based methods such as Random Forest and XGBoost, as well as linear models such as Linear Regression and Ridge Regression.
- Nipas et al. (2022) utilized Random Forest, Linear Regression, and Ridge Regression in their research.
- Reddy et al. (2023) also employed Linear Regression, Ridge Regression, and Random Forest Regression.
- Aziz et al. (2023) explored XGBoost, Linear Regression, SVM, and Random Forest, with the best results achieved using tree-based methods.

However, when our team tested the algorithm, we encountered a problem with overfitting. As a result, we experimented with other algorithms. A total of 13 algorithms were tested during the experiment, including:
- **Random Forest**
- **Linear Regression**
- **Ridge**
- **Lasso**
- **Elastic Net**
- **Decision Tree**
- **XGBoost**
- **Gradient Boosting**
- **Support Vector Regressor (SVR)**
- **Bayesian Ridge**
- **CatBoost Regressor**
- **LightGBM Regressor**
- **Extra Trees Regressor**

<br> 
In addition to experimenting with various algorithms, we also conducted multiple experiments on scaling, feature selection, and hyperparameter tuning using GridSearch for the algorithm with the best evaluation results.

**Scaling:** We compared two scaling methods, StandardScaler and RobustScaler.
Results: StandardScaler produced a smaller MAE compared to RobustScaler.

**Feature Selection:** We conducted experiments using feature elimination, testing several feature selection techniques-:
- Mutual Information Regression
- Correlation Analysis
- Feature Importance
- Particle Swarm Optimization (PSO)
Results: The Feature Importance technique yielded the lowest MAE and more balanced scores between the training and testing data.

**Tuning:** Hyperparameter tuning was performed only on the 3 best algorithms (those with the lowest MAE).

## 2. **Model Training and Evaluation**: 🏋️‍♀️🎯<br>
Model evaluation was performed using the MAE (Mean Absolute Error) metric, which was chosen for its robustness to outliers and its ability to provide a representative evaluation without disproportionately weighting large errors. A smaller MAE value indicates better model prediction accuracy.

From the evaluation results, the CatBoost model, **utilizing two features—'DistancePerStep' (total distance divided by total steps) and 'Total_MET'** (total daily energy calculated based on activity intensity)—produced the best prediction results with the lowest MAE compared to other models.

The following are the prediction results with the highest MAE:

### Model Results
| Model Name | MAE Train | MAE Test | MAE Dofferent |
|------------|--------------|-------------|-----------|
| CatBoost | 104.84 | 184.07 | 79.23 |
| LightGBM | 148.94 | 212.87 | 63.93 |
| Gradien Boosting | 146.01 | 204.92 | 58.91 |


We discovered that the catBoost Model with the lowest MAE test (184.07) and train (104.84), stability compared to other models. 

## 3. **Model Selection**: 🥇<br>

### Model Results
| Model Name |MAE Train | MAE Test | MAE Different |
|------------|--------------|-------------|-----------|
| CatBoost | **104.84** | **184.07** | **79.23** |

![image](https://github.com/user-attachments/assets/d23a70d6-6545-43a4-b316-5a9fd1779498)



## 🔑 Feature Importance 
Based on the CatBoost model Feature Importance:

![image](https://github.com/user-attachments/assets/569ee123-df91-48a0-a82b-5ab95f879428)

<br>

The importance feature are :
- 'DistancePerStep'
- 'Total_MET'

## 📝 Business Impact Simulation  
![Laporan Final Project - F4 pptx](https://github.com/user-attachments/assets/44b5eeae-29d7-40db-ae5c-5a9fc6d8e0dc)


**Explanation:** <br>
In this analysis, we simulate and assume that in month X, there will be 1,000 new users. Reviewing the previous data, we observe a decrease in active users to 62% of the total users, meaning that by month X+5, **before model only 380 active users remain** using the gadgets and applications.

According to Varecol, personalization in health applications can increase user participation by up to 30% of total users in the long term. With the implementation of personalization features and a **30% increase** in active users, the number of **active users in month X+5 after model is projected to reach 680.**

However, these results will need to be validated with new data after the machine learning model is deployed.


## ✅ Business Recommendation
### Feature Personalized ♥️
- **Personalized Daily/Weekly Calorie Targets**
To increase user flexibility in achieving daily/weekly calorie targets and increase user motivation in achieving goals. In accordance with goal-setting theory (Locke and Latham, 1990, 2022)
- **Deploy Model**
Deploy the best machine learning results, CatBoost with the 2 best features, in the cloud or on devices if possible.
If the predicted calorie burning results are still less than the daily target, the application will provide recommendations for activity adjustments to meet the weekly calorie burning target.

### Gamification 🎮 
- **Feature Challenge**
Gamification can be made into a challenge feature to motivate users to be more active in burning calories. 'Daily Challenge' such as the '10,000 Steps Challenge', and 'Leaderboard' to motivate users, because the majority are still classified as sedentary.

- **Feature Streak**
Then, the streak feature encourages users to stay active by providing rewards for each daily log or daily calorie target achievement.. This aims to maintain user retention and reduce boredom in using the application.

### Motivational Notification 🔔
- **Notification/Reminder**

We recommend the develover to create notification features to encourage users to use Fitbit more often and remind them of the best times to exercise, such as 7 am to 7 pm.


## Acknowledgements🌟

We would like to express our deepest appreciation to Rakamin Academy for providing the opportunity to work on this exciting project. The experience and knowledge we gained throughout this journey have been invaluable.

Special thanks to our mentor, Mr. Dino Febrianto, for his continuous guidance, patience, and support. His insights and wisdom have been instrumental in the successful completion of this project.

Finally, we would like to thank everyone who was involved in this project and those who provided their support and encouragement throughout our journey.

Regards, F4 team
- Bintang Phylosophie
- Asty Nabilah
- Putri Sausan
- Tofan Pratama
- David Bryan
<br>
<p align="center">
<img src="https://media1.giphy.com/media/3ohs7JG6cq7EWesFcQ/giphy.gif?cid=ecf05e47v1a2kre6ziee4vjvkc67vxhrwh8ho4089wc0aqli&ep=v1_gifs_search&rid=giphy.gif&ct=g" width="800">
</p>

🎓 This Final Project is a Rakamin Academy's program.
