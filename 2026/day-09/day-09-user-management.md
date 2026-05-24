# Day 09 – Linux User & Group Management Challenge
## Task

Today's goal was to practice Linux user and group management through hands-on challenges involving:

* User creation

* Group management

* Shared directory permissions

* Team collaboration setup

## Task 1: Create Users

### Commands Used

sudo useradd -m tokyo

sudo useradd -m berlin

sudo useradd -m professor


sudo passwd tokyo

sudo passwd berlin

sudo passwd professor


<img width="614" height="451" alt="image" src="https://github.com/user-attachments/assets/6c9d0375-bfc3-4e50-9cb8-066d64b2a9ea" />


### Verification

<img width="1032" height="106" alt="image" src="https://github.com/user-attachments/assets/a9eeb9fd-bd53-4330-877a-5915543e5c06" />

<img width="410" height="111" alt="image" src="https://github.com/user-attachments/assets/4b8bee3b-1e23-4aee-a49a-0e2ce39b2117" />


---

## Task 2: Create Groups

### Commands Used

sudo groupadd developers

sudo groupadd admins

### Verification

cat /etc/group | grep -E 'developers|admins'

<img width="845" height="147" alt="image" src="https://github.com/user-attachments/assets/465cada7-b92c-4f14-bc13-4ac2c7051fc6" />

---

## Task 3: Assign Users to Groups

### Commands Used

sudo usermod -aG developers tokyo

sudo usermod -aG developers,admins berlin

sudo usermod -aG admins professor


<img width="776" height="104" alt="image" src="https://github.com/user-attachments/assets/4f8b1286-1288-4736-8a28-ad3ffe535e61" />

### Verification

groups tokyo

groups berlin

groups professor

<img width="521" height="167" alt="image" src="https://github.com/user-attachments/assets/584c1a11-07a0-4e04-baaf-b271b5da45f2" />

---

## Task 4: Shared Directory Setup

### Commands Used

sudo mkdir -p /opt/dev-project

sudo chgrp developers /opt/dev-project

sudo chmod 775 /opt/dev-project


<img width="818" height="197" alt="image" src="https://github.com/user-attachments/assets/6b0fbb08-efec-4cc5-b2ed-e65d9c8f67a7" />


### Test File Creation

sudo -u tokyo touch /opt/dev-project/tokyo-file.txt

sudo -u berlin touch /opt/dev-project/berlin-file.txt

<img width="927" height="334" alt="image" src="https://github.com/user-attachments/assets/d1ee8586-e553-4e7d-84eb-fbe4f235117b" />

---

## Task 5: Team Workspace

### Commands Used

sudo useradd -m nairobi

sudo passwd nairobi

sudo groupadd project-team

sudo usermod -aG project-team nairobi

sudo usermod -aG project-team tokyo

sudo mkdir -p /opt/team-workspace

sudo chgrp project-team /opt/team-workspace

sudo chmod 775 /opt/team-workspace

### Test File Creation

sudo -u nairobi touch /opt/team-workspace/nairobi-file.txt

### Verification
ls -ld /opt/team-workspace
ls -l /opt/team-workspace

<img width="1057" height="511" alt="image" src="https://github.com/user-attachments/assets/bfa4354f-b6a1-4ec2-88f4-44b4826c2a98" />












