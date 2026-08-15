# loan-approval-prediction-with-n8n-automation

# 🏦 Explainable Loan Approval AI

An AI-powered **Loan Approval Prediction System** that predicts whether a loan application should be approved or rejected using Machine Learning and provides **explainable, transparent, and actionable reasons** behind the prediction.

The system combines **Random Forest Machine Learning, SHAP-based Explainable AI (XAI), Counterfactual Recommendations, FastAPI, and n8n automation** to create an end-to-end intelligent loan approval workflow.

---

![Uploading WhatsApp Image 2026-08-15 at 10.02.52 AM (1).jpeg…]()


![Uploading WhatsApp Image 2026-08-15 at 10.02.52 AM.jpeg…]()


## 🚀 Project Overview

Traditional loan approval systems often provide only a final decision such as:

> **Loan Approved / Loan Rejected**

However, applicants may also want to understand:

* Why was my loan rejected?
* Which factors affected the decision?
* What can I improve to increase my chances?
* What would happen if my income or credit-related information changed?

This project addresses these problems using **Explainable AI**.

The system predicts the loan decision and provides an explanation of the important features influencing the prediction.

It can also generate **counterfactual recommendations**, such as:

> "Increasing your income or improving your credit-related parameters could improve the probability of loan approval."

---

## ✨ Key Features

* 🤖 Machine Learning-based loan approval prediction
* 🌲 Random Forest classification model
* 📊 SHAP-based feature importance and explanations
* 🔄 Counterfactual recommendations
* ⚡ FastAPI backend
* 🔗 n8n workflow automation
* 📈 Scalable API architecture
* 💾 Pre-trained model and scaler support
* 🧠 Explainable AI for transparent decision-making
* 🌐 Web-based prediction interface
* 📋 Structured loan application processing

---

## 🧠 Technologies Used

| Technology    | Purpose                    |
| ------------- | -------------------------- |
| Python        | Core programming language  |
| Pandas        | Data preprocessing         |
| NumPy         | Numerical computation      |
| Scikit-learn  | Machine Learning           |
| Random Forest | Loan approval prediction   |
| SHAP          | Model explainability       |
| FastAPI       | Backend REST API           |
| Joblib        | Model/scaler serialization |
| Jinja2        | HTML template rendering    |
| Uvicorn       | FastAPI server             |
| n8n           | Workflow automation        |
| HTML/CSS      | Frontend                   |
| Ngrok         | Local webhook/API exposure |

---

## 🏗️ System Architecture

```text
                    ┌─────────────────────┐
                    │   User / Applicant  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │  Loan Application   │
                    │       Form          │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │      FastAPI        │
                    │      Backend        │
                    └──────────┬──────────┘
                               │
                               ▼
                  ┌─────────────────────────┐
                  │   Data Preprocessing    │
                  │  Scaling / Validation   │
                  └────────────┬────────────┘
                               │
                               ▼
                  ┌─────────────────────────┐
                  │    Random Forest Model  │
                  │   Loan Approval Model   │
                  └────────────┬────────────┘
                               │
                    ┌──────────┴──────────┐
                    ▼                     ▼
          ┌──────────────────┐   ┌──────────────────┐
          │  Loan Prediction │   │   SHAP Analysis  │
          │ Approved/Rejected│   │ Feature Impact   │
          └─────────┬────────┘   └─────────┬────────┘
                    │                      │
                    └──────────┬───────────┘
                               ▼
                  ┌─────────────────────────┐
                  │ Counterfactual /       │
                  │ Improvement Suggestions│
                  └────────────┬────────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │    n8n Automation   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Notification /      │
                    │ Automated Workflow  │
                    └─────────────────────┘
```

---

## 🔄 Workflow

### 1. User submits loan application

The applicant enters required financial and personal information through the application interface.

### 2. FastAPI receives the request

The FastAPI backend validates and processes the incoming data.

### 3. Data preprocessing

The input features are transformed using the same preprocessing pipeline used during model training.

Saved preprocessing objects such as scalers can be loaded using Joblib.

### 4. Loan prediction

The processed input is passed to the trained **Random Forest Classifier**.

The model generates the predicted loan decision.

```text
Input Data
    ↓
Preprocessing
    ↓
Random Forest
    ↓
Approved / Rejected
```

### 5. SHAP explanation

SHAP is used to explain which features contributed most to the model's prediction.

Example:

```text
Prediction: Loan Rejected

Important Factors:
- Low income
- High loan amount
- Poor credit-related score
- High debt burden
```

### 6. Counterfactual recommendations

The system provides actionable suggestions based on the prediction.

For example:

```text
Current:
Income = 35,000
Loan Amount = 800,000

Recommendation:
Increase income
or
Reduce requested loan amount
```

The objective is to help the applicant understand what changes could potentially improve the prediction.

### 7. n8n automation

The prediction workflow can be connected to **n8n** through an API/webhook.

n8n can automate tasks such as:

```text
FastAPI
   ↓
Webhook
   ↓
Process Prediction
   ↓
Decision
   ↓
Generate Response
   ↓
Notification / Email / Other Automation
```

---

## 📊 Machine Learning Model

The project uses a **Random Forest Classifier** for loan approval prediction.

Random Forest was selected because it:

* Handles nonlinear relationships
* Works well with mixed feature patterns
* Provides feature importance
* Is robust against overfitting compared with individual decision trees
* Works effectively for classification tasks

---

## 🔍 Explainable AI with SHAP

A major goal of this project is to make the prediction understandable.

SHAP (**SHapley Additive exPlanations**) helps determine how individual features contribute to a prediction.

Conceptually:

```text
                 Prediction
                     │
        ┌────────────┼────────────┐
        ▼            ▼            ▼
     Income      Loan Amount   Credit Score
        │            │            │
        ▼            ▼            ▼
    Positive      Negative      Positive
     Impact        Impact        Impact
```

This allows users and developers to understand the reasoning behind the model output instead of treating the model as a black box.

---

## 🔄 Counterfactual Recommendations

Counterfactual explanations answer a practical question:

> "What could be changed to get a better prediction?"

For example:

```text
Current Prediction:
❌ Loan Rejected

Possible Improvements:
✔ Increase income
✔ Reduce loan amount
✔ Improve financial profile
```

These recommendations make the system more useful than a simple classification model.

---

## ⚡ FastAPI Backend

The backend is implemented using FastAPI.

Example API flow:

```text
POST /predict
```

Request:

```json
{
  "income": 50000,
  "loan_amount": 300000,
  "credit_score": 750
}
```

Response:

```json
{
  "prediction": "Approved",
  "probability": 0.91,
  "explanation": {},
  "recommendations": []
}
```

> The exact request and response fields depend on the final implementation.

---

## 🔗 n8n Automation

n8n is used to automate the loan approval workflow.

Example workflow:

```text
Webhook
   ↓
Receive Loan Data
   ↓
Call FastAPI
   ↓
Get Prediction
   ↓
Process Response
   ↓
Send Notification
```

This architecture allows the Machine Learning system to be integrated with external services and automated business workflows.

---

## 📁 Project Structure

```text
explainable-loan-approval-ai/
│
├── app/
│   ├── main.py
│   ├── routes/
│   ├── models/
│   ├── services/
│   └── templates/
│
├── model/
│   ├── loan_model.pkl
│   ├── scaler.pkl
│   └── other_model_files
│
├── notebooks/
│   └── loan_prediction.ipynb
│
├── data/
│   └── dataset.csv
│
├── static/
│   ├── css/
│   └── js/
│
├── templates/
│   └── index.html
│
├── n8n/
│   └── workflow.json
│
├── requirements.txt
├── README.md
└── .gitignore
```

> Update the folder structure according to your actual GitHub project before uploading.

---

## 🛠️ Installation

### Clone the repository

```bash
git clone https://github.com/Shreya9996/loan-approval-prediction-with-n8n-automation.git
```

### Navigate to the project

```bash
cd explainable-loan-approval-ai
```

### Create virtual environment

```bash
python -m venv venv
```

### Activate virtual environment

Windows:

```bash
venv\Scripts\activate
```

Linux/macOS:

```bash
source venv/bin/activate
```

### Install dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Run the FastAPI Application

```bash
uvicorn app.main:app --reload
```

The application will run locally on:

```text
http://127.0.0.1:8000
```

---

## 🔗 Connecting n8n

To connect the local FastAPI application with n8n, a public webhook/API URL can be created using a tunneling service such as Ngrok.

Example:

```text
Local FastAPI
      ↓
    Ngrok
      ↓
Public URL
      ↓
     n8n
```

The n8n workflow can then send loan application data to the FastAPI prediction endpoint.

---

## 📈 Model Evaluation

The model can be evaluated using metrics such as:

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix
* ROC-AUC

Example:

```python
from sklearn.metrics import accuracy_score

accuracy = accuracy_score(y_test, y_pred)

print("Accuracy:", accuracy)
```

---

## 🔐 Security Considerations

For production deployment:

* Do not expose secret API keys in source code.
* Use environment variables.
* Add authentication to APIs.
* Validate all incoming requests.
* Protect webhook endpoints.
* Avoid storing sensitive applicant information unnecessarily.
* Use HTTPS in production.

Example `.env`:

```text
API_KEY=your_api_key
N8N_WEBHOOK_URL=your_webhook_url
```

Add `.env` to `.gitignore`:

```text
.env
venv/
__pycache__/
*.pyc
```

---

## 🎯 Future Improvements

* [ ] Add advanced counterfactual explanation algorithms
* [ ] Improve model performance through hyperparameter tuning
* [ ] Add interactive SHAP visualizations
* [ ] Add user authentication
* [ ] Add database integration
* [ ] Deploy FastAPI to cloud
* [ ] Deploy n8n workflow
* [ ] Add email/SMS notifications
* [ ] Add applicant history dashboard
* [ ] Add model monitoring
* [ ] Add fairness and bias analysis
* [ ] Add CI/CD pipeline

---

## 🌟 Why This Project?

This project demonstrates how **Machine Learning + Explainable AI + Backend APIs + Workflow Automation** can be combined into a practical real-world application.

Instead of simply predicting:

```text
Approved / Rejected
```

the system attempts to answer:

```text
What is the prediction?
        +
Why did the model make this prediction?
        +
What changes could potentially improve the outcome?
        +
How can the complete workflow be automated?
```

---

## 👩‍💻 Author

**Shreya Patil**

B.Tech Computer Science Engineering

Interested in:

* Artificial Intelligence
* Machine Learning
* Data Science
* Generative AI
* Explainable AI
* Workflow Automation

---

## 📄 License

This project is intended for educational, research, and demonstration purposes.

Add an appropriate open-source license if you plan to distribute the project publicly.

---

## ⭐ Support

If you find this project useful, consider giving the repository a ⭐ on GitHub.

