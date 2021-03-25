# Kubernetes Up And Running Demo

This repository follows the code provided in the Kubernetes Book (added as a PDF for reference)

## simple-node

For running a simple node application as a docker container.

To build an image:
`docker build -t simple-node .`

To run the image:
`docker run --rm -p -p 3000:3000 simple-node`

## kuard (kubernetes up and running demo)

For running the kubernetes up and running demo application

To build an image:
`docker buid -t kuard .`

To run the image:
`docker run --rm -p 8080:8080 kuard`

To tag the image:
` docker tag kuard <insert_target_docker_registry>:<insert_optional_identifier>`

To publish the image:
`docker push <insert_tag_name_from_above>`

To run the published image:
`docker run -d --name kuard --publish 8080:8080 <insert_tag_name_from_above>`

Note that additional resource contraints can be specified with the options:
`--memory 200m --memory-swap 1G --cpu-shares 1024`

To browse the kuard application:
`curl http://localhost:8080`

To stop kuard:
`docker stop kuard`

To remove kuard"
`docker rm kuard`

To delete the image:
`docker rmi <tag-name>

For more information go to Chapter 2: Creating and Running Containers page 20
in ../simple_cluster/Kubernetes_book.pdf

## kind (kubernetes in docker)

### Starting the cluster

Installing kind:
`brew install kind`

To start a cluster:
`kind create cluster`

To delete a cluster:
`kind delete cluster`

For more information go to https://kind.sigs.k8s.io/

### Dashboard UI

To deploy the Kubernetes Dashboard UI:
`kubectl apply -f \
https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml`

To make Dashboard UI available run:
`kubectl proxy`

The Dashboard will be available at
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/

Note that the UI will have RBAC configuration and a sample user will need to be created.
Follow instructions here:
https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md

### Managing pods

To start a pod from a manifest file run:
`kubectl apply -f kuard-pod.yaml`

To get pod details run:
`kubectl describe pods kuard`

To access the pod run:
`kubectl port-forward kuard 8080:8080`

### Service Discovery
