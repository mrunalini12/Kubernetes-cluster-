# 🚀 Kubernetes Cluster Deployment with CI/CD

## 📌 Project Description

This project involves setting up a local Kubernetes cluster using **Minikube** and deploying a **Node.js application** using Docker and Kubernetes. The steps include:

- Building Docker images
- Pushing them to Docker Hub
- Deploying the application on Kubernetes using YAML files
- (Optional) Setting up Jenkins for CI/CD — planned but not implemented in this version

The aim is to demonstrate how containerized applications can be deployed and managed using Docker and Kubernetes.

---

## 🛠️ Technologies Used

- **Docker** – For building, tagging, and pushing images
- **Kubernetes** – For container orchestration
- **Minikube** – Local Kubernetes cluster
- **kubectl** – Kubernetes CLI
- **Docker Hub** – Image repository
- **Git** – Version control
- **YAML** – Defining Kubernetes resources

---

## 📥 Setup Instructions

### ✅ Prerequisites

Make sure you have the following installed:

- Docker
- Minikube
- kubectl
- Docker Hub account

---

### ▶️ Steps to Run Locally

1. **Clone the repository**:
    ```bash
    git clone https://github.com/mrunalini12/Kubernetes-cluster.git
    cd Kubernetes-cluster
    ```

2. **Build the Docker image**:
    ```bash
    docker build -t my-node-app:v1 .
    ```

3. **Tag and push the image to Docker Hub**:
    ```bash
    docker tag my-node-app:v1 mrunalini01/my-node-app:v1
    docker push mrunalini01/my-node-app:v1
    ```

4. **Start Minikube**:
    ```bash
    minikube start
    ```

5. **Deploy to Kubernetes**:
    ```bash
    kubectl apply -f node-app-deployment.yaml
    kubectl apply -f my-node-app-service.yaml
    ```

6. **Access the app**:  
    Use the `NodePort` service URL to access the app in your browser:
    ```bash
    minikube service my-node-app-service
    ```

---

## 📝 Notes

- **Jenkins Setup**: Jenkins pipeline and deployment YAML were present but not used in this project.
- **CI/CD**: Manual Docker and Kubernetes deployment were followed instead of Jenkins-based automation.
- **Scalability**: Auto-scaling and Helm were not used but can be explored as future enhancements.

---

## 📄 Files Used

- `Dockerfile` – Defines the image structure
- `node-app-deployment.yaml` – Deploys the Node.js app in Kubernetes
- `my-node-app-service.yaml` – Exposes the application via a NodePort
- `Jenkinsfile` *(optional)* – Contains CI/CD stages (not used)

---

## 🔮 Future Improvements

- Implement CI/CD using Jenkins or GitHub Actions
- Add Kubernetes auto-scaling
- Use Helm charts for managing deployments
- Secure image access using Kubernetes Secrets

---
 *Maintained with love by Mrunalini.*  


