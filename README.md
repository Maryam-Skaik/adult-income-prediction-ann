# 🧠 Adult Census Income Prediction using Deep Learning (Keras)

![Python](https://img.shields.io/badge/Python-3.11+-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-Keras-orange)
![Deep Learning](https://img.shields.io/badge/Deep%20Learning-ANN-green)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-yellow)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## 📌 Project Overview

This project applies Deep Learning techniques to predict whether an individual earns more than **$50,000 per year** based on demographic, educational, and employment-related information from the Adult Census dataset.

The project was developed as a practical introduction to Artificial Neural Networks (ANNs) using Keras and demonstrates a complete machine learning workflow, including data preprocessing, neural network development, regularization techniques, hyperparameter tuning, and performance evaluation.

The primary objective is not only to build an accurate predictive model but also to explore how different neural network configurations impact generalization performance.

---

## 🎯 Project Goal

The goal of this project is to build and optimize a binary classification model capable of predicting income level using census data.

Through this project, the following Deep Learning concepts are explored:

* Data preprocessing for neural networks
* Handling categorical and numerical features
* Building Artificial Neural Networks (ANNs) with Keras
* Detecting and reducing overfitting
* Applying Dropout regularization
* Using EarlyStopping callbacks
* Hyperparameter tuning with Keras Tuner
* Comparing multiple neural network architectures
* Evaluating classification performance

---

## 📊 Dataset

The project uses the Adult Census Income Dataset, one of the most widely used datasets for classification tasks.

Each record represents an individual and contains demographic, educational, and employment-related information.

### Features Include

* Age
* Work Class
* Education Level
* Education Years
* Marital Status
* Occupation
* Relationship Status
* Race
* Gender
* Capital Gain
* Capital Loss
* Hours Worked Per Week
* Native Country
* Final Weight

### Target Variable

Income

* `0` → Income ≤ $50K
* `1` → Income > $50K

This is a binary classification problem where the objective is to predict an individual's income category.

---

## 🛠️ Data Preparation

Several preprocessing steps were performed before training the neural networks.

### Data Cleaning

* Renamed columns for better readability
* Replaced `"?"` values with missing values
* Filled missing categorical values using an `"Unknown"` category
* Removed duplicate records

### Target Encoding

The target variable was converted into a binary format:

```python
<=50K → 0
>50K  → 1
```

### Feature Transformation

A preprocessing pipeline was built using Scikit-Learn:

#### Numerical Features

* StandardScaler

#### Categorical Features

* OneHotEncoder

#### Combined Pipeline

* ColumnTransformer

This ensured all inputs were transformed into numerical features suitable for neural network training while preventing data leakage.

---

## 🧠 Model Development

Three different neural network approaches were implemented and compared.

### 1️⃣ Baseline Neural Network

Architecture:

* Dense (32 neurons, ReLU)
* Dense (16 neurons, ReLU)
* Dense (1 neuron, Sigmoid)

Training Configuration:

* Binary Crossentropy Loss
* Adam Optimizer
* Accuracy
* Precision
* Recall

This model provided a strong starting point but showed signs of overfitting during training.

---

### 2️⃣ Regularized Neural Network

To improve generalization performance, regularization techniques were introduced.

Architecture:

* Dense (128 neurons, ReLU)
* Dropout (0.3)
* Dense (64 neurons, ReLU)
* Dropout (0.3)
* Dense (1 neuron, Sigmoid)

Additional Techniques:

* Dropout Regularization
* EarlyStopping Callback

These changes reduced the gap between training and validation performance and improved robustness on unseen data.

---

### 3️⃣ Hyperparameter-Tuned Neural Network

To further optimize performance, Keras Tuner was used with the Hyperband search strategy.

Hyperparameters Tuned:

* Hidden layer sizes
* Dropout rate
* Optimizer selection
* Learning rate

Search Space Included:

* Optimizers:

  * Adam
  * RMSprop
  * Nadam

* Learning Rates:

  * 0.01
  * 0.001
  * 0.0001

* Multiple hidden layer configurations

* Multiple dropout values

Hyperband efficiently explored the search space and selected the best-performing model configuration.

---

## 🔍 Hyperparameter Tuning Results

Best configuration discovered:

| Hyperparameter      | Value    |
| ------------------- | -------- |
| First Hidden Layer  | 96 Units |
| Second Hidden Layer | 80 Units |
| Dropout Rate        | 0.3      |
| Optimizer           | Nadam    |
| Learning Rate       | 0.0001   |

This configuration delivered the strongest balance between learning capacity and generalization.

---

## 📈 Results

The final tuned neural network achieved approximately:

| Metric         | Score    |
| -------------- | -------- |
| Accuracy       | 85.8%    |
| Precision      | Strong   |
| Recall         | Strong   |
| Generalization | Improved |

Key observations:

* Baseline model achieved good performance but exhibited overfitting.
* Dropout and EarlyStopping significantly improved stability.
* Hyperparameter tuning further enhanced performance.
* The tuned model provided the best balance between accuracy and generalization.

---

## 📚 Key Deep Learning Concepts Demonstrated

This project demonstrates practical experience with:

* Artificial Neural Networks (ANN)
* Keras Sequential API
* Binary Classification
* Data Preprocessing Pipelines
* One-Hot Encoding
* Feature Scaling
* Overfitting Detection
* Dropout Regularization
* EarlyStopping
* Hyperparameter Optimization
* Keras Tuner Hyperband
* Model Evaluation

---

## 🚀 Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-Learn
* TensorFlow
* Keras
* Keras Tuner

---

## 💡 Conclusion

This project demonstrates a complete Deep Learning workflow for solving a real-world binary classification problem using census data.

Starting from raw tabular data, the project progressed through data cleaning, preprocessing, feature engineering, neural network construction, regularization, and automated hyperparameter optimization.

The final tuned model achieved approximately **85.8% accuracy**, outperforming the baseline architecture while exhibiting stronger generalization capabilities. The results highlight the importance of proper preprocessing, regularization techniques, and systematic hyperparameter tuning when developing effective neural network solutions.
