---
title: "Auto Scaling"
date: 2020-09-30T18:22:00+02:00
draft: true
intro: Auto scaling on Kubernetes
---

We going to start with a metrics-server that will collect metrics for us of our cluster:

```
helm install stable/metrics-server --name metrics-server --namespace metrics
```

I Needed to add some configuration to the metrics-server deployment resource:

```
kubectl patch deployment -n kube-system metrics-server -p='{"spec":{"template":{"spec":{"containers":[{"name":"metrics-server","args":["--cert-dir=/tmp", "--secure-port=4443", "--kubelet-insecure-tls", "--kubelet-preferred-address-types=InternalIP"]}]}}}}'
```

NOTE!
I Did not installed it like this in the end. I installed it with the following command:
```
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.3.6/components.yaml
```

It will install the metrics-service in the kube-system namespace:

```
kubectl get pods -n kube-system -l k8s-app=metrics-server
```

You should see something like this as the output:
```
kubectl get pods -n kube-system -l k8s-app=metrics-server
metrics-server-85cc795fbf-79d72   1/1     Running   0          22s
```

## Test the auto scaling
We can use Locust to test the scaling. First we need to install Locust:

```
pip3 install locust
```

## Create a HPA
```
kubectl autoscale deployment chat-import --cpu-percent=10 --min=1 --max=5
```

To see if everything is configured correctly, run the command:
```
Kubectl get hpa
```

And check that the "Target" don't have any unknown values. If it does, that means that the resource/pod is missing some configuration. Confirm that the pods development resource have request and limit resources specified, for example:
```
resources:
requests:
  memory: "64Mi"
  cpu: "100m"
limits:
  memory: "128Mi"
  cpu: "200m"
```

It can take some minutes before the HPA get metrics, so the 'Target' can show unknown even if everything is setup right. When I checked the logs of the metric server I saw some logs:
```
1 reflector.go:289] k8s.io/client-go/informers/factory.go:133: watch of *v1.Pod ended with: too old resource version: 3110688 (3119140)
W1103 01:34:26.227875       1 reflector.go:289] k8s.io/client-go/informers/factory.go:133: watch of *v1.Pod ended with: too old resource version: 3119140 (3135739)
W1103 04:47:35.616987       1 reflector.go:289] k8s.io/client-go/informers/factory.go:133: watch of *v1.Pod ended with: too old resource version: 3135739 (3175402)
E1103 14:39:42.765513       1 reststorage.go:160] unable to fetch pod metrics for pod default/seismo-server-79954d68b9-2schw: no metrics known for pod
E1103 14:39:57.779029       1 reststorage.go:160] unable to fetch pod metrics for pod default/seismo-server-79954d68b9-2schw: no metrics known for pod
E1103 14:40:13.190275       1 reststorage.go:160] unable to fetch pod metrics for pod default/seismo-server-79954d68b9-2schw: no metrics known for pod
```

## Custom counters for Prometheus with Node applications
- https://github.com/tdeekens/promster

## Links
 - https://aws.amazon.com/premiumsupport/knowledge-center/eks-metrics-server-pod-autoscaler/
- https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/
- https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/
- https://www.padok.fr/en/blog/autoscaling-kubernetes