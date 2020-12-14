---
title: "Deploy to AWS EKS"
date: 2020-09-30T18:22:00+02:00
draft: true
---

## Push our container to Amazon Elastic Container Registry (AWS ECR)
We have already pushed up our container image to Docker Hub registry. Now we going to do the same but to AWS ECR, to make it a bit easier for us.

First we need to create a repository on ECR. I did it on the aws console on their website. Make sure you do it on the region you want it on.

Next we need to add our AWS authentication to docker so we can do the push. To do that we will use two commands, `aws ecr get-login-password --region <region>` will output our password. And we add it to docker with `docker login --username AWS --password password <aws-account-id>.dkr.ecr.<region>.amazonaws.com`

 It is possible to pipe the commands like this:
 {{< terminal >}}
aws ecr get-login-password --region <region> | docker login --username AWS --password-stdin <aws_account_id>.dkr.ecr.<region>.amazonaws.com
{{< /terminal >}}

Now when we fixed the authentication, lets push our image. 
{{< terminal >}}
Docker push <aws etc repository url>
{{< /terminal >}}

When it is done, you should see the image in the repository.


## Create cluster with eksctl
Creating a kluster the normal way in AWS is a lot of steps. But there is an easier way that do a lot of the steps for you, using WeaveWorks eksctl.

Eksctl is an CLI tool that we need to install first. We install it with Homebrew.

```
brew tap weaveworks/tap 
brew install eksctl
```

Before creating the cluster we need to create a confirmation called kubeconfig, that stores the credentials to access our Kubernetes cluster.

Create a folder in your home directory to store our configs
{{< terminal >}}
mkdir -p ~/kubeconfigs
{{< /terminal >}}

To create a cluster we run the command:

```
eksctl create cluster \
  --version 1.17 \
  --region eu-west-1 \
  --node-type t3.micro \
  --nodes 2 \
  --nodes-min 1 \
  --nodes-max 4 \
  --name chat-import
  --kubeconfig=$HOME/kubeconfigs/chat-import-config.yaml

```

## Update cluster
I forgot one time to enable private access endpoint. But I was able to update the cluster and change the configuration:
```
aws eks --region <region> update-cluster-config --name <name> --resources-vpc-config endpointPublicAccess=true,endpointPrivateAccess=true
``` 

## How to delete resources?
To delete resources (development/services) you can run this command
{{< terminal >}}
Kubectl delete -f kube
{{< /terminal >}}
It will find all our resource definitions in the kube directory and delete them on the kluster.

## Get more information
You can use `kubectl describe` command to get more information services, pods and more. Example:

```
kubectl describe svc myService
```

## Issues and solutions
{{< error type="terminal">}}
  {{< terminal >}}
    creating CloudFormation stack "eksctl-chat-import-cluster": AlreadyExistsException: Stack [eksctl-chat-import-cluster] already exists
	status code: 400, request id: 62870b2d-cce7-45c4-986d-c4eb71e86d25
  {{< /terminal >}}

  {{< error-content >}}
  Can't create a cluster because there is an cloud foundation stack with that name already


  __Solution:__ Go to the "cloud foundation" service on AWS, you will probably find the stack there. Delete it.
  {{</ error-content>}}
{{< /error >}}


### Metric-sever is collecting the metrics but hpa is unable to fetch #329
https://github.com/kubernetes-sigs/metrics-server/issues/329

@farrukh90 I was facing a similar issue with my setup and was able to solve it by using the following RoleBinding:

```
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRoleBinding
metadata:
  name: hpa-controller-custom-metrics
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: custom-metrics-server-resources
subjects:
- kind: ServiceAccount
  name: horizontal-pod-autoscaler
  namespace: kube-system
```


Listing nodegroups¶
To list the details about a nodegroup or all of the nodegroups, use:


eksctl get nodegroup --cluster=<clusterName> [--name=<nodegroupName>]
Nodegroup immutability
By design, nodegroups are immutable. This means that if you need to change something (other than scaling) like the AMI or the instance type of a nodegroup, you would need to create a new nodegroup with the desired changes, move the load and delete the old one. Check Deleting and draining.

Scaling
A nodegroup can be scaled by using the eksctl scale nodegroup command:

eksctl scale nodegroup --cluster=<clusterName> --nodes=<desiredCount> --name=<nodegroupName> [ --nodes-min=<minSize> ] [ --nodes-max=<maxSize> ]

## Links
- https://itnext.io/securing-the-base-infrastructure-of-a-kubernetes-cluster-64e79646b7bf
- https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html
- https://medium.com/@Joachim8675309/create-eks-with-an-existing-vpc-8e31d95ccc5b
- https://hub.packtpub.com/how-to-push-docker-images-to-aws-elastic-container-registryecr-tutorial/
- {{<link url="https://aws.amazon.com/eks/" title="Amazon EKS">}}Amazon EKS makes it easy for you to run Kubernetes on AWS 
without needing to install and operate your own Kubernetes clusters.
{{</ link>}}
- https://medium.com/@Joachim8675309/building-eks-with-eksctl-799eeb3b0efd
- https://www.weave.works/blog/gitops-with-github-actions-eks
- https://itnext.io/build-an-eks-cluster-with-terraform-d35db8005963