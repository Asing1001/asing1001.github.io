---
title: Leveraging scikit-learn for Invoice Classification using Text Data
date: 2024-02-16 16:45:47
tags: ["machine learning", "text classification", "invoice processing", "scikit-learn", "Python", "data preprocessing", "grid search", "model evaluation", "model deployment"]
---

In the realm of data science and machine learning, text classification is a common task with a wide range of applications. One such application is invoice classification, where invoices are categorized based on their textual content. In this blog post, we'll explore how to accomplish this task using scikit-learn, a popular machine learning library in Python.

## Understanding the Data

Before diving into the code, let's first understand the data we're working with. Our dataset consists of invoices along with their corresponding categories. We've gathered data from various sources, including human-marked data, generated data, and crawled data from the web.

```python
import pandas as pd

# Load the data
data1 = pd.read_csv('./data/human-marked.csv')
data2 = pd.read_csv('./data/generated/train.csv')
data3 = pd.read_csv('./data/crawled/train.csv')

# Concatenate the data into a single DataFrame
data = pd.concat([data1, data2, data3])
```

## Data Preprocessing and Exploration

After loading the data, we preprocess it to ensure uniformity, such as removing redundant spaces from category labels. Additionally, we explore the distribution of categories in our dataset to gain insights into the class distribution.

```python
# Preprocessing
data['categories'] = data['categories'].str.strip()

# Explore category distribution
category_counts = data['categories'].value_counts()
```

## Building the Classification Pipeline

With our data ready, we construct a classification pipeline using scikit-learn. Our pipeline consists of a TF-IDF vectorizer for feature extraction and a linear support vector classifier (LinearSVC) as the classification model.

```python
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.pipeline import Pipeline
from sklearn.calibration import CalibratedClassifierCV
from sklearn.svm import LinearSVC

# Split the data into training and testing sets
X = data['text'].values
y = data['categories'].values
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Define the pipeline
pipeline = Pipeline([
    ('tfidf', TfidfVectorizer()),
    ('clf', CalibratedClassifierCV(LinearSVC())),
])
```

## Model Training and Evaluation

Next, we train our model using grid search to find the optimal hyperparameters and evaluate its performance on the test set.

```python
from sklearn.model_selection import GridSearchCV
from sklearn.metrics import classification_report

# Define the parameter grid for grid search
param_grid = {
    # Hyperparameters to tune
}

# Perform grid search with cross-validation
grid_search = GridSearchCV(pipeline, param_grid, cv=2)
grid_search.fit(X_train, y_train)

# Evaluate the model on the test set
best_estimator = grid_search.best_estimator_
y_pred = best_estimator.predict(X_test)
report = classification_report(y_test, y_pred)
```

## Inference and Model Deployment

Finally, we demonstrate how to use the trained model for inference on new invoice texts and save the model for future use.

```python
import pickle

# Example inference on new invoice texts
test_texts = ['台電電費', 'Apple', 'netflix訂閱', '瓦斯現金券', '不鏽鋼鍋']
results = get_prediction_probabilities(best_estimator, test_texts)

# Save the trained model
with open('model.pkl', 'wb') as file:
    pickle.dump(best_estimator, file)
```

## Conclusion

In this blog post, we've demonstrated how to leverage scikit-learn to classify invoices based on their textual content. By building a robust classification pipeline and fine-tuning hyperparameters using grid search, we can achieve accurate categorization of invoices, enabling streamlined invoice processing and management.
