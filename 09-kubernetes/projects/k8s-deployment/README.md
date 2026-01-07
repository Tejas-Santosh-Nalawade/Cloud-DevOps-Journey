# Kubernetes Deployment Project

## Overview
Deploy a complete microservices application on Kubernetes.

## Architecture
- Frontend deployment
- Backend API deployment
- Database StatefulSet
- Redis cache
- Ingress controller
- Persistent volumes

## Components
```
├── deployments/
│   ├── frontend.yaml
│   ├── backend.yaml
│   └── database.yaml
├── services/
│   ├── frontend-service.yaml
│   ├── backend-service.yaml
│   └── database-service.yaml
├── configmaps/
├── secrets/
└── ingress.yaml
```

## Setup
```bash
kubectl apply -f deployments/
kubectl apply -f services/
kubectl apply -f ingress.yaml
```

## Notes
