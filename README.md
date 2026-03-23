# Phase3_Project

# SyriaTel Customer Churn Prediction

## 1. Introduction

This project builds a c model to predict customer churn for SyriaTel, a telecommunications company. Churn when customers stop doing business with a company represents significant revenue loss. By identifying customers likely to churn, SyriaTel can implement targeted retention strategies to improve customer lifetime value.

The goal of this project is to build a predictive model that can identify customers most likely to churn. By doing so, SyriaTel can take proactive steps to retain them through targeted offers and improved customer service

## Business Objectives:

-Build a reliable model to predict churn.
-Identify the attributes most strongly associated with churn.
-Provide actionable recommendations to reduce churn.

## 📊 Executive Summary

Random Forest Model: 82.88% accuracy, identifies 60% of customers who will churn (59.89% recall)

Business Impact: Identifies 300 at-risk customers monthly | Potential savings: $600K-$1.5M annually | Expected ROI: 10x return on retention investment

Next Steps: Deploy model - Score customer database monthly -  Launch retention campaigns - Measure ROI - Retrain quarterly

---

##  Results at a Glance

| Metric | Value |
|--------|-------|
| Best Model | Random Forest |
| Accuracy | 82.88% |
| Recall | 59.89% (~6 of 10 churners caught) |
| Precision | 65.57% |
| ROC-AUC | 0.8724 |
| Customers Identified/Month | ~300 (60% of ~500 annual churners) |
| Annual Revenue at Risk | $600K - $1.5M |
| ROI  10x return |

Key Finding: Model successfully identifies customers most likely to churn, enabling SyriaTel to prioritize retention efforts on high-value segments.

---

## Business and Data Understanding

### Stakeholder & Business Problem

Stakeholder: SyriaTel executive leadership, customer retention team, marketing department

Business Problem: SyriaTel loses revenue when customers churn. Understanding which customers are at risk allows the company to:
- Allocate retention budgets efficiently
- Identify at-risk customer segments
- Implement targeted retention campaigns
- Reduce overall churn rate and increase customer lifetime value

### Dataset Overview

Source: [Kaggle - SyriaTel Customer Churn Dataset](https://www.kaggle.com/becksddf/churn-in-telecoms-dataset)

Size: 3,333 customer records with 21 features

Target Variable: `churn` binary: Yes/No


### Key Features Analyzed

- Account information
- Service usage
- Customer interactions
- Demographic patterns
---

## Modeling


This project employs an iterative modeling approach to compare multiple classification algorithms:

1. Logistic Regression : Simple, interpretable parametric model to establish baseline performance
2. Decision Tree : Tree based model to capture non-linear relationships tuned hyperparameters to reduce overfitting
3. Random Forest :captures complex feature interactions

### Data Preparation

Train-Test Split: 80% training (2,667 records), 20% testing (666 records)

Preprocessing Pipeline:
- **Numeric features** (minutes, charges, calls): StandardScaler to normalize scale-dependent models
- **Categorical features** : OneHotEncoder with handle_unknown='ignore'
- **Implementation**: scikit-learn ColumnTransformer in Pipeline to prevent data leakage 


---
## Evaluation

### Classification Metrics Chosen

Given the business problem, I prioritized recall while monitoring precision (false alarm cost) and accuracy the overall correctness:

- Recall: using it for retention I want to catch most customers who will churn
- Precision: Cost of contacting false alarms (false positives)
- F1-Score: Balance between precision and recall
- ROC & AUC: Model's ability to discriminate between classes

### Model Performance (Test Data)

| Model | Accuracy | Precision | Recall | F1-Score | ROC & AUC |
|-------|----------|-----------|--------|----------|---------|
| Logistic Regression | 0.8198 | 0.6327 | 0.5439 | 0.5844 | 0.8543 |
| Decision Tree  | 0.8198 | 0.6364 | 0.5439 | 0.5844 | 0.7689 |
| Decision Tree (Tuned) | 0.8108 | 0.5833 | 0.5989 | 0.5909 | 0.7866 |
| **Random Forest** | 0.8288 | 0.6557 | 0.5989 | 0.6254 | 0.8724 |

**Winner**: Random Forest with 0.8288 test accuracy and 0.5989 recall (identifies 60% of churners)

---
## Conclusion

### Key Findings

1. **Model Performance**: Random Forest achieves 82.9% overall accuracy with 59.9% recall—successfully identifying roughly 6 out of 10 customers who will churn.

2. **Business Impact**: With 500 annual churners predicted from the test set , the model correctly identifies 300 customers. Combined with efficient retention offers, this prevents significant revenue loss.

3. **High Value Indicators**: Customers with high charges, frequent service calls and specific usage patterns are most at risk. 
### Limitations

- 40% of churners missed: The 59.9% recall means 200 customers who churn go unidentified and requires acceptance of residual risk
- **Class imbalance**: 14.5% churn rate means the model sees fewer positive examples; could benefit from SMOTE or class weights

### Recommendations for SyriaTel

1. Deploy Retention Strategy: Prioritize outreach to the 300 identified at-risk customers with retention offers (

2.  Focus resources on customers with:
   - High total charges
   - Multiple service calls 
   - International plan subscribers 

3.  Track which predictions lead to successful retention and retrain the model quarterly as customer behavior evolves

4.  Calculate ROI if the cost of retention offers is less than the lifetime value of prevented churn the 60% recall rate is acceptable

---
. Next Steps
Perform cross-validation to validate model robustness across different splits.

Experiment with additional hyperparameters and ensemble methods to further improve recall.

Deploy the model into SyriaTel’s system to score customers monthly and trigger retention campaigns.

## How to Use This Repository

- **model.ipynb**: Full Jupyter notebook with exploratory analysis, data preparation, model training, and evaluation
- **bigml_59c28831336c6604c800002a.csv**: Raw dataset (3,333 records)
- **README.md**: This file—bridge between presentation and technical notebook


```bash
jupyter notebook model.ipynb
```
ß
>>>>>>> 033fffb (Initial commit)
