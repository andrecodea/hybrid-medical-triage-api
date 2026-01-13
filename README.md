# 🏥 Intelligent Hospital Triage System (Hybrid AI)

![Python](https://img.shields.io/badge/Python-3.11-blue?style=flat&logo=python)
![FastAPI](https://img.shields.io/badge/API-FastAPI-009688?style=flat&logo=fastapi)
![XGBoost](https://img.shields.io/badge/ML-XGBoost-EB4034?style=flat&logo=xgboost)
![LangChain](https://img.shields.io/badge/GenAI-LangChain-1C3C3C?style=flat&logo=langchain)
![Docker](https://img.shields.io/badge/Deploy-Docker-2496ED?style=flat&logo=docker)

> **Status:** 🚧 Work in Progress (MVP Phase)

A hybrid clinical decision support system that combines **Classic Machine Learning (XGBoost)** for precise risk classification (Manchester Triage Protocol) with **Generative AI (LLMs)** for explainability and clinical grounding.

---

## 📐 System Architecture

This project implements a **Hybrid AI Architecture** to solve the "Black Box" problem in medical AI.

```mermaid
graph LR
    User[🏥 Nurse/Doctor] -->|Symptoms Input| API[⚡ FastAPI Gateway]
    
    subgraph "Deterministic Layer (Speed & Precision)"
        API -->|Features| ML[📈 XGBoost Model]
        ML -->|Risk Level (1-5)| Result
    end
    
    subgraph "Generative Layer (Reasoning & Grounding)"
        API -->|Context + Prediction| RAG{🧠 LangChain Agent}
        RAG -->|Retrieve Protocols| VectorDB[(📚 Protocols DB)]
        VectorDB --> RAG
        RAG -->|Clinical Explanation| Result
    end
    
    Result[JSON Output] --> User
