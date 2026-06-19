# Day 30 – Docker Images & Container Lifecycle

## Task 1: Docker Images

### What is a Docker Image?
* A Docker Image is a lightweight, read-only blueprint that contains everything required to run an application:

-Application code

-Runtime

-Libraries

-Dependencies

-Environment configuration

Images are immutable, meaning they cannot be modified after creation.

A running instance of an image is called a Container.

1.Pull the nginx, ubuntu, and alpine images from Docker Hub
* docker images
* docker pull alpine

<img width="457" height="103" alt="image" src="https://github.com/user-attachments/assets/90e36791-23ed-4830-870c-78e7edbfca98" />


2.List all images on your machine — note the sizes

<img width="414" height="85" alt="image" src="https://github.com/user-attachments/assets/fb977bd0-bca2-420b-8240-d58b68ebd927" />

3.Compare ubuntu vs alpine — why is one much smaller?

| Image  | Purpose                    | Approx Size |
| ------ | -------------------------- | ----------- |
| nginx  | Web Server                 | ~190 MB     |
| ubuntu | Full Linux Distribution    | ~80 MB      |
| alpine | Minimal Linux Distribution | ~8 MB       |

* Ubuntu is a linux distribution designed for broad compatibility and ease of use
* Alpine is a security-oriented, minimalist distribution

4.Inspect an image — what information can you see?

docker inspect alpine

<img width="560" height="413" alt="image" src="https://github.com/user-attachments/assets/d7275c2a-9b1f-4a01-8c3b-e038a7f8ee58" />

It has below information:
* Image ID
* Creation timestamp
* Architecture
* Environment variables
* Entrypoint
* Exposed ports
* Operating system

5.Remove an image you no longer need

docker rmi ubuntu

## Task 2: Docker Image Layers

1. Viewing Layer History
   
   docker image history nginx

   <img width="619" height="216" alt="image" src="https://github.com/user-attachments/assets/0590da1d-95b2-4af7-b722-10098107da76" />

2. What are Docker Layers?

   Every instruction inside a Dockerfile creates a new layer.

Example:
```bash
FROM ubuntu
RUN apt update
RUN apt install nginx
COPY . /app
```
Generated Layers:
```bash
Layer 1 → Ubuntu Base
Layer 2 → apt update
Layer 3 → nginx Installation
Layer 4 → Application Files
```

Why Docker Uses Layers

Storage Efficiency
* Shared layers are reused across images.

Faster Builds
* Docker rebuilds only changed layers.

Faster Downloads
* Only missing layers are downloaded.

Better Caching
* Previously built layers are reused automatically.

## Task 3: Container Lifecycle

Create a container 
* docker create --name web-server nginx

Start a container 
* docker start web-server


<img width="691" height="193" alt="image" src="https://github.com/user-attachments/assets/2bd9f2c3-f5f7-4cab-ad34-de6008ae78cd" />

Pause a container 
* docker pause web-server

Unpause a container 
* docker unpasuse web-server 

<img width="686" height="203" alt="image" src="https://github.com/user-attachments/assets/230f5dc3-581a-4a09-acf1-a08d7c48889f" />


Stop a container 
* docker stop web-server

Restart a container 
* docker restart web-server

<img width="686" height="219" alt="image" src="https://github.com/user-attachments/assets/bb9c7836-2c82-44f2-afc8-f1d5b5ed684c" />

Kill a container 
* docker kill web-server 

Remove a container 
* docker rm web-server

<img width="731" height="172" alt="image" src="https://github.com/user-attachments/assets/fbb2b9dc-7ca2-4854-a6d0-5e139c396b42" />


## Task 4: Working with Running Containers
