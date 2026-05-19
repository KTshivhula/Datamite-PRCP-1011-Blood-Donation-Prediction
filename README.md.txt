# 🩸 Blood Donation Prediction

## 📌 Project Overview
Every year, millions of patients need blood transfusions, but blood supply depends on volunteer donors. This project predicts whether a donor will give blood again in March 2007 based on their donation history. The goal is to help blood drives **target likely donors**, reducing costs and improving blood supply planning.

**Dataset:** Mobile blood donation vehicle records from a university in Taiwan.  
**Target:** `Made Donation in March 2007` (1 = donated, 0 = did not donate)

---

## 🎯 Key Results

| Model | Accuracy | ROC AUC | Best For |
|-------|----------|---------|----------|
| **Logistic Regression** | 60.3% | **0.6885** ✅ | Ranking donors (production) |
| Random Forest | 73.3% | 0.6575 | Minimizing false alarms |
| Decision Tree | 65.5% | 0.6187 | Baseline interpretation |

**Production Recommendation:** Logistic Regression – highest ROC AUC, simple, interpretable, and prioritizes **recall** (catching actual donors).

---

## 📊 Dataset

- **Donors:** 576  
- **Donation rate (March 2007):** 24% (imbalanced – only 1 in 4 donated)  
- **Features:**
  - `Months since Last Donation`
  - `Number of Donations`
  - `Total Volume Donated (c.c.)`
  - `Months since First Donation`

### Class imbalance challenge
A naive model predicting "no donation" would be 76% accurate but useless. We addressed imbalance with `class_weight='balanced'` and stratified train/test splits.

---

## 🔧 Technologies & Libraries

- Python 3.11
- `pandas`, `numpy` – data manipulation
- `scikit-learn` – Logistic Regression, Random Forest, Decision Tree
- `matplotlib`, `seaborn` – visualizations

See [`requirements.txt`](requirements.txt) for exact versions.

---

## 📈 Exploratory Data Insights

| Feature | Donors vs Non‑donors |
|---------|----------------------|
| **Months since Last Donation** | Donors have shorter recency (median ~2 months) |
| **Number of Donations** | Donors have higher frequency (median ~7) |
| **Total Volume Donated** | Donors have donated more total blood |
| **Months since First Donation** | Donors have longer history (loyalty) |

*Boxplots and histograms in the notebook confirm these patterns.*

---

## 🚀 How to Run

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/blood-donation-prediction.git
cd blood-donation-prediction

# 2. (Optional) Create a virtual environment
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Launch Jupyter Notebook
jupyter notebook notebook/Blood_Donation_Prediction.ipynb