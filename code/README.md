# Code — Global Rainfall Prediction

This directory contains the implementation of the **regional rainfall forecasting models** and selected trained model checkpoints used in the Global Rainfall Prediction framework.

## 📂 Regional Models

The repository currently presents the **best-performing model configuration selected for each regional forecasting task**:

* **China**
* **Nigeria**
* **South Africa**
* **Yemen**

Each country folder contains the relevant implementation for the selected model, including **data preprocessing, feature engineering, model configuration, evaluation, and trained model files**, where applicable.

### 🧪 Experimental Analysis

During the research, multiple **preprocessing strategies, model configurations, and experimental settings** were investigated before selecting the model configuration presented for each region.

The experiments included comparisons of:

* **Log Transformation + Min-Max Scaling**
* **Yeo-Johnson Transformation + Robust Scaling**
* Different deep learning model configurations
* Hyperparameter settings and training configurations
* Regional forecasting performance using **RMSE, MAE, and R²**

For repository clarity, only the **selected/best model implementation for each country** is presented here.

> **Note:** The complete experimental configurations, intermediate results, comparative analyses, and additional experiments are not included in this directory. Researchers interested in the **full experimental setup or detailed comparative results** are welcome to contact me.
