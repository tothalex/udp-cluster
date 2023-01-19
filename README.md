`export AWS_REGION=eu-central-1 # Define the AWS region`

`export CLUSTER_NAME=myenergi # Cluster name`

`export KUBECONFIG=${HOME}/.kube/myenergi # Define a new KUBECONFIG for the example`

## Create Cluster in AWS

`eksctl create cluster --name ${CLUSTER_NAME} --region ${AWS_REGION} --nodes 2 --node-type t2.medium --asg-access`

specifying the _--asg-access_ we enable the horizontal pod auto scalling

## Install AWS Load Balancer Controller [AWS Guide](https://docs.aws.amazon.com/eks/latest/userguide/aws-load-balancer-controller.html)

[_Make sure you install Amazon VPC CNI_](https://docs.aws.amazon.com/eks/latest/userguide/eks-add-ons.html)

[Troubleshoot](https://aws.amazon.com/premiumsupport/knowledge-center/load-balancer-troubleshoot-creating/)

## Install the service

`helm install cluster .`

_Troubleshoot Service_

`kubectl get all` _make sure the service/packet-handler has an external-ip_

`kubectl describe service/packet-handler` _make sure there is no error in the events section_

_after the install the aws needs about 10-15 min to create the nlb in the AWS_

[_you can check the nlb status on the AWS EC2 page_](https://eu-central-1.console.aws.amazon.com/ec2/v2/home?region=eu-central-1#LoadBalancers:sort=loadBalancerName)

[_you can also check the pods as target groups on the AWS EC2 page under the Target Groups tab_](https://eu-central-1.console.aws.amazon.com/ec2/v2/home?region=eu-central-1#TargetGroups:)
