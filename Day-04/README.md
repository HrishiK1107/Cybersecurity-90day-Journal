# Cybersecurity Internship Resources-Repository

Welcome to the Cybersecurity Resources-Repository. This repository includes a curated collection of notes, commands, and tools essential for cybersecurity professionals. It will be continuously updated over the next 90 days to ensure you have access to the most current and relevant information. Stay informed and enhance your cybersecurity expertise with these valuable resources.

## Day 3: NMAP Scanning 
This is a comprehensive guide for using Nmap, a powerful network scanning tool used for network discovery and security auditing. Below you'll find various techniques and commands to help you carry out successful Nmap scans.

#### **Syntax**: `nmap[Scan Type(s)][Options]{target specification}`

## Command-Prompts and Examples 

#### **TARGET SPECIFICATION:**
Ex: scanme.nmap.org
- 192.168.0.1
- 10.0.0-255.1-254

#### **HOST DISCOVERY:**
- `sL`: List Scan - simply list targets to scan
- `sn`: Ping Scan - disable port scan
- `Pn`: Treat all hosts as online -- skip host discovery
- `PS/PA/PU/PY`[portlist]: TCP SYN/ACK, UDP or SCTP discovery to given ports
- `PE/PP/PM`: ICMP echo, timestamp, and netmask request discovery probes
- `PO`[protocol list]: IP Protocol Ping

#### **SCAN TECHNIQUES:**
  - `sS/sT/sA/sW/sM`: TCP SYN/Connect()/ACK/Window/Maimon scans
  - `sU`: UDP Scan
  - `sN/sF/sX`: TCP Null, FIN, and Xmas scans

#### **PORT SPECIFICATION AND SCAN ORDER:**
  - `p` <port ranges>: Only scan specified ports
  - Ex: -p22; -p1-65535; -p U:53,111,137, T:21-25, 80, 139, 8080, S:9

#### **SERVICE/VERSION DETECTION:**
  - `sV`: Probe open ports to determine service/version info
  --version-intensity <level>: Set from 0 (light) to 9 (try all probes)

#### **FIREWALL/IDS EVASION AND SPOOFING:**
  - `f`; `--mtu <val>`: fragment packets (optionally w/given MTU)
  - `D` <decoy1,decoy2[,ME],...>: Cloak a scan with decoys
  - `S` <IP_Address>: Spoof source address

#### **OUTPUT:**
  - `oN/-oX/-oS/-oG`<file>: Output scan in normal, XML, s|<rIpt kIddi3,
     and Grepable format, respectively, to the given filename.
  - `oA` <basename>: Output in the three major formats at once
  - `v`: Increase verbosity level (use -vv or more for greater effect)
  - `d`: Increase debugging level (use -dd or more for greater effect)

#### **MISC:**
  - `6`: Enable IPv6 scanning
  - `A`: Enable OS detection, version detection, script scanning, and traceroute



## Topics Covered

- #### **Nmap**
**Nmap**(Network Mapper) is a free and open-source tool for network discovery and security auditing. It is widely used for network inventory, managing service upgrade schedules, and monitoring host or service uptime.

- #### Transmission Control Protocol (TCP)
TCP is a connection-oriented protocol that ensures reliable data transmission between devices over a network. It establishes a connection before data is sent and guarantees that packets are delivered in the same order they were sent.
Use: Ensures reliable delivery of HTML, images, and other resources.

- #### User Datagram Protocol (UDP)
UDP is a connectionless protocol that allows data to be sent without establishing a connection. It is faster but does not guarantee the delivery, order, or error-checking of packets.
Use: Used in video and audio streaming where speed is critical and some data loss is acceptable. 

- ####  **Recon**
**Reconnaissance** involves gathering information about a target network or system. This is the first step in ethical hacking.
Definition: Gathering preliminary data on a target.
Example: Using Nmap to identify open ports.

- ####  **OSINT**
**Open Source Intelligence (OSINT)** involves collecting data from publicly available sources to gather information on a target.
Definition: Collecting publicly available information.
Example: Using Google to find information on a target.

- ####  **IDS and IPS**
  - **IDS (Intrusion Detection System):** Monitors network traffic for suspicious activity.
  - **IPS (Intrusion Prevention System):** Monitors and takes action to prevent detected threats.

- #### **Why Not to Ping**?
Pinging a website can sometimes alert IDS/IPS systems, leading to blocking or tracking of your IP address. Using more subtle methods can avoid detection.
Reason: Alerts IDS/IPS systems.

Diagram:

![Ping vs. TCP Explanation](https://i.sstatic.net/kudkw.png)



- #### **Service Detection Flowchart** 
```
	       nmap
	 	|
	       / \
     id-service   TCP/UDP
	|	     |
     version	  state of
     deatils 	    port
	|	     |
	|	     |-open 
	|	     |-close
	|	     |-filter
	--------------
	       |
	vulnerabilites
	       |
	    exploit
```
![nmap diagram ](https://github.com/HrishiK1107/Cybersecurity-90day-Journal/assets/166363838/5aa95d93-4edb-440d-8ee3-559df44d60d4)



- ####  *Scanning*:
![Scanning](https://www.thesecuritybuddy.com/wordpress/bdr/uploads/2020/02/Nmap_20.jpg)



- #### **Wafw00f**:
Used to identify the Firewall service used by the website.

![Wafw00f](https://github.com/HrishiK1107/Cybersecurity-90day-Journal/assets/166363838/bb447463-de65-43ef-a811-e864535f04b7)


## Practical Experience:
Performed an Nmap scan for the domain keralauniversity.ac.in, you can use the syntax and commands mentioned in this repository.

```sh
sudo nmap -Pn -p21,22,53,80,81,433,800,8080 -sV -oN test.txt -vv keralauniversity.ac.in  
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-07-04 21:47 IST
NSE: Loaded 46 scripts for scanning.
Initiating Parallel DNS resolution of 1 host. at 21:47
Completed Parallel DNS resolution of 1 host. at 21:47, 0.04s elapsed
Initiating SYN Stealth Scan at 21:47
Scanning keralauniversity.ac.in (14.139.185.78) [8 ports]
Discovered open port 80/tcp on 14.139.185.78
Completed SYN Stealth Scan at 21:47, 1.94s elapsed (8 total ports)
Initiating Service scan at 21:47
Scanning 1 service on keralauniversity.ac.in (14.139.185.78)
Completed Service scan at 21:47, 6.34s elapsed (1 service on 1 host)
NSE: Script scanning 14.139.185.78.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 21:47
Completed NSE at 21:47, 22.17s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 21:47
Completed NSE at 21:47, 0.41s elapsed
Nmap scan report for keralauniversity.ac.in (14.139.185.78)
Host is up, received user-set (0.085s latency).
Scanned at 2024-07-04 21:47:23 IST for 31s

PORT     STATE    SERVICE     REASON          VERSION
21/tcp   filtered ftp         no-response
22/tcp   filtered ssh         no-response
53/tcp   filtered domain      no-response
80/tcp   open     http        syn-ack ttl 128 Apache httpd 2.4.6 ((CentOS) OpenSSL/1.0.2k-fips mod_fcgid/2.3.9 mod_wsgi/3.4 Python/2.7.5 PHP/7.2.27)
81/tcp   filtered hosts2-ns   no-response
433/tcp  filtered nnsp        no-response
800/tcp  filtered mdbs_daemon no-response
8080/tcp filtered http-proxy  no-response

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 31.59 seconds
           Raw packets sent: 16 (704B) | Rcvd: 2 (88B)
```

----
Stay tuned for daily updates with the latest cybersecurity resources.




