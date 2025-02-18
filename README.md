# Kubernetes Theory Questions

## Part 1: Theory Questions (10 points)

### a) Kubernetes Architecture

#### Core Components of a Kubernetes Cluster:
- **Master Node**: Controls the cluster and manages deployments.
- **Worker Nodes**: Run the applications inside pods.
- **etcd**: A distributed key-value store for cluster data.
- **kube-apiserver**: Exposes the Kubernetes API and handles communication within the cluster.

#### What is a Pod, and How Does it Differ from a Docker Container?
- **Pod**: The smallest deployable unit in Kubernetes that can contain one or more Docker containers.
- Unlike a single Docker container, a pod provides a shared network and storage environment for its containers.

---

### b) Deployments and Services

#### Purpose of a Kubernetes Deployment:
- Ensures applications run in a desired state with defined replicas.
- Supports updates, rollbacks, and scaling to maintain high availability.

#### Types of Services in Kubernetes:
- **ClusterIP**: Default type, accessible only within the cluster.
- **NodePort**: Exposes a service on a static port across all nodes.
- **LoadBalancer**: Uses the cloud provider’s external load balancer to expose the service.

---

### c) Scaling and Autoscaling

- Kubernetes supports horizontal scaling by increasing or decreasing the number of pods.

#### Horizontal Pod Autoscaler (HPA):
- Adjusts the number of pod replicas based on CPU or memory usage.
- Uses the **metrics-server** to monitor resource consumption.
