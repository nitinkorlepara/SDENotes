# DOCKER

- A Linux Container which is an isolated runtime inside of linux with process space,netork interface and have disk space.

![Docker](/Tools/Docker.png)

- **Docker Image** the representation of a docker container
- **Docker Container** The standard runtime ofdocker
- **Docker Engine** the code which manages Docker. Creates and run Docker Containers.

![Docker Engine](/Tools/DockerEngine.png)

### Commands

- **docker ps** --> list all docker iamges running
- **docker stop XXXXX** --> stop docker image with container ID(XXXXX)
- **docker buid - t <tag-name->** build docker image
- **docker run -p <host-port>:<container-port> <image-name>** map host port to a conainer port 
