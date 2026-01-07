# MLOps Pipeline Project

## Overview
End-to-end ML pipeline with deployment and monitoring.

## Architecture
```
Data Source → Feature Store → Training Pipeline → Model Registry
                                                        ↓
                                            Serving Infrastructure
                                                        ↓
                                                  Monitoring
```

## Components
1. **Data Pipeline**
   - Data ingestion
   - Data validation
   - Feature engineering

2. **Training Pipeline**
   - Model training
   - Hyperparameter tuning
   - Model evaluation
   - Model versioning

3. **Deployment**
   - Model serving (REST API)
   - Batch inference
   - Real-time inference

4. **Monitoring**
   - Performance metrics
   - Data drift
   - Model drift
   - Alerting

## Tech Stack
- MLflow (experiment tracking)
- DVC (data versioning)
- FastAPI (model serving)
- Docker + Kubernetes (deployment)
- Prometheus + Grafana (monitoring)

## Setup
```bash
# Train model
python train.py

# Start MLflow server
mlflow ui

# Deploy model
docker build -t ml-model .
kubectl apply -f deployment.yaml

# Monitor
python monitor.py
```

## Notes
