+++
author = "Sreehari Rajamohan"
title = "Demystifying Model Performance: Understanding Accuracy"
date = "2024-04-02"
description = "This article discuss about Accuracy method used for model performance evaluation"
tags = [
    "Machine Learning",
    "Beginner",
    
]
categories = [
    "Machine Learning",
  
]
series = ["Themes Guide"]
aliases = ["migrate-from-jekyl"]
+++

In this article we will discuss how to measure the performance of a machine learning model using Accuracy method.

<!--more-->

# 1. Accuracy

It is one of the simplest technique to measure the performance of a model. It is used for measuring the performace of the classification models. The accuracy value lies between 1 and 0. 1 being the best and 0 the worst.

$$
 Accuracy = \frac{\text{Number of classification done correctly } }{\text{Total classification instances in the test set}}
$$

## Example

Lets suppose we have a dataset of 100 images.

- 60 images of cat
- 40 images of dog
- task = classify the images to cat and dog
- we created a machine learning model and it made the classification as below

{{< table title=" " >}}

| Images | Total | Correct Prediction | Incorrect Prediction |
| :----: | :---: | :----------------: | :------------------: |
|  Cat   |  60   |         55         |          5           |
|  Dog   |  40   |         36         |          4           |

{{< /table >}}
<br>

$$
 Accuracy = \frac{\text{Number of classification done correctly } }{\text{Total classification instances in the test set}}= \frac{ 55+36}{100} = 91 \\%
$$

<br>

### Issues

1.  <b>Failure with imbalanced data</b>

    If data is imbalanced "Accuracy" method will not serve the purpose. Lets suppose in our previous example there are 90 images of cat rather than 60 and 10 images of dog instead of 40.
    Now we create a "Stupid" algorithm which will classify any image given as cat.
    In that case, if our new dataset is given as input, the model will classify

    - 90 images correctly
    - 10 images incorrectly
    - Accuracy = 90\%

    So Accuracy should never be used as a measure of performance machine learning model with imbalanced data.

2.  <b>Failure with Probability Score Interpretation</b>  
    Accuracy is not the suitable model to evaluate the model that return probability scores. Lets understand this with an example  
    <br>
    We have two models Model 1 and Model 2 which returns probability as its output. <div>The condition to calculate the predicted labels **y_pred_1** and **y_pred_2** is such that any value > 0.5 is considered as 1 and any value <0.5 is considered as 0.

    ![alt text](/accuracy_1.png)

    If we compare, model_1 and model_2, both have the same accuracy value.
    But through observation, we can understand that model_1 is better than model_2.</div><b>
    so Accuracy cannot use be used as a performance measure for models that returns probablity scores</b>

{{< highlight go "linenos=table,hl_lines=8 15-17,linenostart=199" >}}
// Python
from sklearn.metrics import accuracy_score

y_true = [1, 1, 0, 1, 0] # True labels
y_pred = [1, 1, 0, 1, 0] # Predicted labels

accuracy = accuracy_score(y_true, y_pred)

print("Accuracy:", accuracy)
{{< / highlight >}}
