🚀 Spring Boot + MongoDB on Kubernetes (Jenkins CD – POC)

This repository demonstrates a production-style Kubernetes deployment of a Spring Boot application integrated with MongoDB, deployed using Jenkins-driven Continuous Deployment (CD).

The entire Kubernetes stack is managed using a single YAML file, making this project ideal for learning and demonstrating real-world DevOps workflows.

📌 Project Type

Proof of Concept (POC)
Built to demonstrate end-to-end DevOps deployment flow using Docker, Jenkins, and Kubernetes.

🧠 High-Level Overview

This project covers the deployment phase (CD) of an application lifecycle:

Application is already containerized using Docker

Docker image is stored in Docker Hub

Jenkins pulls the code and triggers deployment

Kubernetes orchestrates the application and database

🔁 End-to-End Flow (Build → Deploy)
Stage 1: Application Build (Already Completed)

Spring Boot application is containerized

Docker image is pushed to Docker Hub

No image rebuild during Kubernetes deployment

Stage 2: Continuous Deployment (Focus of This Project)

Jenkins pulls the repository

Jenkins executes Kubernetes deployment commands

Kubernetes pulls the Docker image and runs the application

☁️ Infrastructure Layer

Kubernetes cluster (can be local or cloud-based)

Worker nodes schedule:

Spring Boot application pods

MongoDB database pod

MongoDB uses persistent storage

🏗️ Architecture Overview
Request & Response Flow
User (Browser)
   ↓
NodePort Service
   ↓
Spring Boot Pods (Stateless)
   ↓
MongoDB Service
   ↓
MongoDB Pod (Stateful)
   ↓
Persistent Volume (PV)
   ↓
Response back to User Browser

Design Principles

Spring Boot → Stateless

MongoDB → Stateful with persistent storage

Services → Handle networking and discovery

.
├── springbootmongo.yaml       
├── Jenkinsfile 
├── pom.xml                                
├── src/                       
│   ├── main/
│   │   ├── java/               
│   │   │   └── com/example/...
│   │   └── resources/         
│   └── test/                  
└── README.md                   


📄 Kubernetes Deployment Strategy
Single YAML File Approach

All Kubernetes resources are defined in one file:

springbootmongo.yaml


Each resource is separated using YAML document separators:

---


This enables one-command deployment of the entire stack.

📦 Kubernetes Objects Used
Spring Boot (Stateless Application)

Deployment

ReplicaSet

ConfigMap

Secret

Service (NodePort)

MongoDB (Stateful Database)

ReplicaSet

ConfigMap

Secret

Persistent Volume (PV)

Persistent Volume Claim (PVC)

Service

🧱 MongoDB – Stateful Component

MongoDB is deployed with:

Configuration via ConfigMap

Credentials via Secret

Data persistence using PV & PVC

Internal access using a Kubernetes Service

✅ Data remains safe even if the pod restarts or is recreated.

🧩 Spring Boot – Stateless Component

Spring Boot is deployed with:

Multiple replicas for availability

Configuration injected via ConfigMap

Database credentials injected via Secret

Exposed externally using a NodePort Service

Spring Boot connects to MongoDB using the MongoDB service name.

🚀 Deployment via Jenkins (CD Stage)

Jenkins pipeline executes the deployment using:

kubectl apply -f springbootmongo.yaml --validate=false

What This Command Does

Pulls Docker images from Docker Hub

Creates all Kubernetes resources

Schedules pods on worker nodes

Attaches persistent storage to MongoDB

🔍 Verification & Monitoring

Check deployment status:

kubectl get pods
kubectl get svc
kubectl get pvc
kubectl logs <pod-name>

🌐 Application Access

The Spring Boot application can be accessed via:

http://<Node-IP>:<NodePort>

🎯 Key Kubernetes & DevOps Concepts Demonstrated

Jenkins-driven Continuous Deployment

Single-file Kubernetes deployment

Stateless vs Stateful workloads

ConfigMaps & Secrets

Persistent storage with PV & PVC

Service-based networking

NodePort exposure

Production-style Kubernetes design

🔮 Future Enhancements

Replace NodePort with Ingress

Use StatefulSet for MongoDB

Add liveness & readiness probes

Split YAML into multiple files

Introduce Helm charts

Build full CI/CD pipeline (CI + CD)

👤 Author

Nitheesh Kumar Bellamkonda
DevOps Engineer | Kubernetes | Jenkins | Docker | AWS

⭐ Note

This project is a Proof of Concept (POC) built for learning, practice, and real-world DevOps demonstration.
