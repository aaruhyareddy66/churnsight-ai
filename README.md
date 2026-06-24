# churnsight-ai
<div align="center">

![ChurnSight AI](https://img.shields.io/badge/ChurnSight-AI-58A6FF?style=for-the-badge&logo=python&logoColor=white)
![ML](https://img.shields.io/badge/Machine_Learning-XGBoost-orange?style=for-the-badge)
![RAG](https://img.shields.io/badge/RAG-FAISS-green?style=for-the-badge)
![LLM](https://img.shields.io/badge/LLM-LLaMA_3.3_70B-purple?style=for-the-badge)
![Deploy](https://img.shields.io/badge/Deployed-Live-brightgreen?style=for-the-badge)

### An end-to-end Machine Learning system that predicts customer churn with AI-powered retention insights

**[🚀 Live Demo](https://churnsight-frontend-8c1k.vercel.app)** • **[Backend Code](https://github.com/aaruhyareddy66/churnsight-backend)** • **[Frontend Code](https://github.com/aaruhyareddy66/churnsight-frontend)**

</div>

---

## 🌟 What is ChurnSight AI?

ChurnSight AI is a full-stack machine learning application I built to predict which customers are likely to leave a telecom company — and more importantly, **why** they might leave and **what to do about it**.

The system doesn't just make predictions. It explains them using SHAP values, retrieves relevant retention knowledge using a RAG pipeline, and lets you have a conversation with an AI analyst powered by LLaMA 3.3 70B.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🎯 **Single Prediction** | Enter any customer's details and get instant churn probability with recommendations |
| 📊 **Bulk Prediction** | Upload a CSV file to analyze thousands of customers at once |
| 🤖 **AI Chat** | Ask retention questions — answered by LLaMA 3.3 70B grounded in domain knowledge |
| 📈 **Analytics Dashboard** | Model performance metrics and SHAP feature importance charts |

---

## 🧠 Tech Stack

```
┌─────────────────────────────────────────────────────┐
│                   React Frontend                     │
│              (Recharts + Tailwind)                   │
│           Deployed on Vercel                         │
└──────────────────────┬──────────────────────────────┘
                       │ REST API
┌──────────────────────▼──────────────────────────────┐
│                 FastAPI Backend                      │
│              Deployed on Render                      │
└────────┬─────────────┬──────────────────────────────┘
         │             │
┌────────▼──────┐ ┌────▼──────────────────────────────┐
│  ML Pipeline  │ │         RAG + LLM Pipeline         │
│  XGBoost      │ │  FAISS Vector Search               │
│  SHAP Values  │ │  Keyword Embeddings                │
│  73% Accuracy │ │  LLaMA 3.3 70B via Groq API        │
│  79% ROC-AUC  │ │                                    │
└───────────────┘ └────────────────────────────────────┘
```

---

## 📊 Model Performance

| Metric | Score |
|--------|-------|
| Accuracy | 73% |
| ROC-AUC | 78.76% |
| Dataset Size | 5,000 customers |
| Features Used | 14 |

### Top Churn Factors (SHAP)
1. **Contract Type** — Month-to-month customers churn 3x more
2. **Monthly Charges** — High bills correlate with churn
3. **Tenure** — New customers (< 12 months) are highest risk
4. **Total Charges** — Lifetime value indicator
5. **Internet Service** — Fiber optic has higher churn rate

---

## 🏗️ Architecture

### ML Pipeline
- Trained **XGBoost classifier** on synthetic Telco customer data
- Used **SHAP TreeExplainer** for per-prediction explainability
- Features include contract type, tenure, monthly charges, payment method, and service add-ons

### RAG Pipeline
- Built a knowledge base of **15 churn retention insights**
- Implemented **keyword-based semantic retrieval** to find top-3 relevant chunks per query
- Injected retrieved context into LLM system prompt for grounded answers

### API Layer
- **FastAPI** with 5 endpoints: `/predict`, `/predict-bulk`, `/chat`, `/analytics`, `/health`
- Full **CORS** support for cross-origin requests
- Pydantic models for request validation

---

## 🚀 Run Locally

### Prerequisites
- Python 3.10+
- Node.js 18+
- Groq API Key (free at [console.groq.com](https://console.groq.com))

### Backend
```bash
cd backend
python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # Mac/Linux

pip install -r requirements.txt

# Create .env file
echo "GROQ_API_KEY=your_key_here" > .env

# Train the ML model
python train_model.py

# Start backend
uvicorn main:app --reload --port 8000
```

### Frontend
```bash
cd frontend
npm install
npm run dev
```

Open **http://localhost:3000** 🎉

---

## 📁 Project Structure

```
churnsight/
├── backend/
│   ├── main.py              # FastAPI app — all endpoints
│   ├── train_model.py       # XGBoost training script
│   ├── requirements.txt
│   ├── models/
│   │   ├── xgb_churn_model.pkl
│   │   ├── label_encoders.pkl
│   │   ├── scaler.pkl
│   │   └── model_metadata.json
│   └── data/
│       └── telco_churn.csv
│
└── frontend/
    ├── src/
    │   ├── App.jsx           # Full React app
    │   └── main.jsx
    ├── index.html
    ├── package.json
    └── vite.config.js
```

---

## 🎤 Key Learnings

- Built a complete **end-to-end ML pipeline** from data generation to deployment
- Implemented **RAG (Retrieval Augmented Generation)** to ground LLM answers in domain knowledge
- Learned how to serve ML models via **REST APIs** using FastAPI
- Deployed a full-stack app using **Render + Vercel** with CI/CD via GitHub

---

## 📬 Contact

**Aaruhya Reddy**
- GitHub: [@aaruhyareddy66](https://github.com/aaruhyareddy66)
- Live Project: [churnsight-frontend-8c1k.vercel.app](https://churnsight-frontend-8c1k.vercel.app)

---

<div align="center">
  <sub>Built with ❤️ by Aaruhya Reddy</sub>
</div>
