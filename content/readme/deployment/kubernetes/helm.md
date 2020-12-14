---
title: "HELM"
date: 2020-09-30T18:22:00+02:00
draft: true
---

### Create HELM Chart
To create a Chart, we run the command:
```
Helm create <chart name>
```

This command will create a folder with the name you specified. And it will contain a boilerplate for your chart.

Chart.yaml -- Contains information about the Chart like version, description type.

The templates folder contains template files for the different resource definitions that you need to deploy. Helm will use this. But we will not add our configuration to it, because we have the values.yaml file in the root.

The Value.yaml file is were we change the values in the templates. For a super basic deployment, with our node application we only need to change some values:

```
image:
  repository: reyesoft/hello-world
  tag: latest
  pullPolicy: IfNotPresent
service:
  name: hello-world
  type: LoadBalancer
  externalPort: 80
  internalPort: 8005
```

These values should be very familiar to you. We set them when we did our previous deployment. The resource definition files in the kube-folder.

In this example we specify the docker image and we add information to create a LoadBalancer service, that make it possible for us to access the application on port 80.


## Dynamic versioning in Chart file
We want to update the AppVersion to easier see what version that is deployed. And we want to update the ChartVersion.

We want the AppVersion to be the SHA-1 commit from GitHub.

One way to do that dynamically when we have built the docker image and given it the SHA-1 from the Github commit. We then want to use a template file for the Chart.yaml that we call 'Chart.yaml.tpl' and store it where the Chart.yaml file used to be. The template will contain some variables that we want to find-and-replace later.

```
appVersion: {AppVersion}
```

Our goal is to find the variables and replace them, and then store the changes in a new file called 'Chart.yaml'. This file will then have the correct version that we specified.

We will use the `sed` command to do the find-and-replace:

```
sed -e 's/{AppVersion}/<the new version>/g' -e 's/{ChartVersion}/<the new version>/g' charts/<chart name>/Chart.yaml.tpl > charts/<chart name>/Chart.yaml
```

## Links
- https://docs.nginx.com/nginx-ingress-controller/installation/installation-with-helm/