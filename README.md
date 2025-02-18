# Kubernetes Assignment Solution

This repository contains the solution to the Kubernetes assignment, which includes both theoretical explanations and practical tasks. Below is a detailed breakdown of the solution.

---

## **Part 1: Theory Questions (10 points)**

### **a) Kubernetes Architecture**

1. **Core Components of a Kubernetes Cluster**:
   - **Master Node**: The control plane of the cluster. It manages the cluster's state, schedules workloads, and handles API requests.
   - **Worker Node**: Runs the actual workloads (pods). Each node has a kubelet, kube-proxy, and container runtime (e.g., Docker).
   - **etcd**: A distributed key-value store that stores the cluster's configuration and state.
   - **kube-apiserver**: The front-end for the Kubernetes control plane. It exposes the Kubernetes API and handles requests.
   - **kube-scheduler**: Assigns workloads (pods) to nodes based on resource availability and constraints.
   - **kube-controller-manager**: Manages controllers like the Node Controller, Replication Controller, etc.
   - **kubelet**: An agent that runs on each node and ensures containers are running in a pod.
   - **kube-proxy**: Manages network rules and allows communication to and from pods.

2. **What is a Pod?**:
   - A **Pod** is the smallest deployable unit in Kubernetes. It can contain one or more containers that share the same network namespace, storage, and lifecycle.
   - **Difference from Docker Container**: A Docker container is a single instance of an application, while a Pod can group multiple containers that work together (e.g., a main application container and a sidecar container for logging).

---

## **Part 2: Practical Tasks (15 points)**

### **a) Create a Deployment**

1. **Deployment File**: `web-server-deploy.yml`
   - This file defines a deployment with 3 replicas of the web server container.

2. **ClusterIP Service File**: `web-server-service.yml`
   - This file defines a ClusterIP service to load balance traffic across the replicas.

3. **Commands**:
   ```bash
   # Apply the deployment
   kubectl apply -f web-server-deploy.yml

   # Apply the ClusterIP service
   kubectl apply -f web-server-service.yml
