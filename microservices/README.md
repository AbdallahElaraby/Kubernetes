# 🛍️ Microservices Demo Application (Kubernetes)

Welcome to the **Kubernetes-based Microservices Demo Application**!  
This project showcases a complete microservices architecture inspired by the [Google Cloud Microservices Demo](https://github.com/GoogleCloudPlatform/microservices-demo), deployable on any Kubernetes environment including **Minikube**, **GKE**, **EKS**, or others.

---

## 🔧 **Architecture & Services Overview**

The application is composed of several microservices, each responsible for a specific business function. These services communicate primarily over **gRPC**.

| 🧩 **Service**                | 🔌 **Port** | 📝 **Functionality**                       |
|-----------------------------|------------|--------------------------------------------|
| 🌐 `frontend`                | `8080`     | Main web UI                                |
| 🛒 `cartservice`             | `7070`     | Manages user shopping carts                |
| 💳 `checkoutservice`         | `5050`     | Handles order checkout                     |
| 💱 `currencyservice`         | `7000`     | Converts between different currencies       |
| 📧 `emailservice`            | `8080`     | Sends order confirmation emails            |
| 💰 `paymentservice`          | `50051`    | Processes payments                         |
| 🛍️ `productcatalogservice`   | `3550`     | Provides product information               |
| 🔍 `recommendationservice`   | `8080`     | Recommends additional products             |
| 🚚 `shippingservice`         | `50051`    | Provides shipping estimates                |
| 📢 `adservice`               | `9555`     | Displays contextual product ads            |
| 🧠 `shoppingassistantservice`| `80`       | AI-powered shopping assistant              |
| 🗃️ `rediscart`               | `6379`     | Redis instance for cart caching            |


    

---

## 🚀 **How to Deploy**

Make sure your Kubernetes cluster is up and running. Then, apply the manifest files to deploy all services:

```bash
kubectl apply -f <your-file-names>.yaml
```

---

## 🌐 **Ingress Setup**

To enable web access via a friendly domain:

1. Enable the ingress addon:

    ```bash
    minikube addons enable ingress
    ```

2. Edit your `/etc/hosts` file and add:

    ```
    <Minikube Node IP>   myexamplebotique.com
    ```

3. Access the app in your browser:

    ```
    http://myexamplebotique.com
    ```

---

## 📊 **Resource Configuration**

All services are optimized with lightweight resource requirements to ensure compatibility with local environments:

```yaml
resources:
  requests:
    cpu: "100m"
    memory: "64Mi"
  limits:
    cpu: "200m"
    memory: "128Mi"
```

> 💡 **Note:** The `rediscart` service is provisioned with slightly higher memory usage for caching needs.

---

## ⚙️ **Customization & Scaling**

Want to tailor the setup for production? Here's what you can do:

- 🧩 Replace or extend microservices with your own logic  
- ⚖️ Add **Horizontal Pod Autoscalers (HPA)** for scalability  
- 🔧 Adjust CPU/Memory limits to match your workload  
- 🔐 Integrate secrets, config maps, observability, and logging tools  

---

## 🙌 **Contribute & Learn**

This setup is great for:

- 🚀 Learning microservices architecture  
- 🔬 Practicing Kubernetes deployments  
- 💡 Experimenting with service mesh, observability, and DevOps pipelines  

---

✨ **Happy Deploying!**
