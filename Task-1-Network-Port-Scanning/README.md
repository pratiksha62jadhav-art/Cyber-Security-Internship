** Task 1 - Scan Your Local Network for Open Ports**

## Objective

To identify active devices, open ports, and running services on an authorized local network using Nmap.

 Tools Used

- Nmap 7.991
- Windows Command Prompt
- Wireshark (Optional)

 Network Information

- Local IPv4 Address: 192.168.1.4
- Subnet Mask: 255.255.255.0
- Network Range: 192.168.1.0/24

 Host Discovery

Command used:

```bash
nmap -sn 192.168.1.0/24
