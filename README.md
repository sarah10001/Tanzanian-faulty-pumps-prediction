[Link to Pump Functionality Prediction PDF](https://github.com/sarah10001/Tanzanian-pump-functionality-prediction/blob/main/Pump%20functionality%20prediction.pdf)


# Tanzanian water pump functionality prediction
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
influencing water pump functionality and maintenance needs. By analyzing historical data on water pump failures and repairs, we can optimize maintenance schedules and resource allocation, prioritize interventions in regions with high repair needs, and evaluate the impact of funding sources on water pump functionality.

### Distributions before and after log transformation
![Distribution before log transformation](![distribution before log transformation](https://github.com/sarah10001/Tanzanian-pump-functionality-prediction/assets/151674519/6c74ea99-d176-490c-9090-7eaad5dc12db)

![Distribution after log transformation](![distribution after log transformation](https://github.com/sarah10001/Tanzanian-pump-functionality-prediction/assets/151674519/f4a3c454-99ec-47e9-b2ed-a7395027061c)


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

![Decision Trees Importance Feature Diagram](https://github.com/sarah10001/Tanzanian-pump-functionality-prediction/assets/151674519/158fbd2d-6453-4011-9c60-c02bda658499)
![Decision Trees Importance Feature Diagram](![decision tree model viz](https://github.com/sarah10001/Tanzanian-pump-functionality-prediction/assets/151674519/16410a01-a91c-4f4b-bf2a-4f000461ac0a)
)


### Alternative Models
### Random Forest Classifier

#### Random Forest Classifier Performance and Feature Importamodel visualizationnce

##### Model Training and Prediction

- **Cross-Validation Scores**: The Random Forest classifier achieved the following cross-validation scores on the training data:
  - [0.8219, 0.8192, 0.8155, 0.8137, 0.8175]
  - Mean CV accuracy: 0.8176
  - Standard deviation of CV accuracy: 0.0028

- **Test Set Predictions**: The model predicted labels for the test set, indicating whether water pumps are functional or non-functional.

##### Implications
- The mean cross-validation accuracy of approximately 81.76% suggests the model performs well on unseen data.
- Low standard deviation indicates consistent performance across different folds.

#### Feature Importance Analysis

##### Decision Trees
- **Extraction Type (0.45)**: Highest importance, reflecting the significant impact of extraction methods on water point functionality.
- **Payment (0.12)**: Second most important, indicating payment modes' influence on functionality.
- **Construction Year (0.12)**: Age of water points affects functionality.
- **Source (0.1)**: Water source significantly affects functionality.
- **Water Quality (0.1)**: Quality of water provided impacts functionality.
- **Funder (0.04)**: Different funders have varying impacts.
- **Geographic Features**: Latitude, region, longitude, and GPS height contribute to understanding spatial patterns.

##### Random Forest
- **Latitude (0.2) and Longitude (0.2)**: Strong spatial patterns observed.
- **Funder (0.125)**: Funding organization's influence.
- **Construction Year (0.125)**: Year of construction remains significant.
- **GPS Height (0.125)**: Elevation impacts functionality.
- **Extraction Type (0.085) and Payment (0.055)**: Varying importance but still influential.
- **Other Features**: Region, source, and water quality also contribute.

#### Conclusion
- Both models reveal complex factors influencing water pump functionality.
- Understanding these factors can inform interventions to improve water access and infrastructure maintenance, particularly in regions with water access challenges.

![Random Forest Feature Importance Diagram](https://github.com/sarah10001/Tanzanian-pump-functionality-prediction/assets/151674519/dc8743f1-cbdf-48e5-90ab-4874934df557)
![Random Forest model viz](![random forest model viz](https://github.com/sarah10001/Tanzanian-pump-functionality-prediction/assets/151674519/5205364c-9d90-4e43-81fe-f995fe76b143)


### Decision Tree Classifier Model Tuning

#### Untuned Decision Tree Model:
- **Cross-validation Scores**: Ranged from approximately 0.772 to 0.779.
- **Mean CV Accuracy**: Around 0.775.
- **Standard Deviation of CV Accuracy**: Approximately 0.0029.

#### Tuned Decision Tree Model:
- **Best Parameters**: max_depth of 20.
- **Best Cross-validation Score**: Approximately 0.783.
- **Mean CV Accuracy with Best Parameters**: Around 0.783.
- **Standard Deviation of CV Accuracy with Best Parameters**: Approximately 0.0014.

### Summary:
- The tuned decision tree model with a max_depth of 20 outperformed the untuned model.
- It achieved higher accuracy and showed more consistent performance across different folds of cross-validation.

### Random Forest Classifier Model Tuning

#### Best Parameters:
- **max_depth**: 30

#### Best Cross-validation Score:
- 0.8113636363636364

#### Cross-validation Scores:
- [0.81585859, 0.80873737, 0.80914141]
- **Mean CV accuracy**: 0.8112457912457912
- **Standard deviation of CV accuracy**: 0.0032659064864030587

#### Test Set Predictions:
- **Predicted labels for the test set using the best model**: [[ True False], [ True False], [ True False], ..., [ True False], [ True False], [False  True]]

### Conclusion:
The tuned random forest classifier, with a max_depth of 30, achieved a mean cross-validation accuracy of approximately 81.12%. Despite a slightly lower accuracy than the default random forest model, it outperforms other models evaluated, including the decision tree classifier and the tuned decision tree model. The tuned random forest exhibits stable performance across different folds, making it the recommended model for practical applications due to its robustness and accuracy in predicting water pump functionality.

![tuned random forest model viz](![tuned random forest viz](https://github.com/sarah10001/Tanzanian-pump-functionality-prediction/assets/151674519/056411a5-f5c2-42d9-ae3c-ea91e2fa0c51)

### Recommendations for Improving Water Pump Functionality

1. **Implement Routine Maintenance Programs:**
   - **Action:** Establish regular inspection and maintenance schedules for water pumps, including checks on mechanical components and water quality.
   - **Benefits:** Timely detection and repair of faults can prevent breakdowns, ensuring continuous access to clean water for communities.

2. **Target High-Risk Regions:**
   - **Action:** Utilize geographic data to identify regions with a high prevalence of non-functional water pumps.
   - **Benefits:** Target interventions, such as repair and rehabilitation efforts, to areas with the greatest need, optimizing resource allocation and impact.

3. **Introduce Flexible Payment Plans:**
   - **Action:** Introduce flexible payment options for water services, including subsidized or tiered pricing models based on income levels.
   - **Benefits:** Improve affordability and accessibility of water services, reducing the financial burden on low-income communities and increasing revenue for maintenance and infrastructure upgrades.

4. **Foster Collaboration with Funders:**
   - **Action:** Engage with funders and donor organizations to align priorities and strategies for water infrastructure projects.
   - **Benefits:** Secure long-term support and investment in water projects, leveraging partnerships to access funding for maintenance, upgrades, and capacity-building initiatives.

5. **Embrace Data-Driven Decision Making:**
   - **Action:** Invest in robust data collection systems and analytics capabilities to track water pump functionality and performance metrics.
   - **Benefits:** Enable evidence-based decision making, including trend analysis, predictive maintenance, and resource allocation based on real-time insights, leading to more effective and efficient management of water infrastructure.

### Conclusion

In conclusion, the project has provided a comprehensive exploration of predicting water pump functionality and optimizing maintenance strategies. By leveraging machine learning techniques and data analysis, we have gained insights into the factors influencing water pump functionality, identified high-risk regions, and proposed actionable recommendations for improving access to clean water. Through collaborative efforts and data-driven decision-making, we aim to contribute to the sustainable management of water infrastructure and ensure the well-being of communities relying on these vital resources.

