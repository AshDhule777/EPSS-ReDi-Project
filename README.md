**EPSS Vulnerability Exploit Prediction**
Using CVE, CVSS, EPSS & CISA KEV Data

**Introduction**

Every year, thousands of new CVE vulnerabilities are published — but very few are exploited in the wild. For penetration testers and security teams, the critical question is:

“Which vulnerabilities actually matter right now?”

Traditional metrics like CVSS measure severity, but not exploitation likelihood. Modern datasets such as:

EPSS (Exploit Prediction Scoring System)

CISA KEV (Known Exploited Vulnerabilities)

provide indicators of real-world exploitation, but analyzing this at scale is challenging.

This project explores whether machine learning can help predict exploitation likelihood using a combined dataset of CVE, CVSS, EPSS, and CISA KEV attributes.

**🎯 Project Goals**
This project focuses on insight, not perfect accuracy:

Understand how vulnerability attributes are distributed

Identify features most related to exploitation

Explore why prediction is difficult

Demonstrate how ML could support vulnerability prioritization

Show challenges caused by severe class imbalance

**📂 Dataset**
The dataset used in this project is:

cve_cisa_epss_enriched_dataset.csv
(Uploaded in this repository)

It includes columns such as:

base_score

impact_score

exploitability_score

epss_score

epss_percentile

cisa_kev (boolean: whether the vulnerability is known exploited)

The dataset was obtained from Kaggle.

**🛠️ Project Workflow**
**1. Data Loading & Cleaning**

Loaded the enriched dataset

Selected key numerical columns

Converted cisa_kev TRUE/FALSE to 1/0

Removed missing values

**2. Exploratory Analysis**

Checked distribution of EPSS and CVSS scores

Observed extreme class imbalance:

Most CVEs = not exploited

Very few = known exploited

**3. Model Training**

A Random Forest Classifier was used because it:

Handles non-linear data

Works well with imbalance

Manages mixed-feature datasets

Train/Test split: 80/20

**4. Evaluation**

Due to dataset imbalance, the model predicts mostly the “not exploited” class.
This is not an error — it reflects real-world exploitation patterns.

**🤖 Machine Learning Model**

**Model used:** Random Forest Classifier

Input features:

base_score

exploitability_score

impact_score

epss_score

epss_percentile

**Target:**

cisa_kev - whether the CVE is known exploited

**📊 Key Findings & Insights**

EPSS is the strongest predictor of exploitation

CVSS scores alone do not indicate likelihood of attack

Severe class imbalance makes ML prediction difficult

Random Forest still reveals meaningful relationships

**Feature importance highlights:**

epss_score

exploitability_score

base_score

**🚀 Challenges**

**Extreme dataset imbalance**

Exploited CVEs are extremely rare

Missing or incomplete fields

Some metrics fail because only one class dominates

Requires more data variety for better model generalization

**📈 Future Improvements**

To make the model more practical:

**🔹 1. Use NLP on CVE Descriptions**

Text features greatly improve real-world vulnerability prediction.

**🔹 2. Apply Resampling**

SMOTE

Class weighting

Undersampling

**🔹 3. Try Advanced Models**

XGBoost

LightGBM

Logistic Regression baseline

**🔹 4. Build a Dashboard**

A simple web UI for pentesters to quickly score vulnerabilities.

**📑 Project Structure**
📁 EPSS-Vulnerability-Exploit-Prediction
│── 📘 EPSS_ReDI_Project.ipynb
│── 📄 cve_cisa_epss_enriched_dataset.csv
│── 📄 EPSS Vulnerability Exploit Prediction.pptx
│── 📄 README.md

**🖥️ How to Run the Notebook**

Install required packages:

pip install pandas numpy scikit-learn matplotlib


Then:

Open Jupyter or Google Colab

Upload the dataset

Run all notebook cells

**🎤 Presentation**

Slides used in this project:
**EPSS Vulnerability Exploit Prediction.pptx**


EPSS Vulnerability Exploit Pred…

**🧑‍💻 Author**
Ashwini Dhule
ReDI School – Machine Learning Track

**🏁 Conclusion**

This project demonstrates that while predicting real-world exploitation is hard, combining EPSS, CVSS, and KEV data offers meaningful insights. Machine learning can support security analysts by highlighting high-risk CVEs — helping teams prioritize what truly matters.

