# Similarity Pooling Method
**Dynamics and Disparities in Daily CO₂ Emissions of Global Cities in Response to Industrial Land Use Shifts**

This repository contains the implementation of the Similarity Pooling Method as presented in our paper *"Dynamics and Disparities in Daily CO₂ Emissions of Global Cities in Response to Industrial Land Use Shifts"*.

## Overview

The Similarity Pooling Method is designed to analyze industrial CO2 emissions by pooling data from reference cities. The method consists of three key steps:

1. **Calculate evaluation scores for each city.**
2. **Identify reference cities.**
3. **Pooling reference cities for target cities.**



## Jupyter Notebooks

We provide two Jupyter Notebooks to cover the analysis for different sectors:

- **Manufacturing Sector:**  
  `algorithm_Similarity-Pooling-Method_manufactureing.ipynb`

- **Power Sector:**  
  `algorithm_Similarity-Pooling-Method_power.ipynb`


## Data Splitting and Model Selection for the random forest model in the Similarity Pooling Method

To ensure a fair evaluation and reduce the risk of data leakage, we split the dataset and perform model selection as follows:

1. **Randomly split the dataset into training and test sets.**  
   We create an independent test set:
   70% of samples for training and 30% for testing (`test_size = 0.3`)
   A fixed random seed for reproducibility (`random_state = 42`)

2. **Choose hyperparameters using cross-validation.**  
   We run `RandomizedSearchCV` with 5-fold cross-validation (`cv = 5`). 

3. **Refit the model on the full training split using the best hyperparameters.**  
   After selecting the best hyperparameters, the model is retrained on training set.

4. **Evaluate on the held-out test set.**  
   We assess model performance on the test split and report evaluation metrics (e.g., MSE, MAE, and R²).  
   The test set is never used during training or hyperparameter choose.
   
