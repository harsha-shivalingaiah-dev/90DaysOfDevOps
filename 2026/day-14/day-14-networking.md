# Day 14 - Networking Fundamentals & Hands-on Checks

## Quick Concepts

### OSI Model vs TCP/IP

OSI Model has 7 layers from Physical to Application.

* Application,Presentation,Security,Transport,Network,Data Link and Physical.

TCP/IP simplifies networking into 4 layers

* Link, Internet, Transport, and Application.

## Where IP, TCP/UDP, HTTP/HTTPS, DNS sit in the stack

* IP works at the Internet layer.
  
* TCP and UDP work at the Transport layer.
  
* HTTP/HTTPS and DNS work at the Application layer.


## Real Example

curl https://google.com

Application Layer (HTTP/HTTPS) → TCP → IP → Network Link

<img width="1026" height="372" alt="image" src="https://github.com/user-attachments/assets/e94a2ad7-cb9a-471d-887a-5b45fc2f4377" />

## Hands on check list 

* Identity (ip addr) : hostname -I

  Note your IP

  <img width="625" height="147" alt="image" src="https://github.com/user-attachments/assets/d706b388-5e6d-4992-a788-274cf35e7632" />

* Reachability Test

  ping -c 4 google.com
  
  <img width="850" height="386" alt="image" src="https://github.com/user-attachments/assets/0099a0c4-e923-4b14-aada-fa5324f8c021" />

* Path: traceroute (or tracepath)

   traceroute google.com


<img width="1678" height="338" alt="image" src="https://github.com/user-attachments/assets/e6bd191f-3fbf-4132-bbee-b10bcbb61f23" />

* Ports: ss -tulpn (or netstat -tulpn)

  <img width="1816" height="347" alt="image" src="https://github.com/user-attachments/assets/1814b632-eecc-48a4-af88-59a05304d9de" />

* Name resolution: dig or nslookup

  $ dig google.com

  * Observation:

  Domain successfully resolved to an IP address.


  <img width="868" height="413" alt="image" src="https://github.com/user-attachments/assets/bdce97f4-7008-4871-a44f-3cdb4aa62702" />


 * HTTP Check

   curl -i https://google.com

   Observation:

    HTTP status code received successfully.

   <img width="1897" height="439" alt="image" src="https://github.com/user-attachments/assets/ac73dda3-01d6-4bb1-bc02-249cb9ef95d6" />

 * Connections Snapshot
   
   netstat -an | head

   Observation:

   Active LISTEN and ESTABLISHED connections observed.

   <img width="1016" height="242" alt="image" src="https://github.com/user-attachments/assets/5380c39e-6a82-4506-9a7e-389b2114ae20" />

   ## Mini Task: Port Probe & Interpret

   nc -zv localhost 22

   Observation:

   ubuntu@ip-172-31-42-234:~$ nc -zv localhost 22
   
   Connection to localhost (127.0.0.1) 22 port [tcp/ssh] succeeded!


   SSH port is reachable.
   
   ## If unreachable, check service status and firewall configuration.

   * First check the status of Service systemctl status <Service>
   
   * Check the logs of the service journalctl -u <Service>
   
   * Check firwall permission sudo uwf status

   ## Reflection
   
   Fastest Command for Troubleshooting
   
   ping provides the quickest indication of connectivity issues.
   
   If DNS Fails
   
   * Inspect the Application layer and DNS configuration.
   
   If HTTP 500 Appears
   
   * Inspect the Application layer and web server logs.
   
   Two Follow-up Checks
   
   * Verify service status using systemctl.
   * Check firewall rules and network logs.
  
   ## Key Learnings
   
   Learned how networking layers relate to real-world traffic.
   
   Used essential troubleshooting commands.
   
   Verified connectivity, DNS, ports, and HTTP responses. 

   



  
  
