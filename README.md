# Kubernetes Minikube Setup & Commands Guide

## **1️⃣ Prerequisites**
### **System Requirements**
- **OS:** Windows, macOS, or Linux
- **RAM:** Minimum 4GB
- **CPU:** Minimum 2 cores
- **Virtualization enabled** (for Minikube)

### **Install Dependencies**
- **[Docker](https://www.docker.com/)** (preferred) or VirtualBox (if no Docker)
- **[kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)** (Kubernetes CLI)

## **2️⃣ Install Minikube**
### **Windows (Using Chocolatey or Scoop)**
#### Option 1: Using Chocolatey  
```powershell
choco install minikube
```
#### Option 2: Using Scoop  
```powershell
scoop install minikube
```

### **Linux (Debian/Ubuntu)**
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

### **MacOS (Using Homebrew)**
```bash
brew install minikube
```

## **3️⃣ Install kubectl (Kubernetes CLI)**

### **Windows**
```powershell
choco install kubernetes-cli
```

### **Linux**
```bash
sudo apt-get update && sudo apt-get install -y kubectl
```

### **MacOS**
```bash
brew install kubectl
```

## **4️⃣ Start Minikube**
Run Minikube using Docker:  
```bash
minikube start --driver=docker
```
Check Minikube status:  
```bash
minikube status
```

## **5️⃣ Verify Kubernetes Cluster**
Check if Minikube is running properly:  
```bash
kubectl get nodes
```

## **6️⃣ Deploy a Sample Application**
Create a simple deployment:  
```bash
kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
```
Expose it as a service:  
```bash
kubectl expose deployment hello-minikube --type=NodePort --port=8080
```
Check the services:  
```bash
kubectl get services
```

## **7️⃣ Access the Application**
### **Option 1: Automatically Open in Browser**
```bash
minikube service hello-minikube
```

### **Option 2: Manually Open in Browser**
Find Minikube IP:  
```bash
minikube ip
```
Access the app at:  
```
http://<MINIKUBE_IP>:<NODEPORT>
```
Example:  
```
http://192.168.49.2:31063
```

### **Option 3: Use a LoadBalancer (For External Access)**
```bash
kubectl expose deployment hello-minikube --type=LoadBalancer --port=8080
```
Enable network tunneling:  
```bash
minikube tunnel
```

## **8️⃣ Stop & Delete Minikube (If Needed)**
Stop Minikube:  
```bash
minikube stop
```
Delete Minikube cluster:  
```bash
minikube delete
```

## **9️⃣ Additional Commands**
### **Check All Running Pods**
```bash
kubectl get pods
```
### **Describe a Pod**
```bash
kubectl describe pod <POD_NAME>
```
### **Delete a Deployment**
```bash
kubectl delete deployment <DEPLOYMENT_NAME>
```
### **Delete a Service**
```bash
kubectl delete service <SERVICE_NAME>
```

---
✅ **Kubernetes Minikube is set up successfully!** 🚀
