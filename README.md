# Next-Gen Customer Retention: A Stacked Ensemble Model

[![Paper Status](https://img.shields.io/badge/Status-Published-success)](https://sesjournal.com)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

## 📄 Abstract
This repository contains the official implementation of the research paper **"Next-Gen Customer Retention: A Stacked Ensemble Model for Churn Prediction"**, published in *Spectrum of Engineering Sciences (2025)*.

Customer churn is a critical challenge in the telecommunications industry. Traditional models often struggle with class imbalance or computational inefficiency. This research proposes a **Stacked Ensemble Learning** framework that integrates **Random Forest, Naïve Bayes, and K-Nearest Neighbors (KNN)** as base learners, utilizing **Logistic Regression** as a meta-learner.

The model addresses data imbalance using **SMOTEENN** (Synthetic Minority Oversampling Technique and Edited Nearest Neighbors) and introduces a novel metric, the **Latency Aware Accuracy Index (LAAI)**, to optimize the trade-off between predictive accuracy and real-time processing speed.

## 🚀 Key Results
Our proposed Stacked Ensemble model outperformed individual classifiers on the *WA_Fn-UseC_-Telco-Customer-Churn* dataset, achieving a state-of-the-art accuracy of **98.1%**.

| Model | Accuracy | Precision | Recall | F1-Score | LAAI (Score) |
|-------|----------|-----------|--------|----------|--------------|
| SVM | 79.67% | 79.97% | 79.67% | 79.71% | 0.72 |
| KNN | 92.72% | 92.76% | 92.72% | 92.76% | 0.90 |
| Random Forest | 91.78% | 91.78% | 91.47% | 91.64% | 0.26 |
| Logistic Regression | 90.48% | 90.50% | 90.48% | 90.49% | 0.81 |
| **Ensemble Stacking** | **98.10%** | **98.10%** | **98.10%** | **98.10%** | **0.90** |

*Data sourced from Table 5 and Table 6 of the original paper.*

## 💡 Novel Metric: LAAI
To ensure the model is practical for real-world deployment, we utilized the **Latency Aware Accuracy Index (LAAI)**. This metric penalizes models that are accurate but too slow for real-time systems.

$$LAAI = \frac{Accuracy}{1 + Latency}$$

Where *Latency* is the total time taken for prediction. Our Stacked model achieves a high LAAI of **0.90**, matching KNN in efficiency while far surpassing it in accuracy.

## 🛠️ Methodology
The pipeline follows these steps as detailed in the research:
1.  **Data Preprocessing:** Handling missing values in `TotalCharges` and encoding categorical variables via One-Hot Encoding.
2.  **Class Balancing:** Applied **SMOTEENN** to handle the 74%-26% class imbalance in the original dataset.
3.  **Modeling:** * **Base Learners:** Random Forest ($n=100$), KNN ($k=5$), Naïve Bayes (Gaussian).
    * **Meta Learner:** Logistic Regression.
4.  **Evaluation:** Models were tested on a 20% hold-out test set.

## 💻 Installation & Usage

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/YOUR_USERNAME/NextGen-Customer-Retention.git](https://github.com/YOUR_USERNAME/NextGen-Customer-Retention.git)
   cd NextGen-Customer-Retention

📊 Dataset
We utilized the WA_Fn-UseC_-Telco-Customer-Churn dataset, which contains 7,043 customer records with 21 features.

Source: Kaggle - Telco Customer Churn.
