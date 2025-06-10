# SyriaTel-Churn
A project about a telecommunications company in need of predictive models capable of proactively reducing churn 


# Business Understanding
Churn is a one of the biggest problems in the telecom industry.

For Telecom companies it is important to attract new customers and at the same time prevent old ones from leaving their companies. There are different reasons why customers may choose to terminate their contracts, including pricing, poor customer service, change in customer preference, among others.

Due to the direct effect of churn on revenues, telecom companies apply machine learning models to predict churn on an individual customer basis and take countermeasures such as discounts, special offers, or other measures to keep their customers. Finding factors that contribute to customer churn is important so as to take the necessary actions in order to reduce this churn.


# Data Understanding
The dataset contains data on the customers of a Telecom company. Each row represents a customer and the columns contain customer’s attributes which are described in the following:

state – The U.S. state where the customer lives.

account length – How long the customer has had an account, in days.

area code – The area code of the customer's phone number.

phone number – The customer's phone number

international plan – Whether the customer has an international calling plan.

voice mail plan – Whether the customer has a voicemail plan.

number vmail messages – Number of voicemail messages the customer has.

total day minutes – Total minutes the customer spent on calls during the day.

total day calls – Total number of calls made during the day.

total day charge – The cost of the daytime calls.

total eve minutes – Total minutes of evening calls.

total eve calls – Number of evening calls.

total eve charge – The cost of the evening calls.

total night minutes – Total minutes of night-time calls.

total night calls – Number of night-time calls.

total night charge – The cost of the night-time calls.

total intl minutes – Total minutes of international calls.

total intl calls – Number of international calls.

total intl charge – Cost of international calls.

customer service calls – Number of times the customer called customer service.

churn – Whether the customer left the service (TRUE) or stayed (FALSE).

The dataset itself can be found here - https://www.kaggle.com/becksddf/churn-in-telecoms-dataset

# Modelling

# Logistic Regression Model

Despite its name, a Logistic Regression is actually a classification algorithm and not regression. It is used when the target variable is categorical.

It predicts the probability that a given input belongs to a certain class.

A logistic regression is simple, fast and easy to interpret.

**After creating the model**


**ROC Curve (Receiver Operating Characteristic Curve)**

The ROC curve is a plot that showing how well a classifier can distinguish between two classes, positive and negative, at various thresholds.

AUC (Area Under the Curve) AUC stands for Area Under the Curve of the ROC.

It basically summarizes the performance of the model into a single number.

Key AUC Values:

1.0 = Perfect classifier

0.5 = Similar to random guessing

< 0.5 = Worse than random as it could be an inverted classifier

The higher the AUC, the better the model is at distinguishing between the classes.

It is very helpful especially when the classes are imbalanced, just like in our target.

![image](https://github.com/user-attachments/assets/853524f7-3a4a-44e5-a2b3-b47fb017c1ab)

**ROC AUC Curve Interpretation**

AUC (Area Under the Curve) = 0.79

This means that The model can distinguish between churners and non-churners 79% of the time.

This is a decent performance and suggests that the model is quite effective at identifying potential churners.

The curve is above the diagonal by quite much, especially at lower false positive rates.

This suggests the model performs well at distinguishing classes with a low error rate in that region.


# Model Performance
Accuracy: 0.8576

The model correctly predicts churn vs. no churn 85.76% of the time.

This may seem high, but can be very misleading due to class imbalance as most customers do not churn. That means that even a model that predicts “no churn” all the time can get high accuracy.

Precision for class 1 (churn): 0.5185

Of all customers predicted to churn, 51.85% actually did.

There is a decent chance the model will falsely flag some customers as churners (false positives). However, this may be beared with if the cost of retaining non-churners is lower than losing churners.

Recall (churn): 0.2887

Only 28.87% of actual churners were correctly identified.

Very low recall, which is a major concern. Over 70% of the customers who actually churned are missing. For this churn model, recall is more important than precision as we want to catch as many churners as possible for intervention.

F1 Score: 0.3709

This is the harmonic mean of precision and recall. It is low because recall is low.

The model’s balance between catching churners and being accurate when it does is not strong.

ROC AUC Score: 0.7897

This is the overall ability to discriminate between churners and non-churners.

It is quite decent (closer to 1 is better), which suggests that the model does have some underlying signal.

Confusion Matrix:

True Negatives (TN): 544

False Positives (FP): 26

False Negatives (FN): 69

True Positives (TP): 28

Implication:

We are catching only 28 churners but missing 69, which is concerning for a retention strategy.

Classification Report:

Class 0 (no churn): High precision, recall, F1 (model is very good at predicting who non-churners)

Class 1 (churn): Lower performance across the board

Business Implications

Retention Strategy Risk:

If this model is used to guide customer retention efforts, a large portion of churners will definately be missed as it may not act on customers who are actually at risk of churning.

Cost-Effectiveness:

Intervening on false positives (non-churners predicted as churners) could waste some resources, but this may be more acceptable than missing true churners.

To Summarize:

The model is highly accurate overall, but massively underperforms in detecting actual churners.

Recall on churn is too low for it to be effective at all in preventing loss of customers.

# Decision Tree Classifier

A Decision Tree Classifier is a type of learning algorithm used for classification tasks. It works by splitting a dataset into branches based on feature values then forming a tree-like structure that leads to a final prediction.

A decision tree classifier is easy to understand and visualize, handles both numerical and categorical data and requires minimal data preprocessing.

**After creating the model**

# Model Evaluation

Accuracy - 0.8621

86.2% of predictions are correct which is a small improvement over logistic regression (85.8%).

Precision (churn) - 0.5210

When predicting a customer will churn, the model is correct 52% of the time.

Recall (churn)- 0.6392

When predicting a customer will churn, the model is correct 52% of the time.

F1 Score - 0.5741

Balanced score between precision and recall, also significantly improved from the 0.37 of the logistic regression.

ROC AUC Score - 0.7791

It is slightly lower than the logistic regression's 0.7897, but still decent and indicates the model separates classes well enough.

Churn (class 1) is handled much better now as:

A Recall of 0.64 means we are catching nearly 2 out of every 3 churners.

A Precision of 0.52 is similar to before, which means some non-churners are still misclassified, but is still tolerable.

As for the Confusion matrix:

We can now correctly identify 62 churners, as compared to only 28 in the logistic regression.

False positives, 57, are higher than before, 26, but this is a trade-off for catching more churners than before.

False negatives, 35, are much less than in logistic regression, 69.

Positive Implications on Churn Management

Now were catching almost 2/3 of churners. This is much more actionable for retention efforts.

Still maintaining a decent precision, meaning interventions may not waste too many resources on false churn predictions.

Negative Implication

Slight increase in false positives, non-churners predicted to churn. If the intervention is costly, this might require careful budget management or prioritizating based on the probability of churn.

Therefore:

The decision tree model performs significantly better in terms of recall and F1 score, which are critical for churn problems.

The next thing is to tune the decision tree for better performance.

Now we apply hyperparameter tuning via GridSearchCV to the Decision Tree model, thus optimizing for F1 Score.

GridSearchCV is used to automate the process of hyperparameter tuning for machine learning models. It finds the best combination of hyperparameters for a model. This is done by attempting all possible combinations in a grid, evaluating them using cross-validation then returning the combination that performs best.


**After tuning the model**

![image](https://github.com/user-attachments/assets/3c40ff4b-41d8-4f6e-9d57-f3fea1d65e0f)


**ROC AUC Curve Interpretation**

AUC (Area Under the Curve) = 0.80

This means that the model can distinguish between churners and non-churners 80% of the time.

This is good performance and suggests the model is slightly more effective at identifying potential churners.

The ROC curve shows a steep rise adjacent to the top-left corner, which indicates:

High true positive rate - model catches most churners early

Low false positive rate - fewer mistakes in flagging non-churners

# Model Evaluation

Accuracy - 0.8456

84.6% of predictions are correct. Slightly lower than before which is a trade-off for higher recall.

Precision (churn) - 0.4795

47.95% of predicted churners actually churn which is slightly lower than earlier models.

Recall (Churn) - 0.7216

A huge improvement as nearly 3 out of 4 actual churners correctly identified.

F1 Score (Churn) - 0.5761

The best overall balance of precision and recall across all the models.

ROC AUC Score - 0.7964

This is the best ROC AUC indicating the strongest separation ability between churners and non-churners.

The Churn class has been handled best as:

A small dip in precision for churn class compared to untuned decision tree.

There is a major gain in recall as the the model now captures 72% of churners, up from 64% previously and 29% in logistic regression.

Churner detection seems to be highly effective.

Confusion Matrix

Best true positive count so far as 70 churners are caught.

False negatives (27) are lowest so far which is better than 35 (untuned Decision Tree) and 69 (Logistic Regression).

False positives (76) increased, though it is expected when prioritizing recall.

Business Implications for Churn Prediction

Strengths

Best recall so far (72%) — we are now catching most of the at-risk customers.

Still maintaining a similar precision, meaning customer interventions won’t be excessively wasted on non-churners.

Highest AUC — indicates that this model is best at ranking customers by churn risk.

Weakness

More false positives — 76 customers flagged as churners who are not. This could slightly burden retention resources.

However, if churn costs more than a retention campaign, the trade-off could be worth it.


# Feature Importance

![image](https://github.com/user-attachments/assets/520c170b-f7c8-4e1f-9090-cee4987a040d)

This is a feature importance chart that displays the features most influencing the decision tree’s ability to predict customer churn.

The top most influential features are:

**total day charge**

Customers with higher daytime call charges are more likely to churn.

This could indicate frustration due to high daytime usage costs especially if users don’t perceive value for their money or if competitors offer better deals.

*Recommendation*

Segment customers with high day charges and monitor their satisfaction or churn risk.

Offering loyalty discounts, tiered plans, or flat-rate unlimited day calling may reduce pressure from pricing.

Consider campaigns that educate customers on optimizing their usage to lower perceived charges.

**customer service calls**

A high number of service calls is a strong churn indicator.

Frequent calls to customer service probably indicates dissatisfaction or unresolved issues. It seems to be a clear early warning signal of churn, such that if they aren't addressed quickly, they are likely to leave the service

*Recommendation*

Take note of users with multiple service calls in a short window as high risk.

Use predictive churn scores to trigger proactive customer support follow-ups, for example "We noticed you've contacted us multiple times — is there anything we can fix?"

Track the efficiency of customer service resolution and improve on it.

**total eve charge**

Evening call charges also contribute meaningfully to churn prediction.

This reinforces that the overall pricing structure is a driver of churn, not just peak-hour rates.

*Recommendation*

Create time-based promotions, for example, unlimited evening or weekend calling to reduce the perceived cost.

Add alerts or reminders for nearing plan limits or high evening usage to reduce the feeling of surprise bills on customers.

**voice mail plan**

Having or lacking voicemail services may reflect customer preferences and expectations about the completness of service.

Voice mail plan availability might be linked to customer satisfaction and perceived professionalism of service.

*Recommendation*

Survey users with and without voicemail to understand usage and importance.

If voicemail is underused but predictive of retention, include it in all plans as a perceived addition of value.

**account length**

This is one of the least important features to the model, meaning that long time customers aren't necessarily more loyal.

Churn is influenced more by recent behaviour than how long a customer has subscribed to the service.

Customers who show signs of dissatisfaction should be targeted, not just new customers or "at-risk segments" based on tenure.


# Conclusion

The objective was to predict customer churn using available customer service and usage data, and to identify key drivers of churn to support proactive retention strategies.

Among the models tested Logistic Regression, Decision Tree, the Decision Tree achieved the best balance between recall and precision, especially in identifying churners, with an ROC AUC of 0.80 and a recall of 0.72.

Total day charge and customer service calls were the most impertant features in predicting churn, suggesting that high pricing and customer dissatisfaction are the main drivers of churn.

Customers with high call charges and/or frequent customer service calls should be prioritized for retention strategies. Furthermore, plan pricing and service quality should be assessed to reduce triggers behind churn."

For even better model performances:

Try advanced models like XGBoost and Random Forest.

Use more recent data, or data that has more features to manipulate.

Build a real-time churn alert system.

The models built show encouraging results in churn prediction, especially when referring to decision trees with tuned hyperparameters. With proper deployment and thorough monitoring, the system could significantly improve customer retention efforts as they can zero in at-risk customers early.

