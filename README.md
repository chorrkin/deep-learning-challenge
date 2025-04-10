# Alphabet Soup Charity Success Prediction  
**By Chorrkin Chin**

## Overview

This project builds and evaluates a deep learning binary classification model to predict whether funding applicants will successfully use resources from the Alphabet Soup charity. By analyzing key features from the application data, the model helps the organization identify high-potential recipients and optimize funding decisions.

## Preprocessing Summary

- **Target Variable**: `IS_SUCCESSFUL` – 1 for successful funding use, 0 otherwise.
- **Key Features Used**: 
  - `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, `USE_CASE`, `ORGANIZATION`, `INCOME_AMT`, `ASK_AMT`
- **Features Removed**: 
  - `EIN`, `NAME` (binned in optimization), `STATUS`, `SPECIAL_CONSIDERATIONS`
- **Feature Engineering**:
  - Grouped low-frequency categorical values under "Other"
  - One-hot encoded categorical variables
  - Scaled numeric features using `StandardScaler`

## Model Architecture and Training

### Initial Neural Network
- Input Features: 43
- Hidden Layers: 
  - 1st Layer: 80 neurons, ReLU activation  
  - 2nd Layer: 30 neurons, ReLU activation
- Output Layer: 1 neuron, Sigmoid activation
- Training Epochs: 100
- **Accuracy**: 72.94%  
- **Loss**: 0.557

### Optimized Neural Network
- Feature Adjustments: 
  - Removed `STATUS`, `SPECIAL_CONSIDERATIONS`
  - Added binned `NAME` as a new feature
- Architecture Changes:
  - 1st Layer: 100 neurons, ReLU  
  - 2nd Layer: 30 neurons, Sigmoid  
  - 3rd Layer: 10 neurons, Sigmoid
- **Accuracy**: 73.36%  
- **Loss**: 0.539

### Random Forest Classifier (Comparison Model)
- Estimators: 128  
- **Accuracy**: 72.27%

## Summary of Results

- The target performance threshold of 75% accuracy was not met.
- The optimized neural network slightly outperformed the initial model and random forest baseline.
- Results suggest that model performance is limited by the dataset’s predictive strength.

## Recommendations

1. **Ensemble Learning**: Combine neural networks, random forests, and boosting methods using ensemble techniques such as stacking or voting to improve performance.
2. **Additional Data**: Integrate external data (e.g. financial records, organizational history, leadership profiles) to provide better signals for predicting success.
