# Day 05 – Linux Troubleshooting Runbook

## Why runbooks matters?
   It is a detailed, step-by-step guide that outlines routine procedures, troubleshooting steps, and recovery actions for managing systems and services in production in case of any critical issue happens.

   •	Reduces downtime and prevent guesswork in production.
   
   •	Helpful for junior engineers.
   
---
## Demonstrating few commands related to CPU,Memory,Disk usage and logs 
   ### Environment Basics
   #### Command: uname -a 

   ```bash
   ubuntu@ip-10-0-3-187:~$ uname -a
   Linux ip-10-0-3-187 7.0.0-1004-aws #4-Ubuntu SMP PREEMPT Mon Apr 13 13:14:24 UTC 2026 x86_64 GNU/Linux
   ubuntu@ip-10-0-3-187:~$
   ```
   #### Command: cat /etc/os-release

   ```bash
   ubuntu@ip-10-0-3-187:~$ cat /etc/os-release
   PRETTY_NAME="Ubuntu 26.04 LTS"
   NAME="Ubuntu"
   VERSION_ID="26.04"
   VERSION="26.04 (Resolute Raccoon)"
   ```
   ---
   ### Filesystem Sanity 
   #### Command: mkdir /tmp/runbook-demo

   ```bash
   ubuntu@ip-10-0-3-187:~$ mkdir /tmp/runbook-demo
   ubuntu@ip-10-0-3-187:~$ cd /tmp
   ubuntu@ip-10-0-3-187:/tmp$ ls
   runbook-demo
   ```
   Observation: Above command created a directory named "runbook-demo" under /tmp filesystem

   #### Command: cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo

   ```bash
   ubuntu@ip-10-0-3-187:~$ cd /tmp/runbook-demo/
   ubuntu@ip-10-0-3-187:/tmp/runbook-demo$ ls -lrt
   total 4
   -rw-r--r-- 1 ubuntu ubuntu 221 May 20 08:36 hosts-copy
   ubuntu@ip-10-0-3-187:/tmp/runbook-demo$
   ```
   Observation: Above command copies the contents of /etc/hosts to a file named hosts-copy and also displays if file exists. Notice that
   hosts-copy file was created automatically by linux.
   
   ---
   ### CPU / Memory
   #### Command: top 

   ```bash
    top - 09:41:15 up 8 days,  1:45,  3 users,  load average: 0.00, 0.00, 0.00
    Tasks: 133 total,   1 running, 132 sleeping,   0 stopped,   0 zombie
    %Cpu(s):  0.2 us,  0.2 sy,  0.0 ni, 99.4 id,  0.0 wa,  0.0 hi,  0.2 si,  0.2 st
    MiB Mem :    908.7 total,     65.3 free,    391.3 used,    572.5 buff/cache
    MiB Swap:      0.0 total,      0.0 free,      0.0 used.    517.4 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
    37530 ubuntu    20   0   18728   8732   6140 S   0.3   0.9   0:01.12 sshd-session
      1 root      20   0   25684  16416  10912 S   0.0   1.8   0:28.86 systemd
   ```
   Observation: The system is healthy and not showing any sign of high cpu or memory usage

   #### Command: free -m 

   ```bash
   ubuntu@ip-10-0-3-187:~$ free -m
                  total        used        free      shared  buff/cache   available
   Mem:             908         396          61           2         571         512
   Swap:              0           0           0
   ```
   ---
   ### File system and I/O usage 
   #### Command: df -h 

   ```bash
   ubuntu@ip-10-0-3-187:~$ df -h
   Filesystem       Size  Used Avail Use% Mounted on
   /dev/root        6.7G  2.7G  4.0G  41% /
   tmpfs            455M     0  455M   0% /dev/shm
   tmpfs            182M  964K  181M   1% /run
   efivarfs         128K  3.1K  120K   3% /sys/firmware/efi/efivars
   tmpfs            455M  4.0K  455M   1% /tmp
   none             1.0M     0  1.0M   0% /run/credentials/systemd-journald.service
   none             1.0M     0  1.0M   0% /run/credentials/systemd-resolved.service
   /dev/nvme0n1p13  989M   95M  828M  11% /boot
   /dev/nvme0n1p15  105M  6.3M   99M   7% /boot/efi
   ubuntu@ip-10-0-3-187:~$
   ```
   Observation: File system usage is normal 
   #### Command: sudo du -sh /var/log

   ```bash
   ubuntu@ip-10-0-3-187:~$ sudo du -sh /var/log
   33M     /var/log
   ```

   #### Command: iostat 
   ```bash
   ubuntu@ip-10-0-3-187:~$ iostat
   Linux 7.0.0-1004-aws (ip-10-0-3-187)    05/20/26        _x86_64_        (2 CPU)

   avg-cpu:  %user   %nice %system %iowait  %steal   %idle
              0.03    0.00    0.01    0.01    0.08   99.87

   Device             tps    kB_read/s    kB_wrtn/s    kB_dscd/s    kB_read    kB_wrtn    kB_dscd
   loop0             0.00         0.01         0.00         0.00       4502          0          0
   loop1             0.00         0.00         0.00         0.00        690          0          0
   loop2             0.00         0.00         0.00         0.00       1689          0          0
   loop3             0.00         0.08         0.00         0.00      54269          0          0
   loop4             0.00         0.00         0.00         0.00         10          0          0
   nvme0n1           0.40         4.27        12.85         0.00    2965884    8919690          0
   ```
   ---
   ### Network related 

   #### Command: 
   ```bash
   ubuntu@ip-10-0-3-187:~$ sudo ss -tulpn
   Netid State  Recv-Q Send-Q   Local Address:Port   Peer Address:Port Process
   udp   UNCONN 0      0            127.0.0.1:323         0.0.0.0:*     users:(("chronyd",pid=730,fd=4))
   udp   UNCONN 0      0           127.0.0.54:53          0.0.0.0:*     users:(("systemd-resolve",pid=197,fd=18))
   udp   UNCONN 0      0        127.0.0.53%lo:53          0.0.0.0:*     users:(("systemd-resolve",pid=197,fd=16))
   udp   UNCONN 0      0      10.0.3.187%ens5:68          0.0.0.0:*     users:(("systemd-network",pid=591,fd=36))
   tcp   LISTEN 0      4096        127.0.0.54:53          0.0.0.0:*     users:(("systemd-resolve",pid=197,fd=19))
   tcp   LISTEN 0      4096           0.0.0.0:22          0.0.0.0:*     users:(("sshd",pid=31697,fd=3),("systemd",pid=1,fd=166))
   tcp   LISTEN 0      128          127.0.0.1:6010        0.0.0.0:*     users:(("sshd-session",pid=37530,fd=13))
   tcp   LISTEN 0      4096     127.0.0.53%lo:53          0.0.0.0:*     users:(("systemd-resolve",pid=197,fd=17))
   ```
   Observation: Ports are active and listening properly 

   #### Command: curl -I http://localhost
   ```bash
   ubuntu@ip-10-0-3-187:~$ curl -I http://localhost
   curl: (7) Failed to connect to localhost port 80 after 0 ms: Could not connect to server
   ubuntu@ip-10-0-3-187:~$
   ```
   Observation: No web services running on port 80

   ### Logs

   #### Command : journalctl -u docker -n 50
   ```bash
   ubuntu@ip-10-0-3-187:~$ journalctl -u docker -n 50
   May 20 05:53:43 ip-10-0-3-187 systemd[1]: Starting docker.service - Docker Application Container Engine...
   May 20 05:53:44 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:53:44.187631827Z" level=info msg="Starting up"
   May 20 05:53:44 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:53:44.194845680Z" level=info msg="OTEL tracing is not confi>
   May 20 05:53:44 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:53:44.197221822Z" level=info msg="CDI directory does not ex>
   May 20 05:53:44 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:53:44.197252477Z" level=info msg="CDI directory does not ex>
   May 20 05:53:44 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:53:44.199455518Z" level=info msg="detected 127.0.0.53 names>
   May 20 05:53:44 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:53:44.362085125Z" level=info msg="Creating a containerd cli>
   May 20 05:53:44 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:53:44.382719019Z" level=info msg="Loading containers: start>
   May 20 05:53:44 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:53:44.383724155Z" level=info msg="NRI is disabled"
   May 20 05:53:44 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:53:44.383757339Z" level=info msg="Starting daemon with cont>
   May 20 05:53:44 ip-10-0-3-187 systemd[1]: Started docker.service - Docker Application Container Engine.
   May 20 05:54:56 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:54:56.650015729Z" level=info msg="image pulled" digest="sha>
   May 20 05:54:57 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:54:57.036590337Z" level=info msg="sbJoin: gwep4 ''->'57b8bf>
   May 20 05:54:57 ip-10-0-3-187 dockerd[36726]: time="2026-05-20T05:54:57.118082989Z" level=info msg="received task-delete even>
   ubuntu@ip-10-0-3-187:~$
   ```
   Observation: Docker services running correctly. No errors found in logs 

   ### Command: tail -n 50 /var/log/syslog

   ```bash
   ubuntu@ip-10-0-3-187:~$ tail -n 50 /var/log/syslog
   2026-05-20T07:20:19.715445+00:00 ip-10-0-3-187 systemd[1]: sysstat-collect.service: Deactivated successfully.
   2026-05-20T07:20:19.715797+00:00 ip-10-0-3-187 systemd[1]: Finished sysstat-collect.service - system activity accounting tool.
   2026-05-20T07:30:19.690095+00:00 ip-10-0-3-187 systemd[1]: Starting sysstat-collect.service - system activity accounting tool...
   2026-05-20T07:30:19.713002+00:00 ip-10-0-3-187 systemd[1]: sysstat-collect.service: Deactivated successfully.
   2026-05-20T07:30:19.713325+00:00 ip-10-0-3-187 systemd[1]: Finished sysstat-collect.service - system activity accounting tool.
   2026-05-20T07:36:55.049666+00:00 ip-10-0-3-187 systemd[1]: Started session-226.scope - Session 226 of User ubuntu.
   2026-05-20T07:36:55.611913+00:00 ip-10-0-3-187 kernel: audit: type=1400 audit(1779262615.610:230): apparmor="DENIED" operation="open"             class="file" profile="who" name="/usr/share/coreutils/locales/uucore/en-US.ftl" pid=37452 comm="who" requested_mask="r" denied_mask="r"           fsuid=0 ouid=0
   2026-05-20T07:36:56.591548+00:00 ip-10-0-3-187 systemd[1]: Started session-227.scope - Session 227 of User ubuntu.
   ```
   Observation: Log showing normal network and services activity
   
   ---
   ### Quick Review 
   
   •	CPU and memory usage are fine
   
   •	Disk space is within threshold
   
   •	Docker service running normally
   
   •	No critical errors in the logs
   
   •	Network ports responding correctly

   ### In worst case scenario follow below steps

   •	Check logs again
   
   •	Check CPU usage/Disk usage
   
      ```bash
      top , df -h , iostat
      ```
   
   •	Restart service

      ```bash 
      sudo systemctl restart docker
      ```
   
   •	Check if port is used by other service

      ```bash
      ss -tulpn
      ```



   
   
   


  
  

   


   






   
