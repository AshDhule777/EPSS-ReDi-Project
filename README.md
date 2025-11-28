## EPSS Vulnerability Exploit Prediction 

**Using CVE, CVSS, EPSS & CISA KEV Data**

<hr style="border: 0.5px solid #ddd;">

**Introduction**

Every year, thousands of new **CVE vulnerabilities** are published — but very few are exploited in the wild. For penetration testers and security teams, the critical question becomes:

   **“Which vulnerabilities actually matter right now?”**

Traditional metrics like **CVSS** measure severity, but **not exploitation likelihood.**
Modern datasets like:

   - **EPSS (Exploit Prediction Scoring System)**
 
   - **CISA KEV (Known Exploited Vulnerabilities)**

provide indicators of real-world exploitation, but analyzing them at scale is challenging.

This project explores whether **machine learning** can predict exploitation likelihood using a combined dataset of CVE, CVSS, EPSS, and CISA KEV attributes.

---
**Project Goals**

This project focuses on **insight**, not high accuracy:

  - Understand the distribution of vulnerability attributes

  - Identify features most related to exploitation

  - Explore why prediction is difficult

  - Demonstrate how ML can support security teams

  - Highlight challenges due to **severe class imbalance**

---
**Dataset**

The dataset used in this project is:

**cve_cisa_epss_enriched_dataset.csv**
(Uploaded in this repository)

**Sample Columns**
```
base_score
impact_score
exploitability_score
epss_score
epss_percentile
cisa_kev     # 1 = known exploited, 0 = not exploited
```
Dataset Source: **Kaggle**

---
**Project Workflow**

**1️⃣ Data Loading & Cleaning**

  - Loaded enriched dataset
  - Selected key numerical columns
  - Converted cisa_kev TRUE/FALSE → 1/0
  - Removed missing values

**2️⃣ Exploratory Analysis**

  - Checked EPSS and CVSS score distributions
  - Observed extreme class imbalance:
      - Most CVEs = not exploited
      - Few CVEs = known exploited

**3️⃣ Model Training**

  A Random Forest Classifier was used because it:
    - Handles non-linear data
    - Works well with imbalance
    - Supports mixed features
    
  **Train/Test Split:** 80/20

**4️⃣ Evaluation**

  Due to imbalance, the model predicts mostly “not exploited.”
  This reflects real-world exploitation patterns, not a model failure.

---
**Machine Learning Model**

**Model Used: Random Forest Classifier**

**Input Features**
  ```
  base_score
  exploitability_score
  impact_score
  epss_score
  epss_percentile
  ```
**Target**
  ```
  cisa_kev   # 1 = exploited, 0 = not exploited
  ```
---
**Key Insights**

    - EPSS is the strongest predictor of exploitation
  
    - CVSS alone does not indicate likelihood of attack
  
    - Severe class imbalance makes prediction difficult
  
    - Random Forest still reveals meaningful relationships

**Top Feature Importance:**

  **1.** epss_score
  
  **2.** exploitability_score
  
  **3.** base_score

---
**Challenges**

    - Extreme dataset imbalance
    
    - Missing or incomplete fields
    
    - Some metrics fail due to single-class dominance
    
    - Needs more variety for model generalization

---
**Future Improvements**

**🔹 1. Use NLP on CVE Descriptions**

Adds meaningful context to improve prediction.

**🔹 2. Apply Resampling**

  - SMOTE
  - Undersampling
  - Class weighting

**🔹 3. Try Advanced Models**

  - XGBoost
  - LightGBM

**🔹 4. Build a Dashboard**

A UI for pentesters to quickly score vulnerabilities.

---
**Project Structure**
```
📁 EPSS-Vulnerability-Exploit-Prediction
│── 📓 EPSS_ReDI_Project.ipynb
│── 📊 cve_cisa_epss_enriched_dataset.csv
│── 🖼️ EPSS Vulnerability Exploit Prediction.pptx
│── 📘 README.md
```
---
**How to Run the Notebook**
**Install required packages**
```
pip install pandas numpy scikit-learn matplotlib
```
**Run**

Upload dataset → open notebook → run all cells.

---
**Presentation**

Slides used in this project:

**EPSS Vulnerability Exploit Prediction.pptx**

---
**Author**

**Ashwini Dhule**

ReDI School – Machine Learning Track

---
**Conclusion**

This project demonstrates that while predicting real-world exploitation is difficult, combining **EPSS, CVSS, and KEV** offers powerful insights.
Machine learning can support security teams by highlighting high-risk CVEs — helping organizations prioritize the vulnerabilities that truly matter.

---
