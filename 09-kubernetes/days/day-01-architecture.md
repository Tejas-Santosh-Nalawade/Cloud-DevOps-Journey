# Day 01 - Kubernetes Architecture

## Topics Covered
- Kubernetes overview
- Control plane components
- Worker node components
- etcd, API server, Scheduler
- kubelet, kube-proxy

## Architecture
```
Control Plane:
- API Server
- etcd
- Scheduler
- Controller Manager

Worker Nodes:
- kubelet
- kube-proxy
- Container runtime
```

## Commands
```bash
kubectl cluster-info
kubectl get nodes
kubectl version
```

## Notes
