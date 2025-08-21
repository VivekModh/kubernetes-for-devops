# Kubernetes for DevOps 🚀

This repository contains my learning and practice setup for running Kubernetes clusters locally using **Kind (Kubernetes in Docker)** and managing workloads with **kubectl**.  
It includes configuration files, installation scripts, and manifests for experimenting with Kubernetes as part of my DevOps journey.

---

## 📂 Repository Structure
kubernetes-for-devops/
│── config.yml # Kind cluster configuration
│── install.sh # Script to install dependencies (Docker, Kind, Kubectl)
│── nginx/ # Kubernetes manifests for Nginx deployments, namespaces, pods


---

## ⚙️ Setup Instructions

### 1️⃣ Clone this repository

git clone https://github.com/VivekModh/kubernetes-for-devops.git
cd kubernetes-for-devops

2️⃣ Make the install script executable and run it
chmod +x install.sh
./install.sh
This will install:

Docker

Kind

Kubectl

🖥️ Useful Commands

🔹 Check versions
docker --version
kind --version
kubectl version

🔹 Kind cluster management
# Create cluster with config file
kind create cluster --name=vivekmodh-cluster --config=config.yml

# List clusters
kind get clusters

# Delete cluster
kind delete cluster --name vivekmodh-cluster

🔹 Kubernetes cluster info
kubectl cluster-info
kubectl cluster-info --context kind-vivekmodh-cluster
kubectl cluster-info dump
kubectl get nodes

🔹 Namespace management
kubectl get namespaces
kubectl create ns nginx
kubectl delete ns nginx

🔹 Pod management
kubectl get pods -n kube-system
kubectl run nginx --image=nginx -n nginx
kubectl get pods -n nginx
kubectl delete pod nginx -n nginx
kubectl describe pod/nginx-pod -n nginx

🔹 Apply YAML files
kubectl apply -f namespace.yml
kubectl apply -f pod.yml
kubectl apply -f nginx.yml

🔹 Exec into a Pod
kubectl exec -it nginx-pod -n nginx -- bash

🛑 Troubleshooting
Sometimes nginx or apache2 may already be running on ports 80/443.
Stop them before deploying Nginx:

sudo lsof -i :80
sudo lsof -i :443
sudo systemctl stop apache2
sudo systemctl stop nginx
sudo systemctl disable nginx
✅ Learning Outcomes
Setup Kubernetes cluster with Kind

Work with kubectl for managing nodes, pods, and namespaces

Deploy and troubleshoot Nginx workloads

Hands-on practice with YAML manifests

