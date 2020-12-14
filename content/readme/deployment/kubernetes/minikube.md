---
title: "Minikube"
date: 2020-09-30T18:22:00+02:00
draft: true
---

Minikube is a tool that makes it easy to run Kubernetes locally. Minikube runs single-node Kubernetes cluster inside a Virtual Machine (VM) on your computer for users looking to try out Kubernetes or develop with it day-to-day.

## Install Minikube
Before you install Minikube, make sure you have a Hypervisor installed:
- https://github.com/moby/hyperkit
- https://www.virtualbox.org/wiki/Downloads
- https://www.vmware.com/products/fusion

You can install Minikube using Homebrew:

{{< terminal >}}
brew install minikube
{{< /terminal >}}

To confirm that the installation was successful, start up a local Kubernetes. Cluster with this command:

{{< terminal >}}
minikube start --driver=<driver_name>
{{< /terminal >}}

The driver is the same name as the hypervisor you have installed.

You can check the status of the minikube once it is up and running:

{{< terminal >}}
minikube status
{{< /terminal >}}

To stop the minikube, run:
{{< terminal >}}
minikube stop
{{< /terminal >}}

Clean up the local state
When you start up the minikube and it returns an error: "machine does not exist"

Then you need to clear the minikube's local state by running:

{{< terminal >}}
minikube delete
{{< /terminal >}}
