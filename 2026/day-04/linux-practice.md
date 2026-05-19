# Day 04 - Linux Practice: Processes and Services

## Process Checks

### 1. Check running processes

```bash
ps -aux | head -n 10
```

### Observation
Displays currently running processes and resource usage.

---

### 2. Real-time system monitoring

```bash
top
```

### Observation
Shows real-time CPU and Memory usage.

---

## Service Checks

### 3. Check for SSH service status

```bash
systemctl status ssh
```

### Observation
Verified SSH service is active and running.

---

### 4. List running services

```bash
systemctl list-units --type=service --state=running
```

### Observation
Lists the active running services.

---

## Log Checks

### 5. View SSH service logs

```bash
journalctl -u ssh
```

### Observation
Displays SSH startup and service logs.

---

### 6. View recent system logs

```bash
tail -n 10 /var/log/syslog
```

### Observation
Reviewed recent system events and warnings.

---

# Mini Troubleshooting Workflow

## Scenario
cron service troubleshooting

### Step 1: Check service status for cron

```bash
systemctl status cron
```

### Step 2: Stop cron service

```bash
sudo systemctl stop cron
```

### Step 3: Check logs

```bash
journalctl -u cron | tail -n 20
```

### Step 4: Start cron service 

```bash 
sudo systemctl start cron
```

### Step 4: Verify service status

```bash

ubuntu@ip-10-0-3-187:~$ systemctl status cron
● cron.service - Regular background program processing daemon
     Loaded: loaded (/usr/lib/systemd/system/cron.service; enabled; preset: enabled)
     Active: active (running) since Tue 2026-05-19 13:46:22 UTC; 18s ago

systemctl is-active cron

ubuntu@ip-10-0-3-187:~$ systemctl is-active cron
active


```

### Result
SSH service is active and functioning properly. Verified the same from logs

---

# Key Learnings for today
•	Practiced Linux process monitoring

•	Learned service management using systemctl

•	Explored the logs using journalctl and tail command

•	Understood a basic troubleshooting workflow


