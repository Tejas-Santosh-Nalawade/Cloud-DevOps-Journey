# CI/CD Pipeline Project

## Overview
Complete CI/CD pipeline for a web application.

## Pipeline Flow
```
Source Code → Build → Test → Security Scan → Deploy → Monitor
```

## Components
- Source: GitHub/GitLab
- Build: Docker images
- Test: Unit + Integration tests
- Security: SonarQube, Trivy
- Deploy: Kubernetes
- Monitor: Prometheus, Grafana

## Tools Used
- Jenkins/GitHub Actions
- Docker
- Kubernetes
- SonarQube
- Trivy
- Prometheus

## Setup
```bash
# Jenkins setup
docker run -d -p 8080:8080 jenkins/jenkins

# Install plugins
- Docker Pipeline
- Kubernetes
- GitHub Integration
```

## Notes
