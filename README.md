🚀 Spring Boot + MongoDB Application on Kubernetes  
Production-style Kubernetes deployment using a single YAML file

✨ Project Highlights  
✅ Spring Boot application deployed on Kubernetes  
✅ MongoDB deployed with persistent storage  
✅ Single YAML file deployment (springbootmongo.yaml)  
✅ Uses core Kubernetes objects (Deployment, ConfigMap, Secret, PV, PVC, Service)  
✅ NodePort services for application access  
✅ Production-style separation of stateless and stateful components  

📌 Project Overview  
This project demonstrates a **real-world Kubernetes deployment** of a **Spring Boot application integrated with MongoDB**.

The complete deployment is managed using **one Kubernetes YAML file** named:

springbootmongo.yaml

The file contains **all required Kubernetes objects** for both the application and the database, separated using YAML document separators (`---`).

---

🏗️ Architecture Overview  
Client → NodePort Service → Spring Boot Pods → MongoDB Service → MongoDB Pod (PV/PVC)

Spring Boot runs as a **stateless application**, while MongoDB runs as a **stateful component with persistent storage**.

---

🛠️ Technologies Used  
Spring Boot  
MongoDB  
Docker (image pulled from Docker Hub)  
Kubernetes  
kubectl  
Linux  

---

📦 Kubernetes Objects Used  

The deployment uses the following Kubernetes resources:

Spring Boot:
- Deployment  
- ReplicaSet  
- ConfigMap  
- Secret  
- Service (NodePort)  

MongoDB:
- Deployment  
- ReplicaSet  
- ConfigMap  
- Secret  
- Persistent Volume (PV)  
- Persistent Volume Claim (PVC)  
- Service (NodePort)  

All the above resources are defined inside **one YAML file**.

---

📂 Deployment File Structure  

springbootmongo.yaml contains multiple Kubernetes manifests separated by:

---

This allows managing the entire application stack using a single file.

---

🧱 MongoDB Deployment (Stateful Component)  

MongoDB is deployed as a stateful service with:
- Configuration stored in ConfigMap  
- Credentials stored securely in Secret  
- Data persisted using PV and PVC  
- Service used for internal connectivity  

MongoDB data remains **persistent even if the pod restarts or is recreated**.

---

🧩 Spring Boot Deployment (Stateless Component)  

Spring Boot is deployed as a stateless application with:
- Multiple replicas for availability  
- Configuration injected using ConfigMap  
- Database credentials injected using Secret  
- Exposed externally using a NodePort Service  

Spring Boot connects to MongoDB using the MongoDB Kubernetes service name.

---

🚀 Deployment Command  

The entire application stack is deployed using a **single command**:

kubectl apply -f springbootmongo.yaml --validate=false

---

🔍 Verification Commands  

kubectl get pods  
kubectl get svc  
kubectl logs <pod-name>  

---

🌐 Application Access  

The Spring Boot application can be accessed using:

http://<Node-IP>:<NodePort>

---

🎯 Key Kubernetes Concepts Demonstrated  
✔ Single-file Kubernetes deployment  
✔ Stateless vs Stateful workloads  
✔ ConfigMaps and Secrets usage  
✔ Persistent storage with PV & PVC  
✔ Service-based networking  
✔ NodePort exposure  
✔ Production-style Kubernetes object usage  

---

🔮 Future Enhancements  
Split YAML into multiple files  
Use Ingress instead of NodePort  
Add liveness and readiness probes  
Use StatefulSet for MongoDB  
Introduce Helm charts  

---

👤 Author  
Nitheesh Kumar Bellamkonda  
DevOps Engineer | Kubernetes | Docker | Jenkins | AWS  

⭐ This project is built for learning and real-world Kubernetes practice.
