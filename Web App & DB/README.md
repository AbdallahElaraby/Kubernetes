# 🐳 Kubernetes MongoDB + Mongo Express

This project deploys a MongoDB instance with a Mongo Express UI using Kubernetes.

## 🧱 Stack Overview

- **MongoDB**: Backend database
- **Mongo Express**: Web UI to interact with MongoDB
- **Kubernetes Resources**:
  - `ConfigMap`: MongoDB service name
  - `Secret`: Encoded credentials
  - `Deployments`: MongoDB and Mongo Express
  - `Services`: Internal (MongoDB) & LoadBalancer (Mongo Express)

## 🚀 Usage

###  Deploy all resources
kubectl apply -f .

Open in browser:
http://<NodeIP>:30001
Use the credentials from the secret (default: abdallah / abdallah).
