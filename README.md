# Credit Risk Model for Bati Bank

Building a credit scoring model using eCommerce transaction data for Buy-Now-Pay-Later (BNPL) service.

## Project Structure
- `data/`: Raw and processed datasets (gitignored)
- `notebooks/`: Exploratory Data Analysis (EDA)
- `src/`: Source code for data processing, training, and API
- `tests/`: Unit tests

## Setup Instructions
1. Clone this repo
2. Create virtual environment: `python -m venv venv`
3. Activate: `venv\Scripts\activate` (Windows) or `source venv/bin/activate` (Mac/Linux)
4. Install: `pip install -r requirements.txt`

By: Tewodros Tsegay Wendem

## Credit Scoring Business Understanding

### 1. How does the Basel II Accord’s emphasis on risk measurement influence our need for an interpretable and well-documented model?
The Basel II Accord requires financial institutions to hold capital reserves proportional to the risk they take. This means Bati Bank must **prove** its credit risk model is **robust, transparent, and auditable**. An interpretable model (e.g., Logistic Regression with clear feature weights) allows regulators to **validate** the bank’s risk assessment, ensuring compliance. A "black box" model (e.g., deep neural nets) would fail this requirement, exposing the bank to regulatory penalties.

### 2. Since we lack a direct "default" label, why is creating a proxy variable necessary, and what are the potential business risks of making predictions based on this proxy?
Without historical loan data, we have no "default" labels. So we use **disengagement (low RFM scores)** as a proxy for high risk. The risk? **Proxy bias**: a customer might be disengaged due to life events (e.g., job loss), not credit risk. If we deny credit based on this, we **exclude good customers**, lose revenue, and potentially face **fair lending criticism**.

### 3. What are the key trade-offs between using a simple, interpretable model vs. a complex, high-performance model in a regulated financial context?
- **Simple Model (Logistic Regression)**:  
  ✅ Interpretable (meets Basel II)  
  ✅ Easy to debug and audit  
  ❌ May miss complex patterns  
- **Complex Model (XGBoost)**:  
  ✅ Higher accuracy  
  ❌ "Black box" — hard to explain to regulators  
  ✅ **Solution**: Use XGBoost + **SHAP** for post-hoc explanations — best of both worlds.