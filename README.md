# Tanzanian Faulty Pumps Prediction
## Overview
Access to clean and potable water is crucial for the health and well-being of Tanzanian citizens. However, many water pumps across the country are faulty, leading to 
water shortages and posing significant health risks to communities. To address this issue, we aim to develop a predictive model that can identify faulty water pumps 
based on various features such as pump age, location, type, and condition. By accurately predicting faulty water pumps, authorities and organizations can prioritize 
maintenance and repair efforts, ensuring clean and safe water is readily available to all Tanzanians.

## Business Understanding
The Ministry of Water in Tanzania is a key stakeholder in addressing the issue of faulty water pumps. As the government body responsible for water resource management 
and infrastructure development, the Ministry plays a crucial role in ensuring water supply systems are well-maintained and functional. By leveraging predictive modeling, 
the Ministry can efficiently allocate resources for maintenance and repair activities, improving the reliability and accessibility of clean water for Tanzanian communities.

## Data Understanding
The dataset contains various features related to water pumps, including pump age, location, installer, and funding source. Our objective is to develop a predictive model 
to classify water pumps into functional, non-functional, and functional needs repair categories. Additionally, we aim to conduct exploratory data analysis to identify factors
influencing water pump functionality and maintenance needs. By analyzing historical data on water pump failures and repairs, we can optimize maintenance schedules and resource 
allocation, prioritize interventions in regions with high repair needs, and evaluate the impact of funding sources on water pump functionality.

## Modeling
The primary objective is to predict the functionality of water pumps based on historical data. Machine learning models excel at predictive tasks, allowing us to build accurate models that can generalize well to unseen data. This predictive capability is crucial for identifying non-functional pumps and ensuring timely maintenance or replacement.

To achieve this objective, we initially employed decision trees as a baseline model. Decision trees provide a straightforward approach to classification tasks and offer insights into feature importance. However, to enhance predictive accuracy and capture more complex relationships within the data, we also explored the use of random forests as an alternative model.

Random forests extend the capabilities of decision trees by aggregating multiple decision trees and mitigating overfitting. By leveraging the ensemble of trees, random forests can provide robust predictions and handle high-dimensional datasets effectively. This approach allows us to capitalize on the strengths of both decision trees and random forests to develop models that accurately predict water pump functionality and generalize well to new data.

### Baseline Model
### Decision Tree Classifier

#### Training and Prediction

**Training Data**: Features and labels are separated, where features are obtained by dropping the target columns ('status_group_functional', 'status_group_non functional') from the training data.
**Test Data**: Test data is prepared by aligning the columns of the test dataset with the training dataset and filling missing values with 0.
**Model Fitting**: A Decision Tree classifier (clf) is trained using the training data.
Prediction: The trained classifier makes predictions on the test set, providing binary predictions for the functional and non-functional states of the water pumps.
Cross-Validation

**Model Evaluation**: The performance of the Decision Tree classifier is assessed using 5-fold cross-validation on the training data.
Scoring Metric: Accuracy is used as the evaluation metric during cross-validation.
Cross-Validation Scores: The accuracy scores of the classifier on each fold of cross-validation are recorded.
**Mean Accuracy**: The average accuracy across all folds indicates the overall performance of the classifier.
Standard Deviation: The standard deviation of accuracy scores reveals the consistency of the model's performance across different folds.

**Interpretation**
The Decision Tree classifier achieved a mean cross-validation accuracy of approximately 0.774 with a standard deviation of 0.004. These results indicate the model's capability in predicting the condition of water pumps, considering both functional and non-functional states. 


### Alternative Models
### Random Forest Classifier

**Random Forest Cross-validation Scores**:
The Random Forest classifier was evaluated using cross-validation on the training data. The obtained cross-validation scores are as follows:

**Cross-validation scores**: [0.8165, 0.8189, 0.8113, 0.8116, 0.8113]
Mean CV accuracy: 0.8139
Standard deviation of CV accuracy: 0.0032
**Test Set Predictions**:
The model made predictions for the test set, providing insights into its performance on unseen data:

**Predicted labels for the test set**: [[ True False], [ True False], [ True False], ..., [ True False], [ True False], [False True]]
These predictions indicate the model's classification for each data point in the test set, where True represents one class and False represents the other.

**Implications**:
The Random Forest classifier demonstrates a mean cross-validation accuracy of approximately 81.39%, indicating reasonable performance on unseen data.
With a low standard deviation of cross-validation accuracy, the model exhibits consistent performance across different folds of the training data.
Comparatively, the Random Forest classifier outperforms the Decision Trees model, achieving a higher mean cross-validation accuracy and lower standard deviation.
Further improvements to the Random Forest classifier's performance are explored through hyperparameter tuning.




