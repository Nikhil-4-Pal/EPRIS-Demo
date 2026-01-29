# 🏗️ Early Project Risk Intelligence System (EPRIS)
### *Predictive Analytics for Interior Design & Construction Risks*

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![XGBoost](https://img.shields.io/badge/Model-XGBoost-orange)
![SHAP](https://img.shields.io/badge/Explainability-SHAP-green)
![Status](https://img.shields.io/badge/Status-Prototype%20%2F%20PoC-yellow)

## 📋 Executive Summary
EPRIS is a data-driven decision support system designed to predict cost overruns and schedule delays during the critical **first 20% of a project's lifecycle**. 

In the construction and interior design industry, early warning signs are often fragmented across structured financial data and unstructured project manager notes. This project demonstrates a **Hybrid Machine Learning Architecture** that fuses these data sources to flag high-risk projects before they escalate.

> **Note:** *This repository contains a **Proof of Concept (PoC)** implementation using synthetic data to demonstrate the architectural pattern. No proprietary or confidential data is included.*

---

## 🛑 The Business Challenge
Projects frequently miss targets due to **Vendor Volatility**, **Scope Creep**, and **Data Fragmentation**. 

* **The Problem:** Risks are often hidden in unstructured text (email updates, meeting notes) that traditional BI dashboards miss.
* **The Goal:** Build a model that prioritizes **Recall** (catching every risk) over raw Accuracy, while providing interpretable "Why" factors for stakeholders.

---

## ⚙️ Solution Architecture

The system utilizes a dual-channel feature engineering approach:

1.  **Structured Channel:** Processes numerical indicators (Budget, Duration, Vendor Scores).
2.  **Unstructured Channel:** Uses **NLP (TF-IDF)** to extract semantic risk signals (e.g., sentiment trends, keywords like "rework" or "delay") from project notes.
3.  **Fusion & Modeling:** Merges features into a unified vector passed to an **XGBoost Classifier**.
4.  **Explainability:** Uses **SHAP (SHapley Additive exPlanations)** to provide local interpretability for every prediction.

### Tech Stack
* **Language:** Python
* **Modeling:** XGBoost, Scikit-learn
* **NLP:** TF-IDF Vectorizer (replicated logic for PoC)
* **Explainability:** SHAP
* **Data Generation:** NumPy/Pandas (Synthetic Engine)

---

## 📊 Key Performance Metrics (PoC)

The model was optimized for **Recall** to minimize False Negatives (missing a risky project).

| Metric | Score | Business Impact |
| :--- | :--- | :--- |
| **Precision (Risk)** | **98%** | High trust; few false alarms wasting PM time. |
| **Recall (Risk)** | **97%** | Safety net; captures ~97% of actual failures. |
| **F1-Score** | **0.98** | Balanced performance on imbalanced data. |

*(Metrics based on synthetic validation set of 200 projects)*

---

## 🧠 Explainability (SHAP Analysis)

The system rejects the "Black Box" approach. Using SHAP, we identify the exact drivers of risk:

* **Positive Drivers (Safe):** Keywords like *"completed"*, *"stable"*, *"early"*.
* **Negative Drivers (Risk):** Keywords like *"issues"*, *"concern"*, *"change"*, and low *Vendor_Reliability* scores.
* **Context Awareness:** The model successfully distinguishes between *"material"* (often used in cost increase contexts) vs *"materials"* (often used in delivery contexts).

---

## 🚀 How to Run

### 1. Installation
```bash
git clone [https://github.com/yourusername/epris-demo.git](https://github.com/yourusername/epris-demo.git)
cd epris-demo
pip install -r requirements.txt
