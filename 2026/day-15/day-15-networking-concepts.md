# Day 15 – Networking Concepts: DNS, IP, Subnets & Ports

## Task 

Understand how DNS resolves names to IPs

* Learn IP addressing (IPv4, public vs private)

* Break down CIDR notation and subnetting basics

* Know common ports and why they matter


## Task 1 - DNS: How Names Become IPs

What Happens when you type google.com in a browser?

* The browser sends a DNS query to resolve the domain name.

* DNS servers return the IP address associated with the domain.

* The browser establishes a connection to that IP address.

* The Web server responds with the requested webpage.

## Common DNS Record Types

A - Maps a domain name to an IPv4 address

AAAA - Maps a domain name to an IPv6 address

CNAME - Creates an alias for another domain

MX - Specifies mail servers for email delivery

NS - Identifies authoritative name servers

## DNS lookup command 

dig google.com 

<img width="802" height="452" alt="image" src="https://github.com/user-attachments/assets/520100ef-30e2-4558-9dcc-01b7fd946b03" />



;; ANSWER SECTION:

google.com.             251     IN      A       142.250.73.142


Identified A record : 142.250.73.142

TTL(Time To Live ) : 121 seconds

* TTL most commonly stands for Time to Live. It is a numerical value that acts as an expiration date or hop limit for data in computing, preventing information from
  looping indefinitely and causing network congestion.

## Task 2 - IP Addressing

### What is an IPv4 Address?

An IPv4 address is a 32-bit numerical identifier assigned to devices on a network. It consists of four octets separated by dots, such as 192.168.1.10

* Format: Written in "dotted-decimal" notation, split into four 8-bit numbers (octets) separated by periods.

* Example: 192.168.0.1

* Range: Each of the four octets can range from 0 to 255.

* Total Pool: Supports roughly 4.3 billion unique addresses (2³²).

### Public vs Private IP Addresses

Public IP : Globally unique and routable on the internet. Example : 8.8.8.8

Private IP : It is reserved for internet network not routable on the public internet. Example : 192.168.1.10

### Run: ip addr show — identify which of your IPs are private

<img width="1053" height="334" alt="image" src="https://github.com/user-attachments/assets/da565691-3a51-49a6-b734-c9bc109add1f" />


My system IP: 172.31.33.163/20

# Task 3 - CIDR & Subnetting

## What does 192.168 2.0/24 mean?

The first 24 bits represent the network portion of the address, while the remaining 8 bits are used for host addresses.

## Why do we need Subnet?

Subnetting divides large network in a small trafic noise and boost security

* Better network organization

* Improved security

* Efficient IP allocation

* Reduced broadcast traffic

## How many usable hosts in a /24? A /16? A /28?

/24 --> 254 usable host

/16 --> 65,534 usable host

/28 --> 14 usable host

The first address is the network address, it identifies the subnet itself not a device

The last address is the broadcast address used to send a message to all devices on that subnet

# CIDR Table

| CIDR | Subnet Mask     | Total IPs | Usable Hosts |
| ---- | --------------- | --------- | ------------ |
| /24  | 255.255.255.0   | 256       | 254          |
| /16  | 255.255.0.0     | 65,536    | 65,534       |
| /28  | 255.255.255.240 | 16        | 14           |


# Task 4: Ports – The Doors to Services

## What is a Port?

A port is a logical communication endpoint that allows multiple services to run on the same device while keeping network traffic organized.

## Common Ports


| Port  | Service |
| ----- | ------- |
| 22    | SSH     |
| 80    | HTTP    |
| 443   | HTTPS   |
| 53    | DNS     |
| 3306  | MySQL   |
| 6379  | Redis   |
| 27017 | MongoDB |


# Command used 

ss -tulpn

```bash
ubuntu@ip-172-31-33-163:~$ ss -tulpn

Netid           State            Recv-Q            Send-Q                            Local Address:Port                       Peer Address:Port           Process
udp             UNCONN           0                 0                                     127.0.0.1:323                             0.0.0.0:*
udp             UNCONN           0                 0                                    127.0.0.54:53                              0.0.0.0:*
udp             UNCONN           0                 0                                 127.0.0.53%lo:53                              0.0.0.0:*
udp             UNCONN           0                 0                            172.31.33.163%ens5:68                              0.0.0.0:*
udp             UNCONN           0                 0                                         [::1]:323                                [::]:*
tcp             LISTEN           0                 4096                                    0.0.0.0:22                              0.0.0.0:*
tcp             LISTEN           0                 4096                              127.0.0.53%lo:53                              0.0.0.0:*
tcp             LISTEN           0                 4096                                 127.0.0.54:53                              0.0.0.0:*
tcp             LISTEN           0                 4096                                       [::]:22                                 [::]:*
ubuntu@ip-172-31-33-163:~$

``` 


## Task 5 - Putting It Together

## What Happens When Running curl http://myapp.com:8080 ?

DNS resolves myapp.com into an IP address.

The system establishes a TCP connection to port 8080.

Packets are routed through the network using IP addressing.

The application responds with the requested data.

## Your App Cannot Reach Database at 10.0.1.50:3306. What Would You Check?

Verify database service is running.

Check network connectivity.

Confirm MySQL is listening on port 3306.

Review firewall and security group rules.

Validate application configuration.


## Learnings

DNS converts human-readable domain names into IP addresses.

CIDR notation helps efficiently manage and divide networks.

Ports allow multiple services to communicate over a single IP address.

Understanding networking fundamentals is essential for troubleshooting in DevOps environments.








