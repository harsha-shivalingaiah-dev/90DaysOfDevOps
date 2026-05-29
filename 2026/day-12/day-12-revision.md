# Day 12 – Breather & Revision

## Mindset & plan:are your goals still right?

* Goals are very much clear and taking small steps daily to reach it.
  
* Learning the basics and doing hands daily to build the foundation for further topics to easily understand.
  
* Showing up daily on the discord session, answering the queries asked by fellow learners and attending the doubt clearing sessions to make myself clear with the subject.

## Processes & services: 

* ps aux : To check status of all process

* journalctl : To check logs and find the root cause of a service failure

* systemctl : To check the current status of service, can be used to stop,start or restart the services

## File skills:

* echo "I am on Day 12 and revising the topics done " >>  status_check.txt

* chmod 764  devops.sh

* chown berlin:sample.txt

* cp professor.txt tokyo.txt

* mkdir -p /u01/backup/logs

## Cheat sheet refresh - Highlight 5 you would reach for first in an incident

* top or htop
  
* df -h
  
* ps aux
  
* systemctl status
  
* journalctl -u service | tail -n 20

## Mini Self-Check

### Which 3 commands save you the most time right now, and why?

* top or htop : show the running processes
  
* systemctl : to check status of service
  
* journalctl -u : Display the logs on screen instead of going to log file location

## How do you check if a service is healthy?

* systemctl status <service_name> (e.g., systemctl status sshd)
  
* service --status-all (Running services are typically marked with a [ + ])
  
* service <service_name> status
  
* journalctl -u <service_name>

* ps aux | grep <service_name> to see if a process for that service is active

## How do you safely change ownership and permissions without breaking access? Give one example command.

## What will you focus on improving in the next 3 days?

* Revisit the shell scripting recording and do build basic shell scripts.


