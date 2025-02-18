# DEPI-k8s-task
Part 1: Theory Questions (10 points)
a) Kubernetes Architecture
Core Components of a Kubernetes Cluster:

Master Node: The control plane of the cluster. It manages the cluster's state, schedules workloads, and handles API requests.

Worker Node: Runs the actual workloads (pods). Each node has a kubelet, kube-proxy, and container runtime (e.g., Docker).

etcd: A distributed key-value store that stores the cluster's configuration and state.

kube-apiserver: The front-end for the Kubernetes control plane. It exposes the Kubernetes API and handles requests.

kube-scheduler: Assigns workloads (pods) to nodes based on resource availability and constraints.

kube-controller-manager: Manages controllers like the Node Controller, Replication Controller, etc.

kubelet: An agent that runs on each node and ensures containers are running in a pod.

kube-proxy: Manages network rules and allows communication to and from pods.

What is a Pod?:

A Pod is the smallest deployable unit in Kubernetes. It can contain one or more containers that share the same network namespace, storage, and lifecycle.

Difference from Docker Container: A Docker container is a single instance of an application, while a Pod can group multiple containers that work together (e.g., a main application container and a sidecar container for logging).

b) Deployments and Services
Purpose of a Kubernetes Deployment:

A Deployment ensures that a specified number of pod replicas are running at all times. It provides declarative updates for pods and ReplicaSets.

High Availability: Deployments ensure high availability by automatically replacing failed pods and allowing rolling updates to minimize downtime.

Types of Services:

ClusterIP: Exposes the service on a cluster-internal IP. Used for internal communication within the cluster.

NodePort: Exposes the service on a static port on each node’s IP. Used for external access to the service.

LoadBalancer: Exposes the service externally using a cloud provider’s load balancer. Used for production environments.

ExternalName: Maps the service to an external DNS name. Used for integrating with external services.

c) Scaling and Autoscaling
Scaling in Kubernetes:

Kubernetes allows manual scaling by adjusting the number of replicas in a deployment using kubectl scale.

Horizontal Pod Autoscaler (HPA): Automatically scales the number of pod replicas based on CPU utilization or other metrics. For example, if CPU usage exceeds 70%, HPA increases the number of replicas to handle the load.
Part 2: Practical Tasks (15 points)
a) Create a Deployment
Deployment File: web-server-deploy.yml

This file defines a deployment with 3 replicas of the web server container.

ClusterIP Service File: web-server-service.yml

This file defines a ClusterIP service to load balance traffic across the replicas.

Commands:
# Apply the deployment
kubectl apply -f web-server-deploy.yml

# Apply the ClusterIP service
kubectl apply -f web-server-service.yml

Testing Load Balancing:

Use kubectl get pods to list the pods.

Use kubectl port-forward <pod-name> 8080:80 to forward traffic to a specific pod.

Access http://localhost:8080 to verify the web server is running.

Repeat for multiple pods to confirm load balancing.

b) Service Exposure
NodePort Service File: web-server-nodeport.yml

This file defines a NodePort service to expose the deployment externally.

Commands:
# Apply the NodePort service
kubectl apply -f web-server-nodeport.yml

Verification:

Use kubectl get services to get the external IP of the node.

Access http://<node-ip>:30080 in your browser to verify the service is reachable.

c) Scaling with Autoscaling
Horizontal Pod Autoscaler (HPA) File: web-server-hpa.yml

This file defines the HPA to scale the deployment based on CPU usage.

Commands:
# Apply the HPA
kubectl apply -f web-server-hpa.yml

Simulate High CPU Usage:

Use a stress test tool like stress inside a pod:
kubectl exec -it <pod-name> -- stress --cpu 2
Observe the scaling behavior using:

kubectl get hpa
kubectl get pods
