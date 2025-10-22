# 🎓 Student Dropout and Academic Success Prediction using Machine Learning

A machine learning project that predicts student academic outcomes (Dropout, Enrolled, Graduate) to enable early intervention and improve student retention rates.


## 🎯 Overview

This project uses machine learning to predict whether students will **dropout**, remain **enrolled**, or **graduate** based on academic performance, demographics, and socioeconomic factors. The goal is to identify at-risk students early so institutions can provide timely interventions.


## 📊 Dataset

- **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success)
- **Size:** 4,424 students
- **Features:** 36 (academic performance, demographics, socioeconomic factors)
- **Target Classes:** 
  - Graduate: 2,209 (50%)
  - Dropout: 1,421 (32%)
  - Enrolled: 794 (18%) ← Minority class

### Key Features
- Academic: Admission grade, semester grades, curricular units approved/enrolled
- Demographic: Age, gender, marital status, nationality
- Socioeconomic: Parents' education/occupation, scholarship status
- Economic: Unemployment rate, inflation rate, GDP

## 🎯 Problem Statement

**Challenge:** Predict student outcomes to identify at-risk students early for intervention.

**Key Issues:**
**Class imbalance** - Only 18% of students are in the "Enrolled" category



## 📈 Results

### Model Comparison

| Metric | Baseline | With SMOTE | Change |
|--------|----------|------------|--------|
| **Overall Accuracy** | 77% | 76% | -1% ⚠️ |
| **Enrolled Recall** | 37% | 55% | **+48%** ✅ |
| **Enrolled F1-Score** | 0.45 | 0.51 | **+13%** ✅ |


While SMOTE reduced overall accuracy by 1% (77% → 76%), this trade-off is **beneficial**:

- SMOTE created synthetic samples for the minority "Enrolled" class
- Model became more sensitive to enrolled students (improved recall)
- This increased false positives, slightly lowering overall accuracy

-Catching at-risk students is more important than perfect accuracy
-Missing a student who drops out (false negative) is more costly than a false alarm (false positive)
-Student advisors would prefer checking extra students over missing those who need help


### Detailed Performance (SMOTE Model)
```
              precision    recall  f1-score   support

     Dropout       0.83      0.71      0.77       284
    Enrolled       0.48      0.55      0.51       159
    Graduate       0.83      0.86      0.84       442

    accuracy                           0.76       885
```

## 🔑 Key Findings

1. **Class Imbalance is Critical** - Baseline model missed 63% of at-risk enrolled students
2. **SMOTE Significantly Improved Detection** - Enrolled class recall: 37% → 55% (+48%)
3. **Most Predictive Features** - 2nd semester approved units, grades, admission scores
