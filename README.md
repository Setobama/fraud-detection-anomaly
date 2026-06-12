# fraud-detection-anomaly
Fraud detection project using Isolation Forest and One-Class SVM to identify anomalous financial transactions. Part of my AI for Finance portfolio.
# 👋 Hi, I'm Akinyele  
Machine Learning & NLP Practitioner | AI for Finance | Anomaly Detection | Data Science

## 🚀 Professional Projects  
- Fraud Detection (Isolation Forest, One-Class SVM)  
- Financial Sentiment Analysis (BERT)  
- Stock Anomaly Detection (LSTM)  

## 📘 Learning Projects  
- NLP Experiments  
- ML Algorithms Practice  
- Python Learning Notes  

## 🛠️ Personal Projects  
- Automation Tools  
- Side Experiments  

### Dataset
This project uses the Credit Card Fraud Detection dataset.

The dataset is stored on Google Drive due to its large size:
https://drive.google.com/file/d/1tqCoMiZTBLwCPWM3D9NJpmKaUh7B7Ckc/view?usp=drive_link

The notebook automatically loads the dataset using a direct download link.

fraud-detection-anomaly/
│── notebook.ipynb
│── README.md
│── requirements.txt
│── plots/
│     └── anomalies.png
│── models/
│     └── isolation_forest.pkl


# 🛡️ Credit Card Fraud Detection — Hybrid Machine Learning Approach

This project builds a robust fraud‑detection pipeline using a combination of **unsupervised anomaly detection** and **supervised classification** to identify fraudulent credit‑card transactions in a highly imbalanced dataset.

The goal is to simulate a real‑world fraud‑detection workflow where anomalies must be detected proactively, and labelled fraud cases are extremely rare.

---

## 📌 Project Overview

Credit card fraud is a rare but high‑impact event. In this dataset, fraudulent transactions represent only **0.17%** of all records, making this a classic **imbalanced classification** problem.

This project implements a **hybrid pipeline**:

1. **Unsupervised anomaly detection**  
   - Isolation Forest  
   - One‑Class SVM  
   These models detect unusual behaviour without relying on labels.

2. **Supervised learning**  
   - Logistic Regression  
   - Random Forest  
   - XGBoost  
   These models learn directly from the labelled fraud cases.

This combination mirrors real‑world fraud‑detection systems used in banking and fintech.

---

## 📂 Dataset

The dataset used is the **Credit Card Fraud Detection** dataset from Kaggle:

🔗 https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

The dataset contains:

- **284,315** legitimate transactions  
- **492** fraudulent transactions  
- PCA‑transformed features (`V1`–`V28`)  
- `Amount` and `Time`  
- `Class` (0 = normal, 1 = fraud)

Due to its size (~150 MB), the dataset is **not stored in this repository**.

### 📥 Download the dataset

You can download the dataset directly from Kaggle.

Alternatively, the notebook loads the dataset from Google Drive using `gdown`:

```python
!pip install gdown

import gdown

file_id = "1tqCoMiZTBLwCPWM3D9NJpmKaUh7B7Ckc"
url = f"https://drive.google.com/uc?id={file_id}"

gdown.download(url, "creditcard.csv", quiet=False)
```

Then load it:

```python
import pandas as pd
df = pd.read_csv("creditcard.csv")
```

---

## 🧠 Methodology

### **1. Data Preprocessing**
- Loaded dataset from Google Drive  
- Checked for missing values  
- Scaled numerical features  
- Handled class imbalance using:
  - Class weights  
  - SMOTE (optional)  
  - Stratified train/test split  

---

### **2. Unsupervised Anomaly Detection**
These models detect unusual patterns without labels:

- **Isolation Forest**  
- **One‑Class SVM**

They assign anomaly scores to each transaction, helping surface suspicious behaviour.

---

### **3. Supervised Classification**
Using the labelled `Class` column:

- Logistic Regression  
- Random Forest  
- XGBoost (best performer)

Metrics used:

- Precision  
- Recall  
- F1‑score  
- ROC‑AUC  
- Confusion Matrix  

---

## 📊 Model Performance

The confusion matrix shows that the model:

- Correctly identifies the majority of fraud cases  
- Maintains a low false‑positive rate  
- Achieves high recall on the minority class  
- Avoids the trap of predicting “non‑fraud” for everything  

This strong performance is due to:

- The dataset being labelled  
- PCA‑transformed features making fraud patterns separable  
- Hybrid unsupervised + supervised pipeline  
- Proper handling of class imbalance  

---

## 🧾 Conclusion

This project demonstrates how a hybrid machine‑learning pipeline can effectively detect rare fraudulent transactions in a highly imbalanced dataset. The combination of **unsupervised anomaly detection** and **supervised classification** mirrors real‑world fraud‑detection systems used in financial institutions.

The confusion matrix and evaluation metrics confirm that the model achieves strong recall on the fraud class while maintaining low false‑positive rates. This shows that the model is not simply memorising patterns but genuinely learning the underlying structure of fraudulent behaviour.

Overall, this project highlights the value of combining anomaly detection with supervised learning to build a scalable, reliable fraud‑detection system suitable for production environments.

---

## 🚀 Future Improvements

- Deploy model as an API (FastAPI / Flask)  
- Add real‑time streaming detection (Kafka)  
- Train deep‑learning autoencoders for anomaly detection  
- Implement cost‑sensitive learning  
- Add SHAP explainability  

---

## 📎 Repository Structure

```
fraud-detection-anomaly/
│── notebook.ipynb
│── README.md
│── requirements.txt
│── models/
│── plots/
```

---

## 👤 Author

**Akinyele**  
Machine Learning & Data Science Practitioner  
Specialising in anomaly detection, fraud analytics, and operational automation.

