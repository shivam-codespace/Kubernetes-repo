 
## 🚀 EKS Cluster Setup Using EC2 Management Host

### **Step 1: Create EKS Management Host**

1. Launch an **Ubuntu EC2 instance** (`t2.micro`) in AWS.
2. SSH into the instance.

👉 **Install kubectl**

```bash
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin
kubectl version --short --client
```

👉 **Install AWS CLI**

```bash
sudo apt update -y
sudo apt install unzip -y
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws --version
```

👉 **Install eksctl**

```bash
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version
```

---

### **Step 2: Create IAM Role & Attach to EC2**

1. Go to **IAM → Roles → Create Role**

   * Select **EC2** as trusted entity.
   * Attach **AdministratorAccess** policy.
   * Name it: `eksroleec2`.
2. Attach this role to the EC2 management host:

   * EC2 → Select instance → **Actions → Security → Modify IAM Role → Attach `eksroleec2`.**

---

### **Step 3: Create EKS Cluster**

Use `eksctl` to create the cluster:

👉 **For N. Virginia (us-east-1):**

```bash
eksctl create cluster --name ashokit-cluster4 \
--region us-east-1 \
--node-type t2.medium \
--nodes-min 2 \
--nodes-max 2 \
--zones us-east-1a,us-east-1b
```

👉 **For Mumbai (ap-south-1):**

```bash
eksctl create cluster --name ashokit-cluster4 \
--region ap-south-1 \
--node-type t2.medium \
--nodes-min 2 \
--nodes-max 2 \
--zones ap-south-1a,ap-south-1b
```

⏳ *Note: Cluster creation takes \~5–10 minutes.*

👉 Verify nodes after cluster creation:

```bash
kubectl get nodes
```

---

### **Step 4: Cleanup (to avoid billing)**

When done with practice, delete the cluster:

```bash
eksctl delete cluster --name ashokit-cluster4 --region ap-south-1
```



 
