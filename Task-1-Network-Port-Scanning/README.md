# Task 1 - Scan Your Local Network for Open Ports

## Objective

To identify active devices, open ports, and running services on an authorized local network using Nmap.

## Tools Used

- Nmap 7.991
- Windows Command Prompt
- Wireshark (Optional)

## Network Information

- Local IPv4 Address: 192.168.1.4
- Subnet Mask: 255.255.255.0
- Network Range: 192.168.1.0/24

## 1. Host Discovery

Command used:
```bash
nmap -sn 192.168.1.0/24
Result
4 hosts were discovered as active:

| IP Address | Status |
|---|---|
| 192.168.1.1 | Host is up |
| 192.168.1.2 | Host is up |
| 192.168.1.3 | Host is up |
| 192.168.1.4 | Host is up |

## 2. TCP SYN Scan
Command used:

```bash
nmap -sS 192.168.1.1-4 -oN tcp-syn-scan.txt
### Observed Open/Filtered Ports

| IP Address | Port | State | Service |
|---|---|---|---|
| 192.168.1.1 | 53/tcp | Open | DNS |
| 192.168.1.1 | 80/tcp | Open | HTTP |
| 192.168.1.1 | 5555/tcp | Open | Unknown/Custom |
| 192.168.1.3 | 80/tcp | Open | HTTP |
| 192.168.1.4 | 135/tcp | Open | MSRPC |
| 192.168.1.4 | 139/tcp | Open | NetBIOS-SSN |
| 192.168.1.4 | 445/tcp | Open | Microsoft-DS/SMB |

Some additional ports were reported as filtered, indicating that firewall filtering may be present.

## 3. Service Detection

Command used:

```bash
nmap -sV 192.168.1.1-4 -oN service-scan.txt
Detected Services
- 192.168.1.1
  - 53/tcp - dnsmasq 2.52
  - 80/tcp - Boa HTTPd 0.94.13
  - 5555/tcp - UPnP-related service
- 192.168.1.3
  - 80/tcp - HTTP
  - 23/tcp - Telnet (filtered)
  - 8000/tcp - HTTP-alt (filtered)
- 192.168.1.4
  - 135/tcp - Microsoft Windows RPC
  - 139/tcp - NetBIOS-SSN
  - 445/tcp - Microsoft-DS/SMB
4. Security Risk Analysis
Port 23 - Telnet
Telnet is an insecure remote-access protocol because it does not provide encrypted communication. The port was detected as filtered in this scan.
Ports 139 and 445 - SMB/NetBIOS
These services are commonly used for Windows file and printer sharing. If unnecessarily exposed, they can increase the attack surface. Access should be restricted using firewall rules and network segmentation.
Port 135 - MSRPC
MSRPC is used by Windows for various remote services. Access should be restricted to trusted systems and networks.
Port 80 - HTTP
HTTP traffic is generally unencrypted. If sensitive information is handled, HTTPS should be preferred.
Port 5555
Port 5555 was detected as an open service on 192.168.1.1. The service should be identified and restricted or disabled if it is not required.
5. Conclusion
The Nmap scan identified four active hosts on the authorized local network and several open or filtered TCP ports.
The scan demonstrates how network reconnaissance can be used to identify exposed services and potential attack surfaces. Unnecessary services should be disabled and access to required services should be restricted using appropriate firewall and network security controls.
Scan Results
The sanitized Nmap output files are included in this folder:
- tcp-syn-scan-public.txt
- service-scan-public.txt
