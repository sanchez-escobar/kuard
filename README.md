# Kubernetes Up And Running Demo

This repository follows the code provided in the Kubernetes Book (added as a PDF for reference)

## simple-node

For running a simple node application as a docker container.

To build an image:
`docker build -t simple-node .`

To run the image:
`docker run --rm -p -p 3000:3000 simple-node`

## kuard

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
