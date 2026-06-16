# fraud-detection-anomaly
Fraud detection project using Unsupervided & supervised method  to identify anomalous financial transactions. Part of my AI for Finance portfolio.
# 👋 Hi, I'm Akinyele  
Machine Learning & NLP Practitioner | AI for Finance | Anomaly Detection | Data Science

### Dataset
This project uses the Credit Card Fraud Detection dataset.

The dataset is stored on Google Drive due to its large size:
https://drive.google.com/file/d/1tqCoMiZTBLwCPWM3D9NJpmKaUh7B7Ckc/view?usp=drive_link

The notebook automatically loads the dataset using a direct download link.

# 🛡️ Credit Card Fraud Detection — Hybrid Machine Learning System

This project implements a complete fraud‑detection pipeline using both **unsupervised anomaly detection** and **supervised classification**. The goal is to replicate real‑world fraud analytics, where fraud is extremely rare and labels may be incomplete or delayed.

The dataset is highly imbalanced, with fraudulent transactions representing only **0.17%** of all records. This makes fraud detection a challenging and realistic machine‑learning problem.

---

## 📂 Dataset Source

This project uses the **Credit Card Fraud Detection** dataset from Kaggle:

🔗 https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

The dataset contains anonymised credit‑card transactions with PCA‑transformed features (`V1`–`V28`), along with `Amount`, `Time`, and a binary fraud label (`Class`). Due to its size (~150 MB), the dataset is **not stored in this repository**.  
Instead, the notebook loads it directly from Google Drive using `gdown`.

Only the dataset link is relevant for reproducibility — no browser information or system metadata is included in this project.

### What Are V1–V28?

The original transaction features in the dataset contained sensitive financial information.  
To protect customer privacy, the dataset creators applied Principal Component Analysis (PCA) to the raw features and released only the transformed components.

V1–V28 are anonymised PCA components that capture the most important variance in the original data while ensuring that no personal or confidential information can be reconstructed.


---

## 📘 Notebook

You can view the full notebook here: https://github.com/Setobama/fraud-detection-anomaly/blob/58677dd74a7b1b77cbecfaf5a80143a0c96f390e/fraud_detection_anomaly.ipynb

👉 **`fraud_detection.ipynb`**

---

# 🧠 Methodology

This project uses a **two‑stage hybrid approach**:

---

## 1️⃣ Unsupervised Anomaly Detection  
Used when labels are missing or unreliable.

### Models:
- **Isolation Forest**
- **One‑Class SVM**

These models learn what “normal” behaviour looks like and flag deviations as anomalies.

### Results:

#### **Isolation Forest**
```
precision (fraud): 0.29
recall (fraud):    0.17
f1-score:          0.22
```

#### **One‑Class SVM**
```
precision (fraud): 0.18
recall (fraud):    0.10
f1-score:          0.13
```

### Interpretation:
- Unsupervised models struggle because they **do not use labels**.  
- Fraud patterns are subtle and require supervised learning.  
- These models are useful for **early anomaly detection**, not final classification.

---

## 2️⃣ Supervised Classification  
Used when labels are available.

### Models:
- **Logistic Regression**
- **Random Forest**
- **XGBoost**

These models directly learn the difference between fraud and non‑fraud.

### Results:

#### **Logistic Regression**
- High recall (0.92)  
- Very low precision (0.06)  
- Many false positives  
- Linear model → cannot capture complex fraud patterns

#### **Random Forest**
- Precision (fraud): 0.96  
- Recall (fraud): 0.77  
- Strong performance  
- Handles non‑linear patterns well

#### **XGBoost (Best Performer)**
- Precision (fraud): 0.86  
- Recall (fraud): 0.83  
- Excellent balance  
- Industry‑standard for fraud detection

### Interpretation:
- Tree‑based models outperform linear models  
- XGBoost provides the best fraud recall and precision  
- Supervised learning is far more effective on this dataset  

---

# 📊 Confusion Matrices

Confusion matrices for all models (unsupervised + supervised) are saved in:

---
### Unsupervised Confusion Matrix
<img src="https://github.com/user-attachments/assets/5d9c00b9-b65a-4986-8a3e-a222bb037c40" width="900" />

### XGBoost Confusion Matrix
<img src="https://github.com/user-attachments/assets/5ca8b54d-8fe6-432c-836c-dc0aa3f53b32" width="1200" />

### Fraud Scatter Plot
<img src="https://github.com/user-attachments/assets/3050207a-de1e-449a-a85c-702907f3b6cf" width="900" />

# 📈 ROC Curves

ROC curves are generated for:

### ✔ Supervised models  
- Logistic Regression  
- Random Forest  
- XGBoost  

### ✔ Unsupervised models  
- Isolation Forest  
- One‑Class SVM  

### ✔ Overfitting check  
- XGBoost Train vs Test ROC

All ROC plots are saved in:

```

```

Example:

### 📈 ROC Curves — Supervised Models
<img width="863" height="641" alt="Image" src="https://github.com/user-attachments/assets/d9dd010b-01c5-4c7d-8bee-b7b21f5bf7c4" />

```

📊 Dataset Separation View
<img width="1386" height="589" alt="Image" src="https://github.com/user-attachments/assets/caff22b8-c8a5-4981-b7a9-a02148b56194" />

shows fraud and non‑fraud distributions in separate histograms

📊 Combined Class Distribution (Log Scale)
<img width="575" height="451" alt="Image" src="https://github.com/user-attachments/assets/ff1ed415-21a0-4727-b6fb-672344cea91c" />

overlays fraud and non‑fraud together, revealing fraud’s rarity.

📊 Ground Truth vs Model Predictions
<img width="1388" height="592" alt="Image" src="https://github.com/user-attachments/assets/e84e2147-14a1-4d6f-8313-b3e9fb540693" />
 
 compares actual labels against XGBoost’s predicted classifications.



# 🔍 Overfitting Check

A Train vs Test ROC comparison is included for XGBoost to verify generalisation.

- If Train AUC >> Test AUC → overfitting  
- If curves are similar → model generalises well  

XGBoost shows strong generalisation.

---

# 🧾 Conclusion

This project demonstrates that:

- **Unsupervised anomaly detection** is useful for discovering unusual patterns but performs poorly on labelled fraud classification.
- **Supervised learning**, especially tree‑based models like Random Forest and XGBoost, performs exceptionally well on this dataset.
- **XGBoost** achieves the best balance of precision and recall, making it the most reliable model for real‑world fraud detection.
- A **hybrid system** combining both approaches mirrors real banking fraud‑detection pipelines.

---

# 🚀 Future Improvements

- Deploy model as an API (FastAPI / Flask)  
- Add SHAP explainability for model transparency  
- Train deep‑learning autoencoders for anomaly detection  
- Implement real‑time streaming detection (Kafka)  
- Use cost‑sensitive learning to penalise false negatives  

---

# 📁 Project Structure

```
fraud-detection/
│── README.md
│── fraud_detection.ipynb
│── requirements.txt
│
│── data/
│     └── (empty or dataset link in README)
│
│── models/
│     ├── xgboost_model.pkl
│     ├── random_forest_model.pkl
│     ├── logistic_regression.pkl
│     ├── isolation_forest.pkl
│     └── oneclass_svm.pkl
│
│── plots/
│     ├── roc_supervised.png
│     ├── roc_unsupervised.png
│     ├── confusion_matrix_xgb.png
│     ├── confusion_matrix_rf.png
│     ├── confusion_matrix_lr.png
│     ├── confusion_matrix_iso.png
│     ├── confusion_matrix_ocsvm.png
│     ├── scatter_fraud.png
│     └── feature_importance_xgb.png   (optional)
│
│── src/
│     ├── preprocessing.py
│     ├── train_supervised.py
│     ├── train_unsupervised.py
│     ├── evaluate_supervised.py
│     ├── evaluate_unsupervised.py
│     └── utils.py
│
└── notebooks/
      └── experiments.ipynb   (optional)

```

---

# 👤 Author

**Akinyele**  
Machine Learning & Data Science Practitioner  
Specialising in anomaly detection, fraud analytics, and operational automation.
