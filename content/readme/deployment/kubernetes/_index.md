---
title: "Kubernetes"
date: 2020-09-30T18:22:00+02:00
draft: true
intro: Deployment with Kubernetes
---

## Create Secrets
It is possible to create secrets in kubernetes which can be accessed by for example HELM.

To create secrets you use this command:
```
	kubectl create secret generic secretName --from-literal=variableName=yoursecret --from-literal=variableName=yourothersecret
```

Then you can access it like this:
```
env:
  - name: SECRET_1
    valueFrom:
      secretKeyRef:
        name: secretName
        key: yoursecret
  - name: SECRET_2
    valueFrom:
      secretKeyRef:
        name: secretName
        key: yourothersecret
```

## Edit secrets
To edit secrets run this command:
```
kubectl edit secrets mysecret
```

## Enable TLS
This information has something to do with our ingress
```
If TLS is enabled for the Ingress, a Secret containing the certificate and key must also be provided:

  apiVersion: v1
  kind: Secret
  metadata:
    name: example-tls
    namespace: foo
  data:
    tls.crt: <base64 encoded cert>
    tls.key: <base64 encoded key>
  type: kubernetes.io/tls
```

## Using Namespaces
It is possible to deploy resources in different namespaces. Useful if you want to hava development and production environment in the same kluster.

- https://kubernetes.io/blog/2015/08/using-kubernetes-namespaces-to-manage/
- http://vadimeisenberg.blogspot.com/2019/03/multicluster-pros-and-cons.html

## Monitoring the kluster
- https://www.eksworkshop.com/intermediate/240_monitoring/

## Tools
- https://kube-forwarder.pixelpoint.io/
## Links
- https://blog.gruntwork.io/how-to-build-an-end-to-end-production-grade-architecture-on-aws-part-1-eae8eeb41fec
- https://app.getambassador.io/initializer/
- https://www.fairwinds.com/blog/best-practices-for-implementing-ci-cd-pipelines-in-kubernetes
- https://www.eksworkshop.com/beginner/091_iam-groups/test-cluster-access/
- https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html
- https://medium.com/@karan.brar/configure-letsencrypt-and-cert-manager-with-kubernetes-3156981960d9
- https://medium.com/@Joachim8675309/adding-ingress-with-amazon-eks-6c4379803b2#3acb
- {{<link url="https://aws.amazon.com/ecr/" title="Amazon ECR">}}Amazon ECR | Docker Container Registry | Amazon Web Services{{</ link>}}

- https://gruntwork.io/guides/kubernetes/how-to-deploy-production-grade-kubernetes-cluster-aws/#kubernetes-architecture
- https://learnk8s.io/nodejs-kubernetes-guide