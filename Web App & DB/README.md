🐳 Kubernetes MongoDB + Mongo Express Mini Project
This is a simple Kubernetes project that deploys a MongoDB database along with a Mongo Express UI. It demonstrates the use of ConfigMaps, Secrets, Deployments, and Services in Kubernetes.

🛠️ Project Structure
This project includes:

MongoDB Deployment & Service

Mongo Express Deployment & LoadBalancer Service

Secrets for sensitive credentials

ConfigMap for configuration data shared between components

📁 Components Explained
✅ ConfigMap
apiVersion: v1
kind: ConfigMap
metadata:
  name: mongodb-configmap
data:
  db_url: mongo-db-service
Used to provide the MongoDB service name to Mongo Express.

🔐 Secret
apiVersion: v1
kind: Secret
metadata:
  name: mongo-secret
data:
  root_username: YWJkYWxsYWg=
  root_password: YWJkYWxsYWg=
  web_username: YWJkYWxsYWg=
  web_password: YWJkYWxsYWg=
Base64 encoded credentials used in both MongoDB and Mongo Express.

📦 MongoDB Deployment & Service
Runs 2 replicas of MongoDB with environment variables sourced from the secret:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo-db-deploy
...
MongoDB is exposed internally via:

apiVersion: v1
kind: Service
metadata:
  name: mongo-db-service
...
🌐 Mongo Express Deployment & LoadBalancer Service
Runs 1 replica of Mongo Express connected to the MongoDB service using environment variables:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo-express-deploy
...
Mongo Express is exposed to external traffic through:

apiVersion: v1
kind: Service
metadata:
  name: mongo-express-service
spec:
  type: LoadBalancer
...
Accessible at NodeIP:30001.

🚀 How to Run
Create all resources:

kubectl apply -f <your-yaml-file>.yaml
Access Mongo Express:

Visit http://<NodeIP>:30001

Login using the basic auth credentials from the secret.

Check pods/services:

kubectl get pods
kubectl get svc
