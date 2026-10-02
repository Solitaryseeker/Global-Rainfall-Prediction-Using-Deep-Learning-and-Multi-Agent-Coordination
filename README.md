# Global Rainfall Prediction Using Deep Learning and Multi-Agent Coordination


## 🌧️ Overview

This repository presents a **Deep Learning-based framework for global rainfall forecasting using regional modeling and multi-agent coordination**. The study investigates how regional rainfall patterns can be modeled independently and subsequently coordinated to improve forecasting across geographically diverse regions.

The research uses **global rainfall time-series data covering 5+ countries**, with detailed experimental analysis conducted for **China, Nigeria, South Africa, and Yemen**. The regional datasets are processed through an end-to-end pipeline involving data preprocessing, feature engineering, temporal sequence generation, and time-series analysis.

Two preprocessing strategies were systematically investigated:

* **Pipeline 1:** Log Transformation + Min-Max Scaling
* **Pipeline 2:** Yeo-Johnson Transformation + Robust Scaling

Multiple deep learning approaches were experimentally evaluated for regional rainfall forecasting, including **Transformer Encoder and iTransformer architectures**. Hyperparameter optimization was performed using **Optuna**, and model performance was assessed using **RMSE, MAE, and R²**.

The framework further explores a **multi-agent coordination approach**, where regional forecasting agents generate individual predictions that are subsequently integrated by an **Attention-Based Coordination Agent**. The coordination mechanism uses regional predictions and associated confidence information to learn how forecasts can be combined.

The repository therefore focuses on the complete research workflow — from **data preprocessing and experimental design to deep learning model development, comparative evaluation, and multi-agent coordination** — providing a reproducible implementation for studying global rainfall forecasting across heterogeneous geographical regions.


---

## 🎯 Objectives

- Develop deep learning models for regional rainfall forecasting.
- Compare **LSTM, Transformer Encoder, and iTransformer** architectures.
- Apply feature engineering to capture temporal and historical rainfall patterns.
- Use **Optuna** for hyperparameter optimization.
- Develop independent rainfall prediction agents for different countries.
- Combine regional predictions using an **Attention-Based Coordination Agent**.
- Build a scalable multi-agent framework for global rainfall prediction.

---

## 🌍 Study Regions

The proposed framework uses rainfall data from four countries:

| Region | Dataset |
|---|---|
|  China | [Subnational Rainfall Indicators](https://data.humdata.org/dataset/chn-rainfall-subnational) |
|  Nigeria | [Subnational Rainfall Indicators](https://data.humdata.org/dataset/nga-rainfall-subnational) |
|  South Africa | [Subnational Rainfall Indicators](https://data.humdata.org/dataset/zaf-rainfall-subnational) |
|  Yemen | [Subnational Rainfall Indicators](https://data.humdata.org/dataset/yem-rainfall-subnational#) |

The datasets contain rainfall information at the subnational level, allowing the models to learn both temporal and geographical rainfall patterns.

---

## 📊 Dataset

The rainfall datasets are obtained from the **WFP / Humanitarian Data Exchange (HDX)** rainfall indicator datasets, based on CHIRPS rainfall information.

The main rainfall variables include:

- `rfh` – 10-day rainfall
- `r1h` – 1-month rainfall
- `r3h` – 3-month rainfall
- `rfh_avg` – long-term average 10-day rainfall
- `r1h_avg` – long-term average 1-month rainfall
- `r3h_avg` – long-term average 3-month rainfall
- `rfq` – rainfall indicator/quality information
- `PCODE` – unique subnational geographical identifier

---


## 🔄 Data Preprocessing

Two preprocessing pipelines are investigated:

### Pipeline 1: Log Transformation + Min-Max Scaling

This pipeline applies logarithmic transformation to reduce the effect of highly skewed rainfall values, followed by Min-Max scaling.

### Pipeline 2: Yeo-Johnson Transformation + Robust Scaling

The Yeo-Johnson transformation is used to improve the distribution of the data, followed by Robust Scaling to reduce the influence of extreme rainfall observations.

The preprocessing pipelines are evaluated experimentally to determine which approach performs better for each regional model.

---

## 📅 Dataset Splitting

A chronological data-splitting strategy is used to prevent future information from being used during model training.

Training: 1 January 1982 – 31 December 2015

Validation: 1 January 2016 – 31 December 2020

Testing: 1 January 2021 – 21 December 2025

This approach reflects a realistic rainfall forecasting scenario where future observations are unavailable during model development.

---

## 🧠 Deep Learning Models

Three deep learning architectures are investigated:

### 1. Transformer Encoder

The Transformer Encoder uses self-attention to learn relationships between different time steps in the rainfall sequence.

### 2. iTransformer

The iTransformer architecture is used for multivariate time-series forecasting. It provides an alternative representation of multivariate temporal information and is used as one of the main forecasting architectures.

---
## Workflow

![](https://github.com/Solitaryseeker/Global-Rainfall-Prediction-Using-Deep-Learning-and-Multi-Agent-Coordination/blob/main/Photo/Multi-Agent%20Rainfall%20Forecasting%20Framework.png)


---

## 🔬 Hyperparameter Optimization

**Optuna** is used for automated hyperparameter optimization.

The optimization process searches for suitable model configurations such as:

- Learning rate
- Hidden dimensions
- Number of attention heads
- Number of layers
- Dropout
- Batch size
- Sequence-related parameters

The best configuration is selected based on validation performance and subsequently used for final model training.

---

## 🤖 Multi-Agent Rainfall Prediction Framework

The proposed system consists of two levels of agents.

### Regional Forecasting Agents

Each country has an independent forecasting agent:

---
🧩 Attention-Based Coordination Agent

The main component of the proposed system is the Attention-Based Coordination Agent.

The coordination agent receives information from all four regional agents.

For every regional agent, three values are provided:

- Predicted rainfall
- R² score
- Confidence score

---

## 📈 Final Regional Agent Performance

The following results represent the final regional models used in
the multi-agent coordination stage.

| Regional Agent | Model | RMSE | MAE | R² |
|---|---|---:|---:|---:|
| China | iTransformer | 0.4005 | 0.3171 | 0.6298 |
| Nigeria | iTransformer | 0.1894 | 0.1351 | 0.8753 |
| South Africa | Transformer Encoder | 0.3375 | 0.2537 | 0.6958 |
| Yemen | iTransformer | 0.3126 | 0.2280 | 0.8050 |
| Coordination Agent | Attention-Based Coordination | 0.1386 | 0.1108 | 0.7883 |

---
## 📜 License

This project is intended for academic and research purposes.
