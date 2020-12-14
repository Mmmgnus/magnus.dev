---
title: "Deployment"
date: 2020-09-30T18:22:00+02:00
draft: true
---


## Docker container
We need to create an container that contains our application. To do that we need a named 'Dockerfile', this file is the recipe that will tell Docker how to start up everything in the container.

```
FROM node:12.0-slim
COPY . .
RUN npm install
CMD [ "node", "index.js" ]
```

The above Dockerfile includes the following commands:

- FROM defines the base layer for the container, in this case, a version of Ubuntu with Node.js installed
- COPY copies the files of your app into the container
- RUN executes npm install inside the container
- CMD defines the command that should be executed when the container starts

With the Dockerfile ready, we can build our container image

```
docker build -t <name/"tag"> <location of dockerfile> 
```

So in my case I run:
```
docker build -t testapp . 
```

To see all docker images on your computer, run: `docker images`

To save the container image as a file, run: `docker save testapp > testapp.tar`

### Docker network
To make containers be able to talk to each other, they need to be on the same "network". 

```
docker network create <name>
```

And you specify the network when you run the containers:

```
docker run --name=mongo --rm --network=myNetwork mongo
```

### Environment variables
It is possible to specify environment variables when you run a container by using the -e flag

### Build arguments when building the docker image
It's possible to add arguments when we build a docker image.

#### Install private NPM packages
To be able to install private packages when building the Docker image, we will need to authenticate is some way. The way we did it in one project was to send in the auth token. This can be done by adding `//package.reposity.url/:authToken <auth token>` to the .npmrc file.

But to do that we had to send in the NPM token with the build command. The build arguments here we come!

First we defined the argument in the Dockerfile:
```
ARG NPM_TOKEN=""
```

The ARG command let us set a default value. In our case we didn't want one.

Then we need to add the value in the argument to the environment variable:
```
ENV TOKEN=$NPM_TOKEN
```

Now we have an environment variable named TOKEN that we can use.

In our docker file we set the registry url with this command:
```
RUN npm config set //packages.whalebone.dev/:_authToken $TOKEN
```

Our docker file should look like something like this:
```
FROM node:12.0-slim
ARG NPM_TOKEN=""
ENV TOKEN=$NPM_TOKEN
COPY . .
RUN npm config set //package.reposity.url/:_authToken $TOKEN
RUN npm install
CMD [ "node", "index.js" ]
```

Now when we run the bild command with the `--build-arg <token>` the private packages is successfully installed.

### Uploading docker container
One nice thing about docker containers is that it is easy to share the docker image with others. Either by sharing the docker image file or you can upload the image to a container registry, like Docker Hub.

To do so, you first need a docker account. When you have one then you can login via the docker cli:

```
docker login
```

Before you can upload the image to Docker Hub, the image needs a name with the following format: `username/image:tag`

- username is your Docker ID
- image is the name of the image
- tag is an optional additional attribute — often it is used to indicate the version of the image

To rename the image to can run the following command:
```
docker tag testapp <username>/testapp:1.0.0
```

To upload the image run:
```
docker push <username>/testapp:1.0.0
```

## Links
- https://learnk8s.io/nodejs-kubernetes-guide