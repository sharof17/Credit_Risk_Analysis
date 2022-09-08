# Credit_Risk_Analysis

## Overview of the analysis:

The purpose of this analysis was to build and evaluate various machine learning models to evaluate individual customer credit risk. The dataset used to train the models was from LendingClub, "a peer-to-peer lending services company.

## Results: 

The original dataset contained 115,675 loan applications in Q1 of 2019. We used the "loan status" to determine whether the application was considered "low" or "high" risk. Applications that had "current" as the "loan status" were classified as "low risk" and the remaining as "high risk". This reduced the dataset to 68,817 total applications with 99% classified as "low risk". 

![1](images/1.png)

Using the 75/25% method to split the data for training vs. testing, 51,366 "low risk" and 246 "high risk" applications were categorized into the training set.   

![2](images/2.png)

### Use Resampling Models to Predict Credit Risk

**RandomOverSampler** Model randomly selects from the minority class and adds it to the training set until both classifications are equal. The results classified 51,366 records each as High Risk and Low Risk.

  ![3](images/3.png)

  * Balanced accuracy score: 64%.

  ![4](images/4.png)

  * The "High Risk" precision rate was only 1% with the recall at 66% giving this model an F1 score of 2%.
  * "Low Risk" had a precision rate of 100% and recall at 62%.  
  
  ![5](images/5.png)
  
  ![6](images/6.png)
  
**SMOTE (Synthetic Minority Oversampling Technique) Model**, like RandomOverSampler increases the size of the minority class by creating new values based on the value of the closest neighbors to the minority class instead of random selection. 

  * The balanced accuracy score improved slightly to 65.1%.

  ![7](images/7.png)

  * Like `RandomOverSampler`, the "High Risk" precision rate again was only 1% with the recall degraded to 61% giving this model an F1 score of 2%.
  * "Low Risk" had a precision rate of 100% and an improved recall at 69%.  

  ![8](images/8.png)
  
  ![9](images/9.png)
  
**ClusterCentroids Model**, an algorithm that identifies clusters of the majority class to generate synthetic data points that are representative of the clusters. The model classified 246 records each as High Risk and Low Risk.

  ![10](images/10.png)

  * Balanced accuracy score was lower than the oversampling models at 54.5%.

  ![11](images/11.png)

  * The "High Risk" precision rate again was only at 1% with the recall at 69% giving this model an F1 score of 1%.
  * "Low Risk" had a precision rate of 100% and with a lower recall at 40% compared to the oversampling models.  

  ![12](images/12.png)
  
  ![13](images/13.png)
  
### Use the SMOTEENN algorithm to Predict Credit Risk

**SMOTEENN (Synthetic Minority Oversampling Technique + Edited NearestNeighbors) Model** combines aspects of both oversampling and undersampling. The model classified 68,460 records as High Risk and 62,011 as Low Risk.

  ![14](images/14.png)

  * The balanced accuracy score improved to 64.5% when using a combined sampling model.

  ![15](images/15.png)

  * The "High Risk" precision rate did not improve was only 1%, however the recall increased to 72% giving this model an F1 score of 2%.
  * "Low Risk" still showed a precision rate of 100% with the recall at 57%.  
  
  ![16](images/16.png)

  ![17](images/17.png)
  
### Use Ensemble Classifiers to Predict Credit Risk

The models classified here are 51,366 as High Risk and 246 as Low Risk.

![18](images/18.png)

**BalancedRandomForestClassifier Model**, two trees of the same size and equal size to the minority class are constructed to represent one for the majority class and one for the minority class. 

  * The balanced accuracy score increased to 78.9% for this model.

  ![19](images/19.png)

  * The "High Risk precision rate increased to 3% with the recall at 70% giving this model an F1 score of 6%.
  * "Low Risk" still had a precision rate of 100% with the recall at 87%.  
  * The top feature by importance was "total_rec_prncp" at 7.9% of the total.

  ![20](images/20.png)
  
  ![21](images/21.png)

  ![22](images/22.png) 

**EasyEnsembleClassifier Model**, a set of classifiers where individual decisions are combined to classify new examples.

  * The balanced accuracy score increased to 93.2% with this model.

  ![23](images/23.png)

  * The "High Risk precision rate increased to 9% with the recall at 92% giving this model an F1 score of 16%.
  * "Low Risk" still had a precision rate of 100% with the recall now at 94%.  

  ![24](images/24.png)
  
  ![25](images/25.png)
  
## Summary: 

To sum up it is important to say that the EasyEnsembleClassifer model yielded the best results with an accuracy rate of 93.2% and a 9% precision rate when predicting "High Risk candidates. The sensitivity rate (aka recall) was also the highest at 92% compared to the other models. The result for predicting "Low Risk" was also the highest with the sensitivity rate at 94% and an F1 score of 97%. Therefore, if a model needed to be recommended to perform this type of analysis, then this one would be the best choice.