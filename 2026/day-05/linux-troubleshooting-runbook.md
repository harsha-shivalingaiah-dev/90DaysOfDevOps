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

   ### Network related 

   #### Command: 
   ```bash
   ubuntu@ip-10-0-3-187:~$ sudo ss -tulpn
   Netid State  Recv-Q Send-Q   Local Address:Port   Peer Address:Port Process
   udp   UNCONN 0      0            127.0.0.1:323         0.0.0.0:*     users:(("chronyd",pid=730,fd=4))
   udp   UNCONN 0      0           127.0.0.54:53          0.0.0.0:*     users:(("systemd-resolve",pid=197,fd=18))
   udp   UNCONN 0      0        127.0.0.53%lo:53          0.0.0.0:*     users:(("systemd-resolve",pid=197,fd=16))
   udp   UNCONN 0      0      10.0.3.187%ens5:68          0.0.0.0:*     users:(("systemd-network",pid=591,fd=36))

   
   
   


  
  

   


   






   
