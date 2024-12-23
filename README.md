# Phase-3-repository

## 1. BUSINESS UNDERSTANDING 

With the data we are provided with, we are supposed to give clear and concise predictions of arrests so that we can be able to prevent the occurences of being falsely arrested and also being able to identify which race, gender and what crimes are committed when one is stopped 

We want to build a classifier to predict whether an arrest happens after a Terry Stop. We're interested in using data like the presence of weapons, time of day, and even potentially sensitive information like race and gender. This could be a powerful tool for understanding the factors that influence police decisions, but it's important to handle sensitive data responsibly and be transparent about how you use it. We're curious if there's a correlation between race (of officer or subject) and the likelihood of an arrest. This is a complex and sensitive topic, and it's important to approach it with careful consideration 

### 1.1 Business Objectives 
1. **Improve Transparency and Accountability:**
*Goal:* To provide a clearer understanding of the factors that influence police decisions during Terry Stops, promoting greater transparency and accountability in law enforcement.
*Outcome:* The model's insights can be used to identify potential biases and areas for improvement in police practices.

2. **Reduce Unnecessary Arrests:**
*Goal:* To develop a model that can help predict the likelihood of an arrest based on objective factors, reducing the number of unnecessary arrests and promoting fairer treatment.
*Outcome:* The model can be used to inform police officers' decisions during Terry Stops, potentially leading to fewer arrests based on subjective biases.

3. **Inform Policy and Training:**
*Goal:* To provide data-driven insights that can inform policy decisions and training programs aimed at reducing bias in law enforcement.
*Outcome:* The model's findings can be used to develop training materials that address potential biases and promote more equitable policing practices.

### 1.2 Project Objectives 
1. **Develop a Predictive Model:**
Goal: To build a robust machine learning model that can accurately predict the likelihood of an arrest after a Terry Stop based on relevant factors.
Outcome: A model that can reliably identify high-risk situations where an arrest is more likely, but also highlight potential biases in decision-making.

2. **Analyze Factors Influencing Arrest Decisions:**
Goal: To identify and quantify the influence of various factors (e.g., presence of weapons, time of day, race, gender) on the likelihood of an arrest.
Outcome: A detailed understanding of the factors that contribute to arrest decisions, allowing for targeted interventions to address potential biases.

3. **Ensure Responsible and Ethical Use of Data:**
Goal: To implement strong ethical safeguards in data collection, model development, and model deployment to prevent misuse and ensure fairness.
Outcome: A model that is transparent, accountable, and used responsibly to promote fairness and equity in law enforcement.

## 2. DATA UNDERSTANDING 
### 2.1 Column Description

1. Subject Age group: Subject age group (10 year increments) as reported 
2. Subject ID: Key, generated daily, identifying unique subjects in the dataset using a character to character match of first name and last name
3. GO/SC Num: General Offense or Street Check number, relating the Terry Stop to the parent report
4. Terry stop ID: Key identifying unique Terry Stop reports.
5. Stop resolution: Resolution of the stop as reported by the officer 
6. Weapon type: Type of weapon, if any, identified during a search or frisk of the subject.
7. Officer ID: Key identifying unique officers in the dataset.
8. Officer YOB: Year of birth, as reported by the officer.
9. Officer Gender: Gender of the officer 
10. Officer Race: Race of the officer 
11. Subject perceived Race: percieved race of the subject as reported 
12. Subject Percieved Gender: Percieved gender of the subject as reported 
13. Reported date: Date the report was filled in the Records Management System (RMS)
14. Reported Time: Time the stop was reported in the RMS
15. Initial Call Type: Initial classification of the call as assigned by 911
16. Final Call type: Final classification of the call as assigned by the primary officer closing the event 
17. Call Type: How the call was received by the communications center
18. Officer Squad: Funstional squad Assignment(not budget) of the officer as reported by the Data Analytics Platform
19. Arrest Flag: Indicator of whether a "physical arrest was made, of the subject, during the Terry Stop
20. Frisk Flag: Indicator of whether a "frisk" was conducted, by the officer, of the subject, during the stop
21. Precinct: Precinct of the address associated with the underlying Computer Aided Dispatch (CAD)
22. Sector: Sector of the address associated with underlying CAD event
23. Beat: Beat of the address associated with the underlying CAD event

### 2.2 Selecting the columns to be used 

* By further filtering your data to only the columns that you need will help you have better understanding of what you are working with
* You select these columns by understanding the objectives you want to accomplish and see what sort of columns works best for you

#### Conclusions drawn

The provided image shows a histogram depicting the distribution of data across different precincts. Some conclusions that can be drawn are:

* **West precinct has the highest count:**  The West precinct has the tallest bar, indicating it has the highest number of occurrences, exceeding 1000.
* **South and East precincts have similar counts:** The bars for North and East precincts appear to have similar heights, suggesting a comparable number of occurrences, both falling between 500 and 600.
* **Limited data for FK ERROR, OOJ, Unknown:** The bars for FK ERROR, OOJ, and Unknown are very small, indicating very few occurrences fall under these categories.
* **Data is skewed:** The data is not evenly distributed across precincts, with a clear skew towards the West precinct followed by the North precinct. This suggests that the terry stops is likely concentrated or more prevalent in the West and North precinct compared to others.

## 3 DATA PREPARATION 
### 3.1 Performing a Train-Test split 
We do this so that we can be able to evaluate the model

* **Focus on Specific Variables:** The code is clearly interested in analyzing the relationships between variables like "Stop Resolution," "Subject Perceived Race," "Subject Perceived Gender," etc., without considering the officers' race or gender, and the subject's age group.

* **Potential Analysis:** This data preparation suggests a potential analysis focusing on how these variables relate to each other. For example, we want to investigate if certain subject perceived races or genders are more likely to be stopped, frisked, or arrested, independent of the officer's characteristics.


### 3.2 One hot encoding the necessary columns 

We one hot encode in order to change the necessary columns with values as strings into integers so that we can be able to do our model fitting 

### 3.3 Fitting our model

This is necessary because it is to best capture the underlying patterns in the training data and with this we can accurately predict based on the input data

## 4.0 Evaluating our model

By using the Area Under the Curve we are able to plot the Receiver Operating Characteristics

#### 4.3.1 Conclusions for the models 

* With the numbers given from our train and test models 0.93 and 0.94 respectively establishes that our predictions are very accurate having a difference of only 0.01 

* Our model shows excellent performance with high AUC values for both training and testing. The slight difference suggests good generalization, but it’s always beneficial to look at additional metrics and the data distribution to ensure robust performance. 
* The fact that the test AUC (0.94) is slightly higher than the train AUC (0.93) suggests that your model may generalize well to unseen data. This is a positive sign, as it indicates that the model is not overfitting to the training data.
* The close proximity of the AUC values (0.94 vs. 0.93) indicates that the model's performance is consistent across both training and testing datasets. This consistency is crucial for ensuring that the model can reliably predict outcomes in real-world scenarios.
* Both the test AUC of 0.94 and the train AUC of 0.93 indicate that your model is performing very well. AUC values closer to 1.0 suggest excellent discrimination between the positive and negative classes.

  ### 4.4 Using Decision Trees

We are using Decision trees since are a valuable tool for modeling data due to their simplicity, interpretability, ability to handle various data types, and suitability for both individual use and ensemble methods

#### 4.4.1 Conclusions For the Decision trees

* The fact that the test AUC is slightly higher than the training AUC suggests that there's very little overfitting. This is a very positive sign, indicating that your model is not just memorizing the training data but actually learning the underlying patterns.
* The consistently high AUC scores across both training and test sets give us high confidence in the predictions our model makes. We can rely on its outputs for decision-making with a good degree of certainty.
* The combination of excellent model fit and strong generalization ability makes our model a strong candidate for more real-world applications. It's likely to perform well in scenarios where accurate predictions are crucial.

  ## 5.0 VALIDATING OUR DATA

By the use of precision and a confusion matrix we are able to validate our data

#### 5.1 Conclusions for our matrix and precision

a precision score of 0.7983 indicates that your model is performing well in identifying relevant instances, but there is potential for further enhancement. Focusing on improving this metric, along with others, can lead to a more robust and reliable model

* **True Positive** are the cases where the model correctly predicted class 1 (the positive class) when the actual class was also 1.
In our case the model correctly identified 190 samples as belonging to class 1.
* **True Negative** are the cases where the model correctly predicted class 0 (the negative class) when the actual class was also 0.
In our case the model correctly identified 546 samples as belonging to class 0.

The above shows a confusion matrix which shows us that the model is significantly better at predicting the 0 class than the 1 class. Evidence for this is:

High True Negatives (TN): 546 samples were correctly classified as class 0.
Lower True Positives (TP): Only 190 samples were correctly classified as class 1.
Class Imbalance: The model seems to overpredict class 0, suggesting a possible imbalance in the training data towards class 0.


## 6. CONCLUSION AND RECOMMENDATIONS 

### 6.1 Conclusion
**Strengths:**
High Accuracy: Your model demonstrates excellent performance with high AUC scores for both training and testing, indicating its ability to distinguish between arrest and no-arrest scenarios.
Good Generalization: The slightly higher test AUC compared to the training AUC suggests that your model generalizes well to new data, meaning it's not just memorizing the training set.
Consistent Performance: The similar AUC scores across training and testing datasets indicate reliable performance, suggesting your model will perform well in real-world scenarios.

**Weaknesses:**
Class Imbalance: The model exhibits a bias towards predicting "no arrest" due to an imbalance in the training data, with far more examples of Terry Stops that did not result in arrests.

**Consequences of Imbalance:**
False Negatives: The model might miss situations where an arrest is actually likely, potentially leading to unsafe situations.
Perceived Bias: The model might over-predict "no arrest" in situations where an arrest is less likely, potentially contributing to a perception of racial bias.

**Addressing the Weakness:**
Data Augmentation: Generate synthetic data to increase the number of "arrest" examples in your training data.
Oversampling/Undersampling: Adjust the class distribution by replicating "arrest" examples or removing some "no arrest" examples.
Class Weights: Assign different weights to each class during training to prioritize "arrest" predictions.

**Overall:**
By addressing the class imbalance, you can improve your model's accuracy and fairness, ultimately achieving your project goals of promoting transparency, reducing unnecessary arrests, and informing policy and training.

### 6.2 Recommendations
**Address Class Imbalance:**
Data Augmentation: Increase the number of examples for class 1 in the training data by using techniques like data augmentation (e.g., creating synthetic data similar to existing class 1 samples).
Oversampling/Undersampling: Adjust the class distribution by oversampling class 1 examples (replicating them) or undersampling class 0 examples (removing some).
Class Weights: Assign different weights to each class during training to give more importance to class 1.

**Evaluate Other Metrics:**
Precision, Recall, F1-Score: These metrics provide a more nuanced view of the model's performance, especially in the context of class imbalance.
ROC Curve: Visualize the model's performance across different thresholds to understand its ability to discriminate between classes.

**Consider Business Objectives:**
Cost of False Positives vs. False Negatives: Determine which type of error is more costly for your specific business problem. This can help you prioritize improving precision or recall.
Target Audience: Understand the needs of your target audience and how the model's predictions will be used. This can guide your efforts to improve the model's performance on specific aspects.

