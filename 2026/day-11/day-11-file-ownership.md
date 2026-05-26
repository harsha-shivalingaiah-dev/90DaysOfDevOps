# Day 11 – File Ownership Challenge (chown & chgrp)

## Tasks

Master file and directory ownership in Linux.

* Understand file ownership (user and group)

* Change file owner using chown

* Change file group using chgrp

* Apply ownership changes recursively

## Task 1: Understanding Ownership

### command: ls -l 

-rw-r--r-- 1 owner  group size date         filename

-rw-r----- 1 ubuntu ubuntu 416 May 23 17:55 nginx-logs.txt

What's the difference between owner and group?

owner: owner is the user who created the file or directory

group: group can have mulitple users and have access to shared files

<img width="681" height="147" alt="image" src="https://github.com/user-attachments/assets/1ce1502c-e13d-4363-9238-6b5006796683" />

----

## Task 2: Basic chown Operations

* Create file devops-file.txt

* Check current owner: ls -l devops-file.txt

<img width="789" height="96" alt="image" src="https://github.com/user-attachments/assets/24afe022-2d16-4ace-9e0b-a3095d5ac584" />

* Change owner to tokyo (create user if needed)

* Change owner to berlin

* Verify the changes

<img width="650" height="192" alt="image" src="https://github.com/user-attachments/assets/f3e418b7-7175-4faf-8b7d-207f8a6573a5" />




****Learning: If u try to change the owner to a user who does not exist, it gives below error****



<img width="663" height="85" alt="image" src="https://github.com/user-attachments/assets/62a25dcf-cecd-45c1-a923-560c72a74e86" />


----

## Task 3: Basic chgrp Operations

* Create file team-notes.txt
  
* Check current group: ls -l team-notes.txt

<img width="630" height="102" alt="image" src="https://github.com/user-attachments/assets/41c6f055-4634-480f-bc54-9f8a0d33ca48" />


* Create group: sudo groupadd heist-team

* Change file group to heist-team

* Verify the change

<img width="739" height="226" alt="image" src="https://github.com/user-attachments/assets/dcbd6cd7-8cf6-46a2-8b15-c0385928e13f" />

----

## Task 4: Combined Owner & Group Change

* Create file project-config.yaml
  
* Change owner to professor AND group to heist-team (one command)

  <img width="1010" height="146" alt="image" src="https://github.com/user-attachments/assets/5a836a00-9de7-445e-860d-ade650f61921" />

  <img width="811" height="73" alt="image" src="https://github.com/user-attachments/assets/6599a21c-9439-4d5b-9721-55da79c3a9e9" />

* Create directory app-logs
  
* Change its owner to berlin and group to heist-team

  <img width="793" height="267" alt="image" src="https://github.com/user-attachments/assets/d824354c-4ee0-4d10-865d-3f85552a9d29" />


## Task 5: Recursive Ownership

* Create directory structure:

  mkdir -p heist-project/vault

  mkdir -p heist-project/plans

<img width="1269" height="204" alt="image" src="https://github.com/user-attachments/assets/faab7527-c7e4-4585-834f-406a490ee148" />

<img width="637" height="86" alt="image" src="https://github.com/user-attachments/assets/99b3b3da-f331-4e0f-9a9a-e7df91a00419" />

  touch heist-project/vault/gold.txt

  touch heist-project/plans/strategy.conf

<img width="889" height="187" alt="image" src="https://github.com/user-attachments/assets/99a08dad-f3cc-49c9-abf0-9c22cc552598" />

* Create group planners: sudo groupadd planners

<img width="1016" height="247" alt="image" src="https://github.com/user-attachments/assets/9cf023aa-cd50-4ba8-b673-630c40f5a4fb" />


* Change ownership of entire heist-project/ directory:

  Owner: professor

  Group: planners

  Use recursive flag (-R)

  ls -lR heist-project


<img width="699" height="311" alt="image" src="https://github.com/user-attachments/assets/31561a79-f44f-47bb-a829-1b8d576e1e5c" />


## Task 6: Practice Challenge (20 minutes)

* Create users: tokyo, berlin, nairobi (if not already created)

* Create groups: vault-team, tech-team

* Create directory: bank-heist/

* Create 3 files inside:

touch bank-heist/access-codes.txt

touch bank-heist/blueprints.pdf

touch bank-heist/escape-plan.txt

* Set different ownership:

access-codes.txt → owner: tokyo, group: vault-team

blueprints.pdf → owner: berlin, group: tech-team

escape-plan.txt → owner: nairobi, group: vault-team

Verify: ls -l bank-heist/

<img width="1004" height="488" alt="image" src="https://github.com/user-attachments/assets/c343e8a2-40a0-484f-a6c1-8c745ec2bcd6" />

----- 

## Why This Matters for DevOps
In real DevOps scenarios, you need proper file ownership for:

* Application deployments

* Shared team directories

* Container file permissions

* CI/CD pipeline artifacts

* Log file management






