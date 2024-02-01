# Comparing Classifiers

### Overview
This report covers the process and results of building a classification model to determine financial marketing results.

The notebook used to build this analysis comes from this link:

The dataset comes from the UCI ML repo: https://archive.ics.uci.edu/dataset/222/bank+marketing

### Problem Statement
An increase in the number of marketing campaigns has decreased their overall effectiveness with the public. As a response, aggressive, direct marketing campaigns have become more common place. Our business objective is increase campaign efficiency by building a model that can explain the success of a contact, measured by whether the consumer subscribed to a deposit offered by our bank. According to Problem 5, we will be using the 7 bank column attributes in our modeling to see which of these 7 attributes have an impact on our acceptance rate.

### Approach
Our approach here was to use the CRISP-DM framework to produce and compare four classification models that will be used to predict whether a consumer contact led to a subscription in a financial product offered by our bank.
The CRISP-DM approach entails:
* Understanding the business problem
* Understanding the data
* Preparing the data for modeling (handling bad values and feature engineering)
* Modeling the data
* Evaluating the models
* Deploying

The business problem was straightforward, and established a clear objective.

The data required significant prepping, including imputing values that would skew our predictions, as well as dropping missing values.
Ultimately we selected 7 relevant values for our analysis:
1. age
2. type of job
3. marital status
4. education
5. whether they have credit in default
6. whether they have housing loan
7. whether they have personal loan

We performed additional feature engineering on these columns, encoding some to change them from categorical to numeric. 
Finally we ran this data through four models, evaluated them based on accuracy and performance (time), and then tuned them for improved accuracy.
We also considered the performance of the models for recall, to help us avoid false positives. We did this so that we could see which model decreases false positives, meaning we are less likely to sink a lot of investment into consumers who will actually not subscribe.

### Results
We selected a baseline "model" with which we could compare our classifier models. In this case, the baseline was simply the majority class, which is to say it is the % of "no's" from the original dataset.
"Model" is in quotes here because it is not a model--it only represent something that can be known after the fact.

The good news is that all models are very close to the majority classifer; unfortunatley they are all just underperforming that benchmark:


Actually, performance is better on the training accuracy than the test accuracy, implying some level of overfitting. In other words, these models might be too complex for the data! Or in other words, the dataset is imbalanced, with the "no's" being a dominant class.

Given that we can rely on measuring performance by "precision", which is a good way to avoid false positives and save on time investment.
From this perspective, Decision Tree had the best performance with 91% precision.
Again, precision measures the ratio of true positives to all positives identified. 
In business terms, it means that of the "yes's" that the model predicts, 91% of these are true "yes's"--a very good precision score!

### Recommendation(s)

Based on these findings, we have several recommendations.
1. Acquire more data in order to improve the "accuracy" findings of the models
    * The ratio of "no's" to "yes's" was so imbalanced that it is difficult to beat a simple majority classifier
    * Resampling is also an option of new data is not available
2. Spend additional time engineering features to decrease complexity of model and get higher accuracy score
3. Try additional models such as Random Forests or Naive Bayes

In terms of useful business knowledge, we can use a decision tree model to effectively target consumers so that we don't waste money targeting users who seem like they will subscribe, but actually will not.

### Next Steps
As mentioned, I believe there is some business value to proceed with deploying a decision tree model.
However, in spirit with the CRISP-DM framework, we should refine our attempts to find a model with high precision and high recall, whether by additional feature engineering or by acquiring more useful data.
