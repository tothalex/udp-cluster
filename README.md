# Helm chart cluster definition for EKS NLB UDP application

## Create EKS Cluster
```sh
eksctl create cluster --name udp --region eu-central-1 --nodes 2 --node-type t2.medium --asg-access
```
