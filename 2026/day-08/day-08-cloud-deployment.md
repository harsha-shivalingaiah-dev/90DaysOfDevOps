# Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment

## Deploy a real web server on the cloud and learn practical server management

### Part 1: Launch Cloud Instance & SSH Access

Launched an EC2 instance on AWS Cloud console

<img width="1227" height="255" alt="image" src="https://github.com/user-attachments/assets/4afbe487-21cd-47b7-a903-76b601175091" />

Command: ssh -i "udaan-batch-server-key.pem" ubuntu@ec2-54-185-189-148.us-west-2.compute.amazonaws.com

<img width="1057" height="568" alt="image" src="https://github.com/user-attachments/assets/51875d02-021b-49a4-9199-a44a11888cbf" />


### Part 2: Install Docker & Nginx

sudo apt update && sudo apt upgrade -y

**sudo apt update:** This refreshes the list of available packages and their versions from the online repositories. 
It does not actually install or change any software

**sudo apt upgrade**: This installs the latest versions of all packages currently on your system based on the updated list.

Add the -y flag to skip the confirmation prompt: sudo apt upgrade -y

ubuntu@ip-172-31-42-234:~$ sudo apt install docker.io -y

ubuntu@ip-172-31-42-234:~$ docker --version

Docker version 29.1.3, build 29.1.3-0ubuntu4.1



ubuntu@ip-172-31-42-234:~$ sudo systemctl status docker

● docker.service - Docker Application Container Engine

     Loaded: loaded (/usr/lib/systemd/system/docker.service; enabled; preset: enabled)
     Active: active (running) since Sat 2026-05-23 17:14:43 UTC; 46s ago

ubuntu@ip-172-31-42-234:~$ sudo apt install nginx -y


ubuntu@ip-172-31-42-234:~$ sudo systemctl status nginx

● nginx.service - A high performance web server and a reverse proxy server

     Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)
     Active: active (running) since Sat 2026-05-23 17:21:21 UTC; 27s ago

ubuntu@ip-172-31-42-234:~$ sudo systemctl enable nginx
Synchronizing state of nginx.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install enable nginx

### Part 3: Security Group Configuration 

Test Web Access: http://<your-instance-ip>

<img width="1307" height="480" alt="image" src="https://github.com/user-attachments/assets/05797932-6b5e-4e2b-bf39-68f171fd51d1" />

### Part 4: Extract Nginx Logs 

Step 1: View Nginx Logs

<img width="1896" height="196" alt="image" src="https://github.com/user-attachments/assets/ff9c2078-f32f-4118-a9eb-c1f0f82d2e63" />


Step 2: Save Logs to File

<img width="1893" height="235" alt="image" src="https://github.com/user-attachments/assets/f456bf39-4c85-4770-b5df-f8e5c5c8d112" />

Step 3: Download Log File to Your Local Machine

<img width="1891" height="358" alt="image" src="https://github.com/user-attachments/assets/b1625d08-7ccf-44d8-9a86-b26b975d9adc" />







