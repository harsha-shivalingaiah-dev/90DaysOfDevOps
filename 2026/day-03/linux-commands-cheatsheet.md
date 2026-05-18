# Process management

•	kill -9: Force kill a process immediately — cannot be ignored

•	ps aux: List all running processes with CPU and memory

•	top: Live interactive view of CPU and RAM usage by process

•	lsof -p: List all files and sockets opened by a process

•	vmstat 1: Report CPU, memory, IO and process stats every second

•	ps -ef: Show all processes in full format with parent PID

•	jobs: List all current background and suspended shell jobs

•	nohup cmd &: Run a command immune to hangup — survives terminal close

# File system 

•	ls -la: List all files including hidden ones with permissions 

•	find . -size +100M: Find files larger than 100MB in current directory tree

•	du -sh folder: Show total disk size consumed by a directory

•	cat /proc/mounts: Show all currently mounted filesystems from kernel

•	fdisk -l: List all disk partitions and their sizes 

•	lsblk: List all block devices including disks and partitions

•	mount /dev/sdb1 /mnt: Mount a disk partition to a directory

•	umount /mnt: Safely unmount a mounted disk partition 

•	chmod 755 file: Set owner=rwx, group=rx,others=rx permissions

# Networking

•	ping -c 4 host: Send 4 ICMP packets to test reachability and latency

•	traceroute host: Show every network hop the packet takes to destination

•	curl -v url: Verbose curl — shows full request and response details

•	wget url: Download a file from a URL to the current directory

•	ifconfig: Display all network interfaces and their IP addresses

•	netstat -tuln: List all open ports and listening services

•	host domain: Simple DNS lookup — resolves hostname to IP address

•	ssh user@host: Connect securely to a remote machine via SSH protocol

•	tcpdump -I eth0: Capture and inspect live network packets on an interface





