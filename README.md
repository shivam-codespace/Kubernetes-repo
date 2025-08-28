

# ☸️ Kubernetes Manifests – Complete Learning & Reference Repository

Welcome to the **Kubernetes Manifests Repo** 🎉
This repository contains **YAML manifest files** for various Kubernetes resources, designed to help developers, DevOps engineers, and learners **practice, understand, and deploy Kubernetes objects**.

It covers everything from **Pods and Services** to **RBAC, StatefulSets, ConfigMaps, Secrets, Volumes, and Ingress**.

If you’re learning Kubernetes or preparing for interviews, this repo will serve as your **practical lab**.

---

## 📖 What is Kubernetes?

Kubernetes (K8s) is an **open-source container orchestration platform** that automates:

* Deployment of containers
* Scaling applications up/down
* Managing networking between services
* Handling storage and configuration

With Kubernetes, you can **run containerized applications reliably in production**.

---

## 📖 What are Kubernetes Manifests?

Manifests are **YAML or JSON files** that define Kubernetes resources.

For example:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
  - name: nginx
    image: nginx:latest
```

This simple manifest creates a **Pod** running Nginx.

Your repo contains **different manifests**, each representing an important Kubernetes concept.

---

## 📂 Repository Structure

| Folder / File                                          | Description                                                                |
| ------------------------------------------------------ | -------------------------------------------------------------------------- |
| **ConfigMap/**                                         | Store non-sensitive configuration data (key-value).                        |
| **Secrets/**                                           | Store sensitive data like passwords, API keys securely.                    |
| **RBAC/**                                              | Role-Based Access Control – manage users, roles, and permissions.          |
| **Ingress/**                                           | Define external access rules (HTTP/HTTPS) to services.                     |
| **Volumes/**                                           | Define storage for pods (Persistent Volumes, PVCs).                        |
| **StatefulSet/**                                       | Manage **stateful apps** like MySQL, PostgreSQL with stable IDs & storage. |
| **DaemonSet/**                                         | Ensure one pod runs on **every node** (monitoring/logging agents).         |
| **Deployment** (recreate, rolling-update, autoscaling) | Different strategies to manage updates & scaling of apps.                  |
| **ReplicaSet & ReplicationController**                 | Ensure a fixed number of pod replicas are running.                         |
| **Services** (ClusterIP, NodePort, LoadBalancer)       | Expose applications internally or externally.                              |
| **Pods**                                               | The smallest deployable unit in Kubernetes.                                |

---

## 🏗 Kubernetes Architecture (Visual)

Here’s how resources in this repo connect together:

![Kubernetes Architecture](https://d33wubrfki0l68.cloudfront.net/25f0f8c7c905c5a58fbbfea7c8a74bcba8d2a7b8/3eecf/images/docs/components-of-kubernetes.svg)

🔹 **Mapping to this repo:**

* **Pods** → Defined in your `pod-manifest.yml`
* **Services** → (`ClusterIP`, `NodePort`, `LoadBalancer`) expose Pods
* **Ingress** → Routes external traffic to Services
* **ConfigMap & Secrets** → Provide configuration to Pods
* **Deployments, ReplicaSets, StatefulSets, DaemonSets** → Manage workloads
* **Volumes** → Provide persistent storage
* **RBAC** → Manages security and access control
* **HPA (Horizontal Pod Autoscaler)** → Automatically scales pods

---

## 🔑 Important Kubernetes Objects in this Repo

### 1️⃣ **Pod**

* The smallest deployable unit in Kubernetes.
* Runs containers.

👉 Example: `javawebapppod_manifest.yml`

---

### 2️⃣ **Service**

* Exposes pods to internal or external traffic.
* Types:

  * **ClusterIP** → Internal access only
  * **NodePort** → Exposes via a port on each Node
  * **LoadBalancer** → Uses cloud provider’s LB

👉 Example: `javawebappsvc_NodePort_service-manifest.yml`

---

### 3️⃣ **Deployment**

* Manages **stateless applications**.
* Supports:

  * **Recreate Strategy** → Stop old pods, start new ones
  * **Rolling Update Strategy** → Gradually replace pods with zero downtime
  * **Autoscaling** → Adjusts replicas based on CPU/Memory

👉 Example: `deployment_rolling_update_manifest.yml`

---

### 4️⃣ **ReplicaSet / ReplicationController**

* Ensures a specific number of pods are always running.

👉 Example: `replicaSet_manifest.yml`

---

### 5️⃣ **DaemonSet**

* Ensures **one pod per node** (e.g., logging agents like Fluentd).

👉 Example: `demonSet_manifest.yml`

---

### 6️⃣ **StatefulSet**

* For **stateful apps** (like databases).
* Provides stable network identity (`mysql-0`, `mysql-1`, …) and persistent storage.

👉 Example: `statefulSet/mysql_statefulset.yml`

---

### 7️⃣ **ConfigMap**

* Stores **non-sensitive config** in key-value format.

👉 Example: `ConfigMap/app-config.yml`

---

### 8️⃣ **Secrets**

* Stores **sensitive data** (DB passwords, API keys, certificates).

👉 Example: `Secrets/db-secret.yml`

---

### 9️⃣ **RBAC (Role-Based Access Control)**

* Manages **who can do what** in the cluster.

👉 Example: `RBAC/role-manifest.yml`

---

### 🔟 **Ingress**

* Exposes services to the **outside world** (HTTP/HTTPS).
* Supports **routing, SSL, and load balancing**.

👉 Example: `Ingress/web-ingress.yml`

---

### 1️⃣1️⃣ **Volumes**

* Provides **persistent storage** to pods.

👉 Example: `Volumes/pvc-manifest.yml`

---

### 1️⃣2️⃣ **Horizontal Pod Autoscaler (HPA)**

* Auto-scales pods based on CPU/Memory usage.

👉 Example: `hpa_autoscaling.yml`

---

## 🛠 How to Use This Repo

1. Clone the repo:

   ```bash
   git clone https://github.com/your-username/kubernetes-manifests.git
   cd kubernetes-manifests
   ```

2. Apply a manifest:

   ```bash
   kubectl apply -f <filename>.yml
   ```

3. Check resources:

   ```bash
   kubectl get all
   ```

4. Delete resources:

   ```bash
   kubectl delete -f <filename>.yml
   ```

---

## 📌 Best Practices with Kubernetes Manifests

✅ Use **Namespaces** to separate environments (dev, test, prod).
✅ Store **Secrets** in Kubernetes **Secret objects** (not plain text).
✅ Use **ConfigMaps** for non-sensitive configs.
✅ Always use **Rolling Updates** instead of Recreate (for zero downtime).
✅ Enable **Autoscaling (HPA)** for production apps.
✅ Use **RBAC** to limit access.
✅ Always define **resource requests & limits** for Pods.
✅ Use **StatefulSets** for databases instead of Deployments.

---

## 📚 Learning Resources

* 📖 [Kubernetes Documentation](https://kubernetes.io/docs/home/)
* 📦 [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
* 📘 [Kubernetes Design Patterns](https://kubernetes.io/docs/concepts/)

---

## ✨ Why This Repo is Useful

* Beginner-friendly examples of **all major Kubernetes resources**.
* Covers **stateless + stateful** applications.
* Great for **hands-on practice & interview prep**.
* Can be extended for **real-world production setups**.

---

🔥 This repo = Your **Kubernetes Lab in a Box** 🚀

