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



