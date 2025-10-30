# 🧮 DATA ANALYTICS LAB - Assignment 7
### **DA5401 A7: Model Selection via ROC & PR (Statlog Landsat)**

**Name:** Aravindhan Mohanraj  
**Roll No:** DA25S006  

---

## 📂 Repository Overview
**Files included:**
- `DA5401 A7 Model Selection.pdf` - Problem Statement.
- `DA_Assignment_7.ipynb` - Jupyter Notebook with full workflow and visuals  
- `README.md` - Project overview and run instructions  
- **Dataset**: Statlog *Landsat Satellite* (`sat.trn`, `sat.tst`) — provided separately
- `sat.doc` : Description about the dataset


---

## 🧠 Notebook Structure (High-Level)
- Introduction & Objective  
- Problem Statement  
- **Part A:** Data Loading & Preprocessing  
- **Part B:** ROC Curves (micro/macro, per-class)  
- **Part C:** PR Curves (micro/macro, threshold analysis)  
- **Part D:** Model Comparison & Recommendation  
- **Part E:** Extra Models & Confusion Matrices  
- Conclusion & Future Work

---

## 🎯 Objective
Use **ROC** and **Precision–Recall (PR)** analyses to **compare classifiers** on a multi-class task and **select a final model** based on nuanced threshold behavior, not just accuracy.

---

## 🧩 Problem Statement
Classify **seven terrain classes** from the Statlog *Landsat* dataset (35 features, 1 label).  
Because classes are **imbalanced**, standard metrics can mislead. The task emphasizes **micro/macro ROC-AUC** and **Average Precision (AP)**, with **One-vs-Rest** decomposition to understand class separability and threshold trade-offs.

---

## ⚙️ Methodology

### **Part A: Data Preparation & Baseline**
1. **Load dataset:** `sat.trn` (train) and `sat.tst` (test); features in columns 1–35, label in column 36.  
2. **Preprocess:** `StandardScaler` on features; encode labels; verify train/test split integrity.  
3. **Baseline:** Fit simple models; inspect class distribution and initial metrics.

### **Part B: ROC Analysis**
- Compute **OvR ROC** per class; **micro**/**macro ROC-AUC**.  
- Plot aggregate and per-class ROC; discuss **class separability** and **ranking quality**.

### **Part C: Precision–Recall (PR) Analysis**
- Compute **micro/macro AP** and per-class PR curves.  
- Compare PR vs ROC under **imbalance**; analyze **threshold effects** on Precision/Recall.

### **Part D: Final Recommendation**
- Synthesize metrics: **Accuracy**, **Weighted F1**, **ROC-AUC**, **Average Precision**.  
- Consider **robustness** across thresholds and **generalization** on held-out test data.  
- Choose the **best overall classifier**.

### **Part E: Additional Models (Bonus)**
- Train and compare extra models beyond the core set; inspect confusion matrices and curve shapes.

---

## 🤖 Models Evaluated
- **Logistic Regression**, **SVC (OvR)**, **KNN (k=3)**, **Naive Bayes (GaussianNB)**  
- **Decision Tree**, **Random Forest**, **Linear Discriminant Analysis (LDA)**, **XGBoost (XGBClassifier)**  
- **Dummy Classifier** as a sanity baseline

---

## 📈 Results — Highlights
- **KNN (k=3)**: **Highest Weighted F1 ≈ 0.903**; strong point estimates but **less robust** to threshold shifts.  
- **SVC (OvR)**: **Top ROC-AUC ≈ 0.987** and **stable PR trade-offs**; best **overall balance** across metrics.  
- **Logistic Regression**: Competitive; slightly **lower recall balance** than SVC.  
- **Naive Bayes**: **High ROC-AUC ≈ 0.959**, but **lower AP** due to probability calibration limits.  
- **Decision Tree / Dummy**: **Poor generalization**; serve as lower bounds.

**Final Choice:** **SVC (One-vs-Rest)** — dependable discrimination and PR behavior across classes.


---

## 🚀 How to Run

1. **Clone the repo:**
   ```bash
   git clone https://github.com/Aravindhan-Mohanraj/assignment-7-Aravindhan-Mohanraj.git
   cd assignment-7-Aravindhan-Mohanraj
   ```

2. **Create & activate a virtual env (recommended):**
   ```bash
   python -m venv venv
   # macOS/Linux
   source venv/bin/activate
   # Windows
   venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -U pandas numpy scikit-learn matplotlib jupyter xgboost
   ```

4. **Launch the notebook:**
   ```bash
   jupyter notebook DA_Assignment-7.ipynb
   ```

---

## 👨‍💻 Author
**Aravindhan Mohanraj**  
**MS Scholar, Data Science & AI, IIT Madras**  
*Data Engineer | Data Science Enthusiast*
