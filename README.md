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

First, we shall import the necessary libraries to facilitate our workflow.

# Importing the necessary libraries
import numpy as np
import pandas as pd
from matplotlib import pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from imblearn.over_sampling import SMOTE
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import GridSearchCV
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import precision_recall_curve, average_precision_score
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, roc_auc_score, confusion_matrix, classification_report,roc_curve, auc
%matplotlib inline


