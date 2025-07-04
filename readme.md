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

# 2. Create EKS Cluster

eksctl create cluster --name demo-cluster --region ap-south-1 --nodes 2

# 3. Create Load Balancer IAM Policy

curl -o iam_policy.json https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/main/docs/install/iam_policy.json
aws iam create-policy ^
  --policy-name AWSLoadBalancerControllerIAMPolicy ^
  --policy-document file://iam_policy.json

# 4. Create IAM Service Account

eksctl create iamserviceaccount ^
  --cluster=demo-cluster ^
  --namespace=kube-system ^
  --name=aws-load-balancer-controller ^
  --role-name=AmazonEKSLoadBalancerControllerRole ^
  --attach-policy-arn=arn:aws:iam::<your-account-id>:policy/AWSLoadBalancerControllerIAMPolicy ^
  --approve

# 5. Install AWS Load Balancer Controller With Helm

helm repo add eks https://aws.github.io/eks-charts
helm repo update

kubectl apply -k "github.com/aws/eks-charts/stable/aws-load-balancer-controller//crds?ref=master"

helm install aws-load-balancer-controller eks/aws-load-balancer-controller ^
  -n kube-system ^
  --set clusterName=demo-cluster ^
  --set serviceAccount.create=false ^
  --set serviceAccount.name=aws-load-balancer-controller ^
  --set region=ap-south-1 ^
  --set vpcId=vpc-03de7ac906232be14 ^
  --set image.tag="v2.7.1"

# 6. Verify Setup

kubectl get pods -n kube-system




