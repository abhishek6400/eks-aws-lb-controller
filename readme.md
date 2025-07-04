## 📖 Project Description

This project provides a complete step-by-step guide to install and configure the **AWS Load Balancer Controller** on an **Amazon EKS (Elastic Kubernetes Service)** cluster using **only CLI tools** — no UI console needed.

It covers:

- ✅ Creating an EKS cluster using `eksctl`
- ✅ Setting up IAM policies and service accounts
- ✅ Installing the AWS Load Balancer Controller via `Helm`
- ✅ Verifying that the controller is running correctly

This setup allows Kubernetes services (like Ingress) on EKS to use **AWS Application Load Balancers (ALBs)** for high availability and auto-scaling.

---

### 🎯 Who is this for?

- DevOps beginners learning AWS EKS
- Engineers preparing for real-world Kubernetes setup
- Anyone looking to automate ALB setup on Kubernetes

---

By the end of this project, you'll have a working EKS cluster with load balancing integrated via AWS ALB — **production-ready and cloud-native**.


# 🚀 EKS + AWS Load Balancer Controller Setup via CLI

> A complete CLI-based guide to set up AWS Load Balancer Controller on EKS.

---

##  Tools Used

-  AWS CLI  
-  eksctl  
-  kubectl  
-  Helm  
-  AWS Console  

---

# 1. AWS CLI Configuration

```bash
aws configure
# Access Key, Secret Key, Region: ap-south-1

---

 **Now you can go to the EKS + AWS Load Balancer Controlle.md for the full project commands and configuration.**
