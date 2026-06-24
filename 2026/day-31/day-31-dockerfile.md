# Day 31 – Dockerfile: Build Your Own Images

## Task 1: Your First Dockerfile

* Create a folder called my-first-image

  ubuntu@ip-172-31-33-163:~/my-first-image$
  
* Inside it, create a Dockerfile that:

```bash

FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y curl

CMD ["echo", "Hello from my custom image!"]
```
  - Uses ubuntu as the base image
  - Installs curl
  - Sets a default command to print "Hello from my custom image!"
  
  - Build the image and tag it my-ubuntu:v1

    docker build -t my-ubuntu:v1
    
  - Run a container from your image

    docker run my-ubuntu:v1


    <img width="580" height="166" alt="image" src="https://github.com/user-attachments/assets/a4a1ba27-0271-4215-bc3f-5e137b9059db" />

    <img width="403" height="179" alt="image" src="https://github.com/user-attachments/assets/d8e3cbf3-b1b1-47b7-a8db-480529f3dcb1" />

## Task 2: Dockerfile Instructions

Create a new Dockerfile that uses all of these instructions:

```bash
FROM — base image
RUN — execute commands during build
COPY — copy files from host to image
WORKDIR — set working directory
EXPOSE — document the port
CMD — default command
Build and run it. Understand what each line does
```


Dockerfile

```bash
FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y curl

WORKDIR /app

COPY apps.txt .

EXPOSE 8080

CMD ["cat", "apps.txt"]

```



