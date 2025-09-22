# nmap-task-1
Task 1: Scan Your Local Network for Open Ports

This document provides a breakdown of an Nmap scan performed on a target IP address (172.172.18.22). The purpose of the scan was to gather information about the open ports and services available on the target machine.

Overview of Commands & Results
Step 1: Check Network Interfaces

The following command was executed to gather details about the available network interfaces on the machine:
bash
ip a

Output:
bash
1: lo: mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000 link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00 inet 127.0.0.1/8 scope host lo valid_lft forever preferred_lft forever inet6 ::1/128 scope host noprefixroute valid_lft forever preferred_lft forever 
2: eth0: mtu 1500 qdisc fq_codel state DOWN group default qlen 1000 link/ether 00:2b:67:b1:c7:5e brd ff:ff:ff:ff:ff:ff 
3: wlan0: mtu 1500 qdisc noqueue state UP group default qlen 1000 link/ether d8:3b:bf:6b:01:66 brd ff:ff:ff:ff:ff:ff inet 172.20.10.13/28 brd 172.20.10.15 scope global dynamic noprefixroute wlan0 valid_lft 1841sec preferred_lft 1841sec inet6 2401:4900:631e:15e7:842d:f4b9:652a:1bdb/64 scope global noprefixroute valid_lft forever preferred_lft forever inet6 fe80::86f4:759e:eeea:cc7e/64 scope link noprefixroute valid_lft forever preferred_lft forever

From the output above:

The local loopback interface (lo) has IP 127.0.0.1.

Ethernet (eth0) is down.

Wireless (wlan0) is up with the IP address 172.20.10.13 on a /28 subnet.

Step 2: Nmap Scan Command

The following Nmap scan was run to detect open ports on the target IP 172.172.18.22:

bash
nmap -sS 172.172.18.22 -oN scan-results.html

Command Explanation:

nmap: Invokes Nmap, a powerful network scanning tool.

-sS: This option performs a SYN scan, which is one of the most popular and stealthy scan techniques.

172.172.18.22: This is the target IP address being scanned.

-oN scan-results.html: Saves the scan results in an HTML format (scan-results.html).

Scan Results:
Starting Nmap 7.95 ( https://nmap.org ) at 2025-09-22 21:39 IST
Nmap scan report for 172.172.18.22
Host is up (0.061s latency).
Not shown: 999 filtered tcp ports (no-response)
PORT   STATE SERVICE
21/tcp open  ftp

Nmap done: 1 IP address (1 host up) scanned in 15.47 seconds

Scan Summary:

The target IP 172.172.18.22 was up with a latency of 0.061 seconds.

Port 21/tcp (FTP) was found to be open.

The scan revealed that 999 ports were filtered (no response).

The scan took 15.47 seconds to complete.

Key Information:

Open Ports:

21/tcp: FTP service (File Transfer Protocol).

Filtered Ports:

999 ports did not respond, which suggests that those ports might be firewalled or blocked by the target.

Conclusion

This Nmap scan reveals that the target machine at 172.172.18.22 has port 21 open for FTP communication. All other TCP ports are either closed or filtered, indicating the target system's firewall or network configuration is blocking responses from other ports.

For more advanced scanning, you may want to consider using additional Nmap options like -p to specify a range of ports, or -sV to detect service versions.
