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
