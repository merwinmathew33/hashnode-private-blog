# Basics of Docker-1

### Introduction

Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as one package.

Using Docker, you can quickly and easily deploy applications predictably and consistently, regardless of the environment. This makes it easier to develop and test applications, as well as to deploy them to production environments.

### Components of Docker

* **Docker Engine**: This is the core component of Docker, which is responsible for building, running, and distributing Docker containers. It is a lightweight runtime that sits on top of the host operating system and handles the containers.
    
* **Docker Hub**: This is a cloud-based registry service for storing and distributing Docker images. It is a central place to store and manage Docker images, and it is free to use for public images.
    
* **Docker Compose**: This is a tool for defining and running multi-container Docker applications. It allows you to use a YAML file to define the configuration for your application and all of its components, and then use a single command to bring everything up or down.
    
* **Docker Swarm**: This is a tool for orchestrating a cluster of Docker nodes and scheduling the containers on those nodes. It allows you to create a cluster of Docker engines and use them to run your containers in a highly available and scalable manner.
    

### Docker architecture

* **Docker Client**: This is the command-line interface (CLI) that you use to interact with the Docker daemon. You can use the Docker client to build, run, and manage Docker containers.
    
* **Docker Daemon**: This is the background process that runs on the host machine and listens for Docker API requests. It is responsible for building, running, and distributing Docker containers.
    
* **Docker Images**: These are lightweight, stand-alone, and executable packages that include everything needed to run a piece of software, including the application code, libraries, dependencies, and runtime. Each Image has its unique ID and a tag for a different version.
    
* **Docker Containers**: These are running instances of Docker images. You can create, start, stop, move, or delete a container using the Docker API or CLI.
    
* **Docker Registries**: These are places where Docker images are stored and managed. The Docker Hub is a public registry that contains a large number of Docker images, including the official images for popular software like Ubuntu, CentOS, and MySQL.
    

### Working of Docker

Docker works by using a client-server architecture. The Docker client communicates with the Docker daemon, which does the heavy lifting of building, running, and distributing Docker containers.

Here's how it works:

1. You use the Docker client to build an image from a Docker file. A Dockerfile is a text file that contains instructions for building an image.
    
2. The Docker daemon builds the image and stores it in a local registry on the host machine.
    
3. You use the Docker client to run a container from the image. The Docker daemon creates a container and runs the application inside it.
    
4. The application inside the container listens on a specific port, and the Docker daemon maps that port to a port on the host machine. This allows you to access the application from the host machine.
    
5. You can start, stop, move, or delete the container using the Docker API or CLI.
    

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652725115656/gzzhoxEQZ.png?auto=compress,format&format=webp align="left")

### Basic Docker commands

* `docker build`: Build an image from a Dockerfile
    
* `docker run`: Run a container from an image
    
* `docker start`: Start a stopped container
    
* `docker stop`: Stop a running container
    
* `docker rm`: Remove a container
    
* `docker rmi`: Remove an image
    
* `docker images`: List all images on the host
    
* `docker ps`: List all running containers
    
* `docker exec`: Run a command in a running container
    

I hope this helps! Let me know if you have any other questions. Follow me to get more details about docker.