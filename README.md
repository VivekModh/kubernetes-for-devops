Kubernetes for DevOps 🚀
A personal repository for learning and experimenting with Kubernetes locally using Kind.

This repository serves as my personal lab for mastering Kubernetes concepts as part of my DevOps journey. It contains the necessary scripts to set up a local cluster, Kubernetes manifests to deploy sample applications, and a cheatsheet of common commands.

📂 Repository Structure
kubernetes-for-devops/
├── config.yml          # Configuration file for the Kind cluster
├── install.sh          # Installation script for all dependencies
└── nginx/
    ├── namespace.yml   # Manifest for the 'nginx' namespace
    ├── pod.yml         # Manifest for a basic Nginx pod
    └── deployment.yml  # Manifest for a scalable Nginx deployment (TBD)
⚙️ Getting Started
Follow these steps to set up your local Kubernetes environment.

Prerequisites
A Linux-based environment (or WSL2 on Windows)

git for cloning the repository

sudo privileges for installing software

Installation
Clone this repository


git clone https://github.com/VivekModh/kubernetes-for-devops.git
cd kubernetes-for-devops
Make the installation script executable

chmod +x install.sh
Run the script to install dependencies
This script will install Docker, Kind, and kubectl.


./install.sh
Create your local Kind cluster
This command uses the config.yml to set up a cluster with a specific name.


kind create cluster --name=vivekmodh-cluster --config=config.yml
Your local Kubernetes lab is now ready!

🖥️ Usage & Common Commands Cheatsheet
Here is a collection of essential commands for managing the environment.

✅ Verify Installations

docker --version
kind --version
kubectl version
☸️ Kind Cluster Management
Bash

# List all Kind clusters
kind get clusters

# Delete a specific cluster to start fresh
kind delete cluster --name vivekmodh-cluster
🔎 Kubectl Cluster Inspection

# Get the status of cluster components (uses the context set by Kind)
kubectl cluster-info

# List all nodes in the current cluster
kubectl get nodes
🗂️ Managing Namespaces

# List all namespaces in the cluster
kubectl get namespaces

# Create a new namespace using the manifest file
kubectl apply -f nginx/namespace.yml

# Delete the namespace and all resources within it
kubectl delete -f nginx/namespace.yml
# OR
kubectl delete ns nginx
📦 Managing Pods (Imperative Commands)
These commands are great for quick tests and debugging.


# List all pods in the 'kube-system' namespace
kubectl get pods -n kube-system

# Run a simple Nginx pod in our 'nginx' namespace
kubectl run nginx-pod --image=nginx -n nginx

# List pods in the 'nginx' namespace
kubectl get pods -n nginx

# Get detailed information about a specific pod
kubectl describe pod/nginx-pod -n nginx

# Delete a pod
kubectl delete pod/nginx-pod -n nginx
📄 Managing Resources (Declarative Approach)
Using YAML files is the standard, repeatable way to manage applications.


# Apply all manifests in a directory
kubectl apply -f nginx/

# Apply a specific manifest file (e.g., the pod)
kubectl apply -f nginx/pod.yml
💻 Interacting with Pods

# Get a shell inside a running pod for debugging
kubectl exec -it nginx-pod -n nginx -- bash

# View the logs of a pod
kubectl logs nginx-pod -n nginx
🛑 Troubleshooting
If you have issues deploying web applications, it might be due to a port conflict on your local machine. Services like Apache2 or a local Nginx server can occupy ports 80 and 443.


# Check which process is using port 80
sudo lsof -i :80

# Stop and disable the conflicting service (example for apache2)
sudo systemctl stop apache2
sudo systemctl disable apache2
