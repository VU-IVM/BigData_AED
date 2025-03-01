---
jupytext:
  cell_metadata_filter: -all
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Lecture: Introduction to Artificial Neural Networks and model validation

This week we will focus on the basic concepts of machine learning and how we can develop a simply machine learning model.

`````{admonition} Learning objectives week 3
:class: important
- Understand the concept of Artificial neural networks.
- Understand and know how you can apply an artificial neural network model in Python. 
- Know how to validate and interpret your results.
`````

## Artificial neural networks

Artificial Neural Networks (ANNs, or simply "neural nets") are computational models inspired by the structure and function of biological neurons. ANNs consist of interconnected processing nodes or "neurons" that are organized into layers, which are used to process information and make predictions.

In an ANN, information is passed from one layer to another through the connections between the neurons, with each neuron applying mathematical transformations to the input it receives. The weights and biases of the connections between the neurons are adjusted during training to minimize a predefined *loss function*, which measures the difference between the model's predictions and the actual values (much like in linear regression when the model minimizes the sum of the squared residuals).

Once trained, an ANN can be used to make predictions by passing input data through the network and computing the output values produced by the final layer. ANNs have been applied in a wide range of fields, including image classification, speech recognition, natural language processing, and forecasting, among others.

### ANNs for classification and regression

ANNs used for classification are designed to categorize input data into one or more predefined classes. They have an output layer with one or more nodes that use a non-linear activation function, such as the *softmax* function, to produce a probability distribution over the classes. The final prediction is made based on the class with the highest predicted probability.

In contrast, ANNs used for regression are designed to predict continuous target values based on input data. They have a single output node with a linear activation function and are trained to minimize the difference between the predicted values and the true target values.

The architecture and training process for each type of neural network will vary depending on the problem being solved.

### What are the advantages of using ANNs?

ANNs are widely used because they offer several advantages, including:

1.  Flexibility: ANNs can handle a wide range of problems, including both linear and non-linear problems, and can be used for both supervised and unsupervised learning.

2.  Scalability: ANNs can handle large amounts of data and can easily be scaled up or down, depending on the complexity of the problem.

3.  Non-linear modeling: ANNs are capable of modeling complex, non-linear relationships between inputs and outputs, which makes them well suited for solving problems with intricate relationships.

4.  Automated feature learning: ANNs can automatically learn relevant features from raw data, which makes them well suited for solving problems where the input features are not well understood.

5.  Robustness: ANNs are robust to missing and noisy data, which makes them well suited for real-world applications.

6.  Ability to generalize: ANNs can generalize from the training data to make accurate predictions on unseen data, which is an important property for many applications.

### What are the disadvantages of using ANNs?

While powerful, ANNs are not perfect. Some disadvantages of using ANNs are:

1.  Complexity: ANNs can be complex and difficult to understand, particularly ANNs with many hidden layers. This can make it challenging to diagnose problems with the model or to interpret (or even trust) its predictions. Such "lack of transparency" can be a concern in applications where the results of the model must be auditable or explainable.

2.  Data requirements: ANNs require large amounts of high-quality training data to produce accurate results. If the training data is limited, noisy, or biased, the model may not perform well.

3.  Overfitting: ANNs are prone to overfitting, which means they may fit the training data "too well"and perform poorly on testing data. This can be addressed through techniques such as *regularization* and *early stopping*, but it requires careful monitoring of the model performance during training.

4.  Computational cost: ANNs can be computationally expensive to train, especially ANNs with many parameters. This can make it challenging to train the model on large datasets or to run the model in real-time applications.

5.  Difficulty in feature selection: ANNs are designed to automatically extract relevant features from the input data, but this process can be difficult to control. In some cases, the model may extract features that are not meaningful or even that harm the performance of the model.

### Types of ANNs

There are several different types of ANNs, some of the most common are:

1.  **Feedforward Neural Networks:** These are the most basic type of ANNs and consist of an input layer, one or more hidden layers, and an output layer. The information flows only in one direction, from the input layer to the output layer, without looping back.

2.  **Convolutional Neural Networks (ConvNets or CNNs):** These are specialized ANNs designed for image recognition and processing. ConvNets use convolutional layers to scan an image and extract relevant features, which are then processed by dense layers to make predictions.

3.  **Recurrent Neural Networks (RNNs):** These are ANNs designed to process sequences of data, such as time series or sequences of words in natural language processing. RNNs use feedback connections to pass information from one step of the sequence to the next.

4.  **Autoencoders:** These are a type of ANN used for unsupervised learning, where the goal is to reconstruct the input data. Autoencoders consist of an encoder that maps the input to a lower-dimensional representation and a decoder that maps the representation back to the original input.

5.  **Generative Adversarial Networks (GANs):** These are a type of ANN used for generating new data that resembles a given training set. GANs consist of two ANNs, a generator and a discriminator, that are trained simultaneously in a zero-sum game framework.

These are some of the most widely used types of ANNs. However, there are many other specialized variants and hybrid models that have been developed (and many more that are currently under development) for specific applications.

### ANNs and Deep Learning

Deep learning is a subfield of machine learning that focuses on using ANNs with many layers, known as *deep neural networks*. The term "deep" refers to the number of layers in the network, which can range from dozens to hundreds or even thousands. Deep learning algorithms have been particularly successful in solving problems in computer vision, natural language processing, and speech recognition.


## Model validation

Model validation is the process of evaluating a model's performance on a set of data it has not seen during training. The goal of validation is to assess how well the model can generalize to unseen data and make accurate predictions. It provides an estimate of the model's performance in real-world scenarios and helps to prevent *overfitting*, which occurs when a model is too closely fit to the training data and does not generalize well to new data.

There are several common methods for model validation, including:

1.  **Holdout validation:** the dataset split into two parts: *training* set and *validation* (testing) set. The model is trained on the training set and evaluated on the validation set, which is used as an unbiased estimate of the model's performance on unseen data. This helps to prevent overfitting and choose the best model based on performance on the validation set.

2.  **K-fold cross-validation:** the training data is divided into K equal parts (or "folds"). The model is then trained on K-1 folds and evaluated on the remaining fold, with this process being repeated K times so that each fold is used for evaluation once. The performance of the model is estimated as the average of its predictions on the K validation folds. This method provides a more robust estimate of the model's performance compared to a simple holdout validation, as it uses all of the training data for both training and validation. K-fold cross-validation is a widely used validation method in machine learning and is especially useful for larger datasets.

3.  **Leave-One-Out Cross-Validation (LOOCV):** a single data point is left out as validation data and the model is trained on all the other data points. This process is repeated for each data point, resulting in a model evaluation for each data point. LOOCV is a very thorough validation method, but also computationally expensive and time-consuming, making it less commonly used than other methods.

4.  **ROC and AUC:** ROC (Receiver Operating Characteristic) is a graphical representation of the performance of a binary (e.g., yes/no) classifier model. It plots the *true positive rate* (sensitivity) against the *false positive rate* (1-specificity) at various threshold settings. AUC (Area Under the ROC Curve) is a single scalar metric that summarizes the overall performance of a classification model. It represents the area under the ROC curve, which provides a visual representation of the model's discrimination ability. A perfect classification model has an AUC of 1, while a random model has an AUC of 0.5. AUC is a widely used metric for evaluating binary classification model.

The choice of validation method depends on the specifics of the **data** and the **model**, but it is important to carefully evaluate the model's performance on independent data in order to ensure that it is reliable and generalizes well to new data.

### Key concepts involving model validation

#### **Overfitting and underfitting**

These are common problems in machine learning where a model performs well on the training data but poorly on new, unseen data. **Overfitting** occurs when a model is too complex and fits the noise in the training data rather than the underlying patterns. This can lead to a model that has a low training error but a high testing error, indicating that it is not generalizing well to new data. Overfitting is often caused by having too many features or a model with too many parameters relative to the size of the training set.

In contrast, **underfitting** occurs when a model is too simple and does not capture the complexity of the relationship between the features and the target variable. This can lead to a model with a high training error and a high testing error, indicating that it is not fitting the training data well and is not generalizing to new data. Underfitting is often caused by having too few features or a model with too few parameters relative to the size of the training set.

Both overfitting and underfitting can be addressed by using techniques such as *regularization*, *feature selection*, and *early stopping*, as well as by increasing the size of the training set or using a more complex model with more parameters. The goal is to find a model that has a good balance between fitting the data well and generalizing to new data:

**-Regularization** adds a penalty term to the *loss function* that the model is trying to minimize, which discourages the model from assigning too much importance to any one feature.
**-Early stopping** involves monitoring the performance of the model on a validation set during the training process and stopping the training when the performance on the validation set stops improving or starts to deteriorate. The idea behind early stopping is to strike a balance between training the model long enough to capture the underlying patterns in the data, but not so long that it starts to fit the noise in the data.
**-Feature selection** is the process of selecting a subset of the most relevant and informative features from the dataset to use in building a machine learning model. It is a crucial step in the modeling process as it can significantly impact the model's performance, reduce the risk of overfitting, and increase interpretability.

#### **Cross-validation**

This is a process of dividing the dataset into several parts and training the model on different parts while testing it on the remaining parts, in order to get an estimate of the model's performance on unseen data.

#### **Performance metrics**

There are several metrics used to evaluate the performance of a model. In machine learning, accuracy, precision, and recall are three commonly used metrics for evaluating the performance of a **binary classification model**.

Accuracy is the fraction of correct predictions made by the model out of all predictions, and is a measure of the overall correctness of the model's predictions. It is defined as:

*Accuracy = (True Positives + True Negatives) / (Total Predictions)*

Precision is the fraction of true positive predictions among all positive predictions made by the model. It measures how many of the positive predictions made by the model are actually correct. It is defined as:

*Precision = True Positives / (True Positives + False Positives)*

Recall (also known as Sensitivity or True Positive Rate) is the fraction of true positive predictions that the model has correctly identified out of all actual positive cases. It measures how well the model can identify all positive cases. It is defined as:

*Recall = True Positives / (True Positives + False Negatives)*

It's important to keep in mind that accuracy, precision, and recall are often in trade-off with each other and the choice of metric to optimize for depends on the problem and the desired outcome. For example, in a disease diagnosis scenario, recall might be more important than precision since it's more important to not miss a positive case (a sick patient) than to have fewer false positives.

To get a more comprehensive understanding of a model's classification performance, it's common to use metrics such as the F1-Score, which is the harmonic mean of precision and recall, or ROC and AUC metrics.

Similary, there are also several metrics to evaluate the performance of **regression models**. Some of the most commonly used metrics are:

1.  *Mean Absolute Error (MAE):* It is the average absolute difference between the actual target values and the predicted values.

2.  *Mean Squared Error (MSE):* It is the average of the squared differences between the actual target values and the predicted values.

3.  *Root Mean Squared Error (RMSE):* It is the square root of the MSE.

4.  *R-Squared:* It is a goodness-of-fit metric that measures how well the model fits the data. It ranges from 0 to 1, where 1 represents a perfect fit and 0 represents a poor fit.

5.  *Mean Absolute Percentage Error (MAPE):* It is the average percentage difference between the actual target values and the predicted values.

The choice of which performance metric to use depends on the nature of the data and the problem being solved. For example, when the target values have a large range, it may be more appropriate to use the MAPE metric instead of the MAE or RMSE metric. When the target values are restricted to a narrow range, the MSE metric may be more appropriate.

#### **Hyperparameter tuning**

This involves selecting the best set of hyperparameters for a model, which can greatly impact its performance. Grid search and random search are common methods used for hyperparameter tuning:

-Model **hyperparameters** are parameters that are set before training a machine learning model and cannot be learned from the data during the training process. They are different from model parameters, which are learned from the data and determine the model's output. Examples of hyperparameters include the learning rate in gradient descent, the number of trees in a random forest, the regularization strength in a linear regression, the number of hidden layers in a neural network, and the number of clusters in a K-Means algorithm. Hyperparameters play a crucial role in determining the model's performance and must be chosen carefully.

#### **Bias-variance tradeoff**

The bias-variance tradeoff is a fundamental concept in machine learning that refers to the trade-off between a model's ability to fit the training data well (*low bias*) and its ability to generalize to new, unseen data (*low variance*). A model with high bias is typically oversimplified, resulting in underfitting of the training data and poor performance on new data. On the other hand, a model with high variance is typically too complex, resulting in overfitting of the training data and poor performance on new data.

If the model has high bias, one approach that can be taken is to use a more complex model with more parameters, or to add additional features to the model. If the model has high variance, one approach is to use regularization techniques or to remove features from the model.

The goal in model validation is to find the right balance between model complexity and performance, so that the model has low bias and low variance and generalizes well to new data. This requires a trade-off between fitting the data well and keeping the model simple, which is often referred to as the **bias-variance tradeoff**. By using model validation techniques, it is possible to make informed decisions about the trade-off and to find a model that generalizes well to new data.
