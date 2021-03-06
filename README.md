# Docker-In-Docker

Jenkins image with the docker client installed for cases where you want to run docker commands from Jenkins but connect to a daemon running elsewhere (for example the same daemon running this container). The docker daemon is *not* running inside of the container.
The task will run as second process inside the image via UNIX socket mapping.

# Tags

`1.7` `latest` - Contains docker client 1.7

`1.6` - Contains docker client 1.6.2

# Usage
## Using a unix socket

    1) Do a git clone : git clone https://github.com/Ashish-Chaturvedi/Docker-In-Docker.git
    2) build the docker image with a tag name
    3) docker run --privileged=true -p 8080:8080 -v /var/run/docker.sock:/var/run/docker.sock docker-jenkins-client

## Using a remote docker host

    docker run -e DOCKER_HOST="tcp://10.10.10.10:2760" docker-jenkins-client

## Environment Variables

`DOCKER_OPTS` - additional `docker` command line arguments. e.g.

    docker run -e DOCKER_OPTS="-l debug" -v /var/run/docker.sock:/var/run/docker.sock docker-jenkins-client
