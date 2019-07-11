## Docker!

In this first workshop, you will:

1. Modify an application
2. Build the application with Docker
3. Build a Kubernetes manifest
4. Apply the Kubernetes manifest to a cluster


### Setup

Make sure you have the following tools installed and available on your computer:

1. [Docker for Desktop](https://www.docker.com/products/docker-desktop) and a [Docker Registry login](https://hub.docker.com/signup)
2. Clone the [Hello Kubernetes Git Repository](https://github.com/paulbouwer/hello-kubernetes)
3. Download the [kubectl command line tool](https://kubernetes.io/docs/tasks/tools/install-kubectl/)


### 1. Modify the application source

- Edit the server.js file to report a message that has a bit more personality


### 2. Build a docker image

- [Learn how to build an image](https://docs.docker.com/engine/reference/commandline/build/)

```
Hints:
- Use the `-t` flag to provide an image tag, a more convenient way to reference the built image.
```

### 3. Run the docker image locally

- [Learn how to run a container](https://docs.docker.com/engine/reference/run/)

```
Hints:
- Use the `-d` flag to daemonize/detach from the container
- Use the `-p` flag to expose the container port to your host machine. The application listens on port 8080, by default. Try mapping 8080 on your host machine to the contaner port 8080.
```


### 4. Publish the docker image to your docker hub

1. Make sure you are logged into Docker Hub via the Docker CLI.
2. Tag your image with your Docker Hub username and the image repository you'd like to publish it to ie: `bnookala/hello-kubernetes`

```
Hints:
- [Docker tag](https://docs.docker.com/engine/reference/commandline/tag/) will be useful here
```

### 5. Modify the hello.yaml file in this repository

1. Create yourself a namespace by any name - make sure to modify the service and the deployment that reference the same namespace
2. Modify the container image reference to point to your newly published container image


### 6. Apply the hello.yaml to your cluster, and wait!

1. Using the `kubectl` tool, apply the hello.yaml to your cluster.

```
Hints:
- Resources that are `applied` can be modified by changing the yaml file and re-applying. Resources that are `created` cannot be modified this way.
- Use the `-f` flag to specify a file.
```

### 7. Inspect the status of your cluster with kubectl

1. `kubectl get deploy -n myNamespace` will show you the status of your Kubernetes Deployments
2. Similary `kubectl get service -n myNamespace` will do the same for services

```
Hints:
- Use `kubectl describe` to get a more detailed view of the deployed resource.
```


### 8. Interact with your application

1. If your deployment went off without a hitch, and the service has an External IP address, you may open a browser and access the external IP retrieved from running `kubectl get service -n myNamespace` directly!
