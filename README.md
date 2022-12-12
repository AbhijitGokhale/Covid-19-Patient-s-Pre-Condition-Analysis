# Covid-19-Patient-s-Pre-Condition-Analysis
A health crisis of massive proportion such as the current COVID-9 pandemic provides us with an opportunity to ponder and reflect over what we can better in the way we deal with healthcare to make us humans be more prepared and enabled to combat such an event in the future. During the entire course of the pandemic, one of the main problems that healthcare providers have faced is the shortage of medical resources and a proper plan to efficiently distribute them. They have been in the dark failing to understand how much resource they could even in the very next week as the COVID-19 curve has swayed very unpredictably. In these tough times, being able to predict what kind of resource an individual might require at the time of being tested positive or even before that will be of great help to the authorities as they would be able to procure and arrange for the resources necessary to save the life of that patient.

## Introduction
A health crisis of massive proportions such as the current COVID-19 pandemic provides us with an opportunity to ponder and reflect over what we can do better in the way we deal with healthcare to make us humans be more prepared and enabled to combat such an event in the future.
During the entire course of the pandemic, one of the main problems that healthcare providers have faced is the shortage of medical resources and a proper plan to efficiently distribute them.
They have been in the dark failing to understand how much resource they could even in the very next week as the COVID-19 curve has swayed very unpredictably. In these tough times, being able to predict what kind of resource an individual might require at the time of being tested positive or even before that will be of great help to the authorities as they would be able to procure and arrange for the resources necessary to save the life of that patient.

## Project Motivation and Goal
Our main objective was to analyze the factors that influence mortality in patients who do not need an intensive care unit and those who do. What are the underlying comorbidities that patients are likely to test positive for COVID? Which factors influence the need for an intensive care unit? This can help with patient triage, optimal distribution of vaccinations (if needed) in countries with limited resources, or prevention in countries susceptible to the virus.

## Dataset
The data obtained is from the Mexican government and hence, the analysis is valid for Mexico or maybe North America. The pandemic stats and behaviors are extremely different for Asian countries when compared to North American or European countries owing to far lower-case fatality rate for Asia. We have data of 566k patients related to their health conditions such as whether they have pneumonia, cardiovascular problems, obesity, copd, asthma etc.

These are our columns –

![image](https://user-images.githubusercontent.com/84480824/206977364-c4fd0781-8bcc-4680-a912-1d853d0a40c6.png)

## Implementation
* **Exploratory Data Analysis:** Correlation Analysis, Null & True Duplicate values, Outlier Analysis, Data Imbalance Analysis
* **Time Series Trends Analysis:** 
    ![image](https://user-images.githubusercontent.com/84480824/206978372-1311f716-d69c-458a-b4a5-03220180dc33.png)
    We can see the cases started rising around March and peaked around May and then gradually started to come down when restrictions were imposed by the Mexican government.
    
    ![image](https://user-images.githubusercontent.com/84480824/206978424-95638c04-2172-4986-b312-f0f55e716c12.png)
    Patients who died after suffering a month are below 30. This could be because they had milder virus and the medical attention over weeks was working well to bring down deaths.
    
    ![image](https://user-images.githubusercontent.com/84480824/206978471-d21ee008-d4ec-4590-9083-4c0987cc37a9.png)
    We can see the graph going down meaning the longer they are in the hospital the number of patients who died is reducing. It is likely that the medical care given was working and the medical team was in control of the situation.
    
    ![image](https://user-images.githubusercontent.com/84480824/206978581-356e90b8-1c24-4465-93aa-7e152c269520.png)
    As we can see in the above visualization the distribution of ICU patients who have usual conditions is as follows:- 
      * Let us look at Lung related diseases or infections because corona virus is known to decapitate the lungs. 
      * There were 8768 ICU patients. 5667 patients are COVID +ve and 3101 patients are COVID-ve. 
      * Around 88% of COVID positive have pneumonia, similarly 74% of COVID negative have pneumonia.
      * Around 53% of above pneumonia positive people needed intubation. 
      * Around 4% of the above people who needed intubation, use tobacco. 
      * So, Pneumonia appears like a strong reason to need ICU whether the COVID result is positive or negative
      
    ![image](https://user-images.githubusercontent.com/84480824/206978771-5b360a11-fe8a-4cae-97eb-55dc708325c7.png)
    As we can see in the above visualization the distribution of ICU patients who did not have usual conditions is as follows: 
      * We have 3101 patients that had a requirement for ICU but weren’t tested positive for COVID. 
      * Around 26% of COVID negative have no pneumonia (primary reason to have an ICU admission). 
      * Around 80% of above pneumonia negative people needed NO intubation. 
      * As seen in the bottom bar, 406 patients who tested covid negative - are free of usual suspects (preconditions /co-morbidities)
  
  Let’s understand the fatality rate distribution with respect to different Age groups. 
  ![image](https://user-images.githubusercontent.com/84480824/206978951-887f1a74-0402-4cf8-ab75-4f719e3c7015.png)
  As we can see from the above distribution of Age Category, Elderly people and senior citizens in the age range of 50 to 80 have the highest fatality rate because of Covid.
  
* **Machine Learning:**
Below are the 4 supervised machine learning algorithms that we have used to classify ICU requirements, likelihood of testing positive and factors that affect fatality rate.

![image](https://user-images.githubusercontent.com/84480824/206977595-91e6c32f-ed2a-4f65-9d8c-d3dc931fb3a2.png)

Hyperparameter tuning was performed on each model using grid search and 3-fold cross validation. Since the classes were imbalanced, we tried to focus more on precision and recall. We have used sklearn for building models. Below, we present the best performing model and important features in each case as well as consolidated results at the end. 

We decided to build above models using below case statements in order to better understand the ICU requirements based on patients who have died and are still hospitalized, utilizing various pre-conditions as a basis: 
    * **Case1:** Predicting death for patients requiring ICU 
    * **Case2:** Predicting death for patients not requiring ICU 
    * **Case3:** Predicting ICU for died patients 
    * **Case4:** Predicting ICU for hospitalized patients 
    * **Case5:** Predicting Covid 
    
Using the results obtained from above cases and exploratory analysis will help us to give suggestions to the hospital on how to handle the patient's ICU requirement of ICU based on certain pre-conditions.

Below are the hyperparameters considered for each model -

![image](https://user-images.githubusercontent.com/84480824/206977997-8b86950e-f2a1-46b1-9c41-000d828ef2c6.png)

* **Model Selection & Evaluation:** Best Validation Score after hyperparameter tuning, Confusion Matrix, Precision, Recall, F-1 Score, Accuracy, AUC-ROC, Precision-Recall Curve

## Conclusion and Suggestions 

The exploratory analysis and the model evaluation results led us to actionable insights in order to decide whether a patient needs to be given ICU or not considering the reasons that had caused fatality and the importance of Covid and other pre-conditions to get to that result. 

* If any patient is hospitalized with a positive test result, he should be given ICU urgently if they have pneumonia or are infants. 
* Large number of deaths are caused by COVID instead of other comorbidities. 
* Patients in the age range of 0 to 10 and in the age range of 50 to 60 are more prone to Covid if they are suffering from medical preconditions such as pneumonia, immunosuppression, and other diseases. 
* Mortality rate among patients who were hospitalized the day they started showing symptoms is higher, maybe due to higher severity of Covid than other pre-conditions based on the feature Importance. 
* The longer patients are in the hospital the mortality rate is reducing. It is likely that the medical care given was working.
