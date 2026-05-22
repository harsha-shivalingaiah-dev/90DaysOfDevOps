# Day 07 – Linux File System Hierarchy & Scenario-Based Practice

## Task 

Linux File System Hierarchy (the most important directories)

Practice solving real-world scenarios step by step

### Core Directories (Must Know)
•	/ (root) 

Base of the entire file system, home of the root user – can be modified by only root.

Use this while navigating to other file systems

•	/home 

home directory of every user who logs into linux

use this to store files and settings related to individual user.

•	/root 

home directory of the super user (root) 

can read, write and edit files under this path by only root

•	/etc 

contains system-wide configuration files for applications and services

use this when adding, modifying settings or working on any issue

•	/var/log 

files that change frequently during system operation such as log files.

logs are very important for monitoring and troubleshooting issues

•	/tmp - Temporary files

stores temporary data, these files are cleared when system gets rebooted

use this if you want to store files for less time.

---
### Additional Directories (Good to Know)

•	/bin 

contains essential executable programs (compiled binaries) needed to operate the machine

this directory is accessible to all users on the system

• /usr/bin 

contains the majority of user-facing applications and utilities (python, git)

You can use this to know which all applications are installed for user

•	/opt 

location for installing third-party applications (chrome,discord,java)

I would use to check manually installed apps

---
# Hands-On Commands

## Find Largest Log Files

```bash
du -sh /var/log/* 2>/dev/null | sort -h | tail -5

ubuntu@ip-10-0-3-187:~$ du -sh /var/log/* 2>/dev/null | sort -h | tail -5
532K    /var/log/auth.log
848K    /var/log/syslog.1
860K    /var/log/syslog
5.7M    /var/log/sysstat
25M     /var/log/journal
ubuntu@ip-10-0-3-187:~$
```

## Look for a file under /etc 
```bash
cat fstab
ubuntu@ip-10-0-3-187:/etc$ cat fstab 
LABEL=cloudimg-rootfs   /        ext4   discard,commit=30,errors=remount-ro     0 1
LABEL=BOOT      /boot   ext4    defaults        0 2
LABEL=UEFI      /boot/efi       vfat    umask=0077      0 1
ubuntu@ip-10-0-3-187:
```
## Display contents of hidden files under home directory 

```bash
ls -la ~

ubuntu@ip-10-0-3-187:~$ ls -la 
total 52
drwxr-x--- 6 ubuntu ubuntu 4096 May 22 08:00 .
drwxr-xr-x 3 root   root   4096 May 12 07:55 ..
-rw------- 1 ubuntu ubuntu  118 May 21 07:20 .Xauthority
-rw------- 1 ubuntu ubuntu 2530 May 22 08:49 .bash_history
-rw-r--r-- 1 ubuntu ubuntu  220 Feb 13 12:16 .bash_logout
-rw-r--r-- 1 ubuntu ubuntu 3771 Feb 13 12:16 .bashrc
drwx------ 2 ubuntu ubuntu 4096 May 12 07:57 .cache
drwx------ 4 ubuntu ubuntu 4096 May 19 07:41 .config
-rw------- 1 ubuntu ubuntu   20 May 22 08:00 .lesshst
-rw-r--r-- 1 ubuntu ubuntu  807 Feb 13 12:16 .profile
-rw-rw-r-- 1 ubuntu ubuntu    0 May 12 08:00 .python_history
drwx------ 2 ubuntu ubuntu 4096 May 12 07:55 .ssh
-rw------- 1 ubuntu ubuntu 1584 May 20 15:02 .viminfo
drwxrwxr-x 2 ubuntu ubuntu 4096 May 21 07:25 demo
ubuntu@ip-10-0-3-187:~$
```
---

# Scenario-Based Practice

## Scenario 1: Service Not Starting
   A web application service called 'myapp' failed to start after a server reboot.
   What commands would you run to diagnose the issue?

   Step 1: Check if the service is running, failed or stopped
   
   systemctl status docker

   Step 2: If service is failed check logs
   
   journalctl -u docker -n 50

   Step 3: To check if service starts automatically on boot
   
   systemctl is-enabled docker

   Step 4: For restarting the service
   
   systemctl restart docker

## Scenario 2: High CPU Usage
   Your manager reports that the application server is slow. You SSH into the server. 
   What commands would you run to identify which process is using high CPU?

   Step 1: To Check live CPU usage
   
   top or htop 

   Step 2: To Look for processes sorted by CPU percentage
   
   ps aux --sort=-%cpu | head -10

   Step 3: If the cpu consuming process is not needed, Increase the nice value lowering the process priority so it gets less CPU time
               
   sudo renice +10 -p PID 

   Step 4: Kill CPU intensive process if needed
   
   Kill PID


 ## Scenario 3: Finding Service Logs
 
    

 ## Scenario 4: File Permissions Issue
 
    A script at /home/user/backup.sh is not executing. When you run it: ./backup.sh You get: "Permission denied"
    
    What commands would you use to fix this?
    
    Step 1: To check the permissions on script backup.sh
    
    ls -l /home/user/backup.sh
 
    Output:-rw-r--r-- (No executable permission)
    
    Step 2: Grant execute permission
    chmod +x /home/user/backup.sh

    Step 3: To check if the file get the permission 
    ls -l /home/user/backup.sh
    
    Output: -rwxr-xr-x (notice 'x' = executable)

    Step 4: Run the script
    ./backup.sh









   

   







