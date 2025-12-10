# DOCKER

- A Linux Container which is an isolated runtime inside of linux with process space, network interface and have disk space.

![Docker](/Tools/Docker.png)

- **Docker Image** the representation of a docker container
- **Docker Container** The standard runtime of docker
- **Docker Engine** the code which manages Docker. Creates and run Docker Containers.

### Docker Layers

Docker images are made up of layers. Each layer represents a set of file changes or instructions in the Dockerfile. Layers are stacked on top of each other to form the final image. This layering system allows for efficient storage and sharing of images.

- **Layer Caching**: When building images, Docker caches each layer. If a layer hasn’t changed, Docker reuses the cached version, speeding up the build process.
- **Union File System**: Docker uses a union file system to combine layers into a single view, allowing for efficient storage and management.

### Commands

- **docker ps** --> list all docker images running
- **docker stop XXXXX** --> stop docker image with container ID(XXXXX)
- **docker build -t <tag-name>** build docker image
- **docker run -p <host-port>:<container-port> <image-name>** map host port to a container port
