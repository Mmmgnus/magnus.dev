---
title: "Deploy to Kubernetes locally"
date: 2020-09-30T18:22:00+02:00
draft: true
---

Before we can start, we need to install and setup [MiniKube](/readme/deployment/kubernetes/minikube/)

So we have our minikube for local Kubernetes cluster and we have our docker image. It is now time to deploy the container image to the cluster.

To verify that everything is working, still. Start up your minikube with `minikube start` and then check if the cluster has been created with the command `kubectl cluster-info`.

First we need to define some resources and to make it easier for use, we store all our resource yaml files in a single folder. We start by defining a Deployment resource in a file named testapp:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: testapp
spec:
  replicas: 1
  selector:
    matchLabels:
      app: testapp
  template:
    metadata:
      labels:
        app: testapp
    spec:
      containers:
        - name: app
          image: mfredlundh/testapp:1.0.0
          ports:
            - containerPort: 8080
          imagePullPolicy: Always
```

Because my docker image is in a private repository, I need to add auth credentials to make it possible to pull it down.

I first needed to create Docker credentials with this command:

```
kubectl create secret docker-registry <name> --docker-server=DOCKER_REGISTRY_SERVER --docker-username=DOCKER_USER --docker-password=DOCKER_PASSWORD --docker-email=DOCKER_EMAIL
```

- <name> will be the name of the credentials and will be used in the resource file.
- <DOCKER_REGISTRY_SERVER> is your Private Docker Registry FQDN. (https://index.docker.io/v1/ for DockerHub)
- <docker_user> is your Docker username.
- <docker_password> is your Docker password.
- <docker_email> is your Docker email.

Back in our resource file (testapp.yaml), I added this credentials to the config:
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: testapp
spec:
  replicas: 1
  selector:
    matchLabels:
      app: testapp
  template:
    metadata:
      labels:
        app: testapp
    spec:
      containers:
        - name: app
          image: mfredlundh/testapp:1.0.0
          ports:
            - containerPort: 8080
          imagePullPolicy: Always
	      imagePullSecrets:
	        - name: mycred
```

To get access to our app outside of the cluster we need a Service resource that works like a load balancer too.

In our resource file we add to the bottom:

```
---
apiVersion: v1
kind: Service
metadata:
  name: testapp
spec:
  selector:
    app: testapp
  ports:
    - port: 80
      targetPort: 8080
  type: LoadBalancer
```

```
selector:
	app: testar
```
The selector will select the Pods/container to expose according to their labels and it should match with what we specified for the pod/container in the Deployment resource.

Now that our resource definition is done we can deploy the application.

First, make sure the cluster is running, that is our [miniKube](/readme/deployment/kubernetes/minikube/).

Second, submit our yaml files to the cluster by using this command:

```
Kubectl apply -f kube
```
It will send all files that is inside our kube folder.

Open up a new terminal window and use this command to check the status of our container/pod.

```
Kubectl get pods --watch
```

You will se that the pod will transitioning from Pending from ContainerCreating to Running. And when the pod is running it is time to get access to the service url, which our service resource will provide us with.

```
Minikube service testapp
```

The service will open up your browser with the url and BAM! You now are accessing the app from the cluster.

