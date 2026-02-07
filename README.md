👇

🚀 Spring Boot + MongoDB on Kubernetes | Jenkins-Driven CD (POC)

Production-style Kubernetes deployment of a Spring Boot + MongoDB application, managed using a single YAML file and deployed via Jenkins CI/CD.

✨ Project Highlights

✅ Spring Boot deployed on Kubernetes
✅ MongoDB with persistent storage (PV & PVC)
✅ Single YAML deployment (springbootmongo.yaml)
✅ Jenkins pipeline pulls code and deploys to Kubernetes
✅ NodePort used for application access
✅ Clear separation of stateless (App) and stateful (DB) components

📌 Project Overview

This project demonstrates a real-world Kubernetes Continuous Deployment (CD) flow.

Source code is pulled by Jenkins

Docker image is fetched from Docker Hub

Application is deployed to Kubernetes using one YAML file

All Kubernetes objects are defined using --- separators

🏗️ Architecture Flow

Client
→ NodePort Service
→ Spring Boot Pods (Stateless)
→ MongoDB Service
→ MongoDB Pod (Stateful with PV/PVC)
→ Response back to client

🛠️ Tech Stack

Spring Boot

MongoDB

Docker (Docker Hub)

Jenkins (CI/CD)

Kubernetes

kubectl

Linux

📦 Kubernetes Objects Used

Spring Boot

Deployment

ConfigMap

Secret

Service (NodePort)

MongoDB

ReplicaSet

ConfigMap

Secret

Persistent Volume (PV)

Persistent Volume Claim (PVC)

Service

👉 All resources are defined inside a single YAML file

🚀 Deployment (via Jenkins)

Jenkins pipeline executes:

kubectl apply -f springbootmongo.yaml --validate=false


This:

Pulls the Docker image

Creates all Kubernetes resources

Attaches persistent storage to MongoDB

Deploys the application end-to-end

🌐 Application Access
http://<Node-IP>:<NodePort>


Verification:

kubectl get pods
kubectl get svc
kubectl logs <pod-name>

🎯 What This POC Demonstrates

✔ Jenkins-driven Kubernetes deployment
✔ Single-file Kubernetes management
✔ Stateless vs Stateful workloads
✔ ConfigMaps, Secrets, PV & PVC
✔ Production-style Kubernetes architecture

🔮 Future Enhancements

Ingress with AWS ALB

StatefulSet for MongoDB

Health probes

Helm charts

Full CI/CD automation

👤 Nitheesh Kumar Bellamkonda
DevOps Engineer | Kubernetes | Jenkins | Docker | AWS

📌 This project is a Proof of Concept (POC) built to demonstrate real-world Kubernetes CD using Jenkins.

#DevOps #Kubernetes #Jenkins #CI_CD #SpringBoot #MongoDB #Docker #CloudNative #POC #LearningByDoing
