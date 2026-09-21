# Credit Risk & Fraud Detection System

A end-to-end Machine Learning web application built with **FastAPI**, **XGBoost / Scikit-Learn**, and a responsive frontend to assess loan applicant credit risk and predict loan default probabilities in real time.

---

## 📌 Project Overview

This application evaluates loan applicant profiles and classifies them into **High Risk** or **Low Risk** categories using a trained Machine Learning pipeline. The backend uses FastAPI with custom threshold tuning to optimize default risk detection.

- **Frontend**: Responsive Web Interface (HTML5, CSS3, JavaScript)
- **Backend**: FastAPI with async model lifecycle management & Pydantic validation schemas
- **Machine Learning**: Pipeline trained on credit dataset serialized with `joblib`

---

## ✨ Features

- ⚡ **Real-Time Risk Scoring**: Computes exact default probability and assigns risk category.
- 🎯 **Optimized Thresholding**: Utilizes a dynamic/tuned decision threshold (`best_threshold.pkl`) to maximize prediction accuracy and balance precision/recall.
- 🎨 **Interactive Web UI**: Modern interface for submitting applicant attributes and viewing live risk indicators.
- 📖 **Interactive API Documentation**: Auto-generated OpenAPI / Swagger UI at `/docs`.

---

## 📁 Repository Structure

```text
credit_fraud_detection/
│── static/                         # Frontend Static Assets
│   ├── index.html                  # Application UI HTML
│   ├── style.css                   # Custom Styling
│   └── script.js                   # Frontend Logic & API Fetching
│── Credit_Risk.ipynb               # Jupyter Notebook for Data Analysis & Model Training
│── main.py                         # FastAPI Application Server & /predict API Endpoint
│── credit_risk_dataset.csv         # Dataset used for training and testing
│── credit_risk_model.pkl           # Trained ML Model Pipeline
│── best_threshold.pkl              # Saved Optimal Decision Threshold
│── requirements.txt                # Python Dependencies
│── runtime.txt                     # Target Python Runtime Version
└── README.md                       # Project Documentation
```

---

## 📊 Dataset & Input Features

The model evaluates applicants based on 11 input attributes:

| Feature Name | Type | Description |
| :--- | :--- | :--- |
| `person_age` | Integer | Applicant's age |
| `person_income` | Float | Applicant's annual income in USD |
| `person_home_ownership` | String | Housing status (`RENT`, `OWN`, `MORTGAGE`, `OTHER`) |
| `person_emp_length` | Float | Employment length in years |
| `loan_intent` | String | Purpose of the loan (`PERSONAL`, `EDUCATION`, `MEDICAL`, `VENTURE`, `HOMEIMPROVEMENT`, `DEBTCONSOLIDATION`) |
| `loan_grade` | String | Loan grade rating (`A`, `B`, `C`, `D`, `E`, `F`, `G`) |
| `loan_amnt` | Float | Requested loan amount |
| `loan_int_rate` | Float | Loan interest rate (%) |
| `loan_percent_income` | Float | Ratio of loan amount to applicant income |
| `cb_person_default_on_file` | String | Historical credit default record (`Y` / `N`) |
| `cb_person_cred_hist_length` | Integer | Credit history length in years |

---

## 🛠️ Setup & Installation

### Prerequisites

- **Python 3.11+** (specified in `runtime.txt`)
- `pip` package manager

### 1. Clone or Download Repository

```bash
git clone https://github.com/preetam-coder/credit_risk_project.git
cd credit_risk_project
```

### 2. Create & Activate Virtual Environment

**Windows (PowerShell):**
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**Linux / macOS:**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 🚀 Running the Application

Start the FastAPI server with Uvicorn:

```bash
uvicorn main:app --reload
```

Once running:
- **Web UI**: Open [http://127.0.0.1:8000](http://127.0.0.1:8000) in your browser.
- **Swagger API Docs**: Open [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs) to explore and test API endpoints interactively.
- **ReDoc API Docs**: Open [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc).

---

## 🔌 API Reference

### Predict Credit Risk

- **Endpoint**: `POST /predict`
- **Content-Type**: `application/json`

#### Request Payload Example

```json
{
  "person_age": 25,
  "person_income": 55000.0,
  "person_home_ownership": "RENT",
  "person_emp_length": 3.0,
  "loan_intent": "MEDICAL",
  "loan_grade": "C",
  "loan_amnt": 10000.0,
  "loan_int_rate": 12.5,
  "loan_percent_income": 0.18,
  "cb_person_default_on_file": "N",
  "cb_person_cred_hist_length": 4
}
```

#### Response Example

```json
{
  "default_probability": 0.3245,
  "default_prediction": 0,
  "threshold": 0.45,
  "Result": "Low Risk"
}
```

---

## 📓 Model Training & Notebook

The model exploration, data preprocessing, feature engineering, cross-validation, hyperparameter tuning, and threshold selection logic are documented in [`Credit_Risk.ipynb`](file:///c:/Users/preet/OneDrive/Desktop/credit_fraud_detection/Credit_Risk.ipynb).

- **Trained Model Artifact**: [`credit_risk_model.pkl`](file:///c:/Users/preet/OneDrive/Desktop/credit_fraud_detection/credit_risk_model.pkl)
- **Optimal Threshold Artifact**: [`best_threshold.pkl`](file:///c:/Users/preet/OneDrive/Desktop/credit_fraud_detection/best_threshold.pkl)

---

## 📜 License

This project is open-source and available under the MIT License.
