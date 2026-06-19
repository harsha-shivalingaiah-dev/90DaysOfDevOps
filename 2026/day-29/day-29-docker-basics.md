# Day 29 – Introduction to Docker

Goal is to understand what Docker is and run your first container.

You will:

* Learn why containers exist and how they differ from Virtual Machines.
* Install Docker on your machine.
* Run and explore containers from Docker Hub.

## Task 1: What is Docker?
* Is an open-source platform that automates the process of building, shipping, and running applications inside lightweight, isolated packages called containers.

## What is a Container?
* A container is a lightweight package that includes an application along with all its dependencies, libraries and configurations needed to run.
* Containers ensure that applications behave the same way across different environments.

## Why Do We Need Containers?
* Without containers, applications may work on one machine but fail on another because of different software versions or configurations.
* Containers solve the "it works on my machine" problem by packaging everything required to run the application.

# Containers vs Virtual Machines
Containers
* Share host OS kernel
* Startup time in seconds
* Resource usage is less
* Performance is near-native

Virtual Machines
* Each VM has its own OS
* Startup time in minutes
* Resource usage is more
* Performance can be additional overhead

## Docker Architecture
* Docker uses a client-server architecture where the Docker Client communicates with the Docker Daemon (dockerd), which does the heavy lifting of building, running, and distributing your containers.
* It has below components:
  - Docker Client (interface where users execute Docker commands)
  - Docker Daemon (background service that manages images, containers, networks, and volumes)
  - Docker Images (Read-only templates used to create containers)
  - Docker Containers (Running instances of Docker images)
  - Docker Registry (A storage location for Docker images)

```bash
  +------------------+               +----------------------------------------+               +---------------------+
  |   Docker Client  |               |               Docker Host              |               |   Docker Registry   |
  |                  |               |                                        |               |                     |
  |   docker build ----REST API----->|  +----------------------------------+  |               |  +---------------+  |
  |   docker pull  ----------------->|  |          Docker Daemon           |  |               |  |  ubuntu image |  |
  |   docker run   ----------------->|  |            (dockerd)             |--|--REST API---->|  +---------------+  |
  +------------------+               |  +----------------------------------+  |               |  |  nginx image  |  |

                                     |    |               |               |   |               |  +---------------+  |
                                     |    v               v               v   |               +---------------------+
                                     | +------+      +---------+     +------+ |
                                     | |Images|      |Container|     |Volume| |
                                     | +------+      +---------+     +------+ |
                                     +----------------------------------------+
```

## Task 2: Install Docker

1.Install Docker on your machine (or use a cloud instance)

https://docs.docker.com/engine/install/ubuntu/

2.Verify the installation

<img width="534" height="113" alt="image" src="https://github.com/user-attachments/assets/3d91b9f0-89cd-4e04-931e-65cd40428c84" />

3.Run the hello world container 

<img width="503" height="287" alt="image" src="https://github.com/user-attachments/assets/1fb42899-1af2-40d7-8598-8106d7a78c47" />

What Happened?
* Docker checked if the image existed locally.
* Since it wasn't available, Docker downloaded it from Docker Hub.
* The image was then used to create and run a container which displayed a success message.

## Task 3: Run Real Containers

1. Run an Ubuntu container in interactive mode — explore it like a mini Linux machine

<img width="562" height="44" alt="image" src="https://github.com/user-attachments/assets/b9677587-759e-4c31-8a4a-c9aa29cf96bd" />


<img width="491" height="182" alt="image" src="https://github.com/user-attachments/assets/80ebfbfd-5de0-4a11-844b-a00fe8788a54" />

2. List all containers (including stopped ones)

docker ps

docker ps -a

<img width="722" height="66" alt="image" src="https://github.com/user-attachments/assets/b48a8935-50f1-44b4-9031-acaacc7262b8" />

3. Stop and remove a container
* To stop a container docker stop < Name of container or container ID >
* To remove a container docker remove < Name of container or container ID >

First we have to stop the container and then remove the container

## Task 4: Explore

Run a container in detached mode — what's different?
* docker run -d nginx
* Detached mode runs the container in the background.
  
Give a container a custom name
* docker run --name my-nginx nginx
  
Map a port from the container to your host
* docker run -d -p 8080:80 nginx
* Host port - 8080
* container port - 80

View Logs
* docker logs nginx-demo

Execute Commands Inside Running Container
* docker exec -it nginx-demo bash


Important Docker commands

```bash
docker run
docker ps
docker ps -a
docker stop
docker rm
docker images
docker logs
docker exec
```
