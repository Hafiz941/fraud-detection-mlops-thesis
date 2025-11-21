# Initial System Architecture Notes
Thesis: Fraud Detection Model with MLOps Deployment & Monitoring

## 1. Overview
This architecture describes how the trained fraud-detection model will be deployed, monitored, and evaluated in a production-like environment using MLOps tools such as Docker, Prometheus, Grafana, and drift-detection frameworks.

---

## 2. System Components

### 2.1 Model Training Component
- Notebook: fraud_detection_modelling.ipynb
- Algorithms tested:
  - Logistic Regression (baseline)
  - Random Forest (best performing)
- Evaluation Metrics:
  - Precision, Recall, F1-score
  - Matthews Correlation Coefficient (MCC)
- Output:
  - Final model saved as pickle file (.pkl)

---

## 3. Model Deployment Architecture

### 3.1 Containerization (Docker)
The final model will be wrapped inside a FastAPI or Flask API and containerized using Docker.

Container includes:
- model.pkl (saved model)
- prediction API endpoint
- logging & metrics export

### 3.2 REST API Flow
User Transaction → API → Model Prediction → Response

---

## 4. Monitoring Architecture

### 4.1 Prometheus
Prometheus will:
- Scrape model metrics (latency, throughput, errors)
- Collect custom ML metrics
  - number of predictions
  - fraud prediction ratio
  - drift alerts

### 4.2 Grafana Dashboard
Grafana will provide dashboards for:
- Model performance over time
- API latency
- Data drift indicators
- Fraud detection rate trends

---

## 5. Drift Detection Module

### Tools Being Considered:
- Evidently AI
- NannyML

### Drift Types:
- Data Drift (input feature distribution changes)
- Concept Drift (model performance degradation)

Outputs:
- drift_report.json
- alerts for retraining

---

## 6. Retraining Flow (Future Work)
When drift is detected:
1. Trigger pipeline
2. Load new data
3. Retrain model
4. Compare MCC score with old model
5. Deploy new version if improved

---

## 7. Deployment Diagram (Simple)

Incoming Transaction Data
        ↓
Model API (Docker)
        ↓
Prometheus Metrics Exporter
        ↓
Grafana Dashboard
        ↓
Drift Detection (Evidently / NannyML)
        ↓
Retraining Trigger (Optional Future Step)

---

## 8. Next Steps
- Build Dockerized API
- Add Prometheus metrics
- Create Grafana dashboard
- Implement drift detection notebook

