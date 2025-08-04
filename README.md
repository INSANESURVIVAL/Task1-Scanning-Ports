📌 Objective
To perform a port scan using Nmap to identify open ports and services running on devices in the local network, and evaluate potential security risks.
________________________________________
🧰 Tools Used
•	Nmap v7.97
•	OS: [Specify your OS, e.g., Windows 10 / Ubuntu 22.04]
________________________________________
🌐 Network Range
Scanned subnet: 192.168.1.0/24
Command used:
nmap -sS 192.168.1.0/24 -oN scan_results.txt
________________________________________
📋 Scan Results Summary
📍 192.168.1.1 (TP-Link Router)
MAC: 1C:61:B4:93:F7:92
Host is up (0.0013s latency)
Port	State	Service	Description
22/tcp	open	SSH	Secure remote login (typically for admin access)
53/tcp	open	Domain	DNS service (can be used for DNS spoofing if misconfigured)
80/tcp	open	HTTP	Web admin interface
1900/tcp	open	UPNP	Universal Plug and Play (can be risky if exposed)
Risk Analysis:
•	UPnP (1900) is often exploited if not secured.
•	Web admin interfaces should require strong credentials and not be exposed externally.
________________________________________
📍 192.168.1.105 (Windows Host or VM)
Host is up (0.00079s latency)
Port	State	Service	Description
135/tcp	open	MSRPC	Windows Remote Procedure Call
139/tcp	open	NetBIOS-SSN	Windows file sharing
445/tcp	open	Microsoft-DS	SMB – vulnerable in past to WannaCry
902/tcp	open	ISS RealSecure	Used by VMware or security software
912/tcp	open	Apex Mesh	May relate to distributed applications
2179/tcp	open	VMRDP	Remote Desktop for VMs
5357/tcp	open	WSDAPI	Web Services for Devices (Windows)
Risk Analysis:
•	SMB (445) and NetBIOS (139) should be firewalled if not needed, as they’re common malware targets.
•	RDP for VMs (2179) should be access-controlled or VPN-restricted.
•	Port 902 & 912: May indicate active virtualization or security services – review for exposure.
________________________________________
⚠️ Key Observations & Risks
•	SMB and RDP ports are attractive attack vectors if exposed outside local network.
•	Router admin interface on HTTP is potentially insecure (should be on HTTPS with authentication).
•	UPnP is often misconfigured and used in internal attacks or malware propagation.
________________________________________
📎 Files in Repository
port-scan-nmap/
├── scan_results.txt
├── README.md
├── screenshots/            # optional
│   └── nmap-output.png     # optional
________________________________________
✅ Conclusion
This exercise helped identify services running on local devices and evaluate potential attack surfaces. It emphasizes the importance of port hygiene, firewalls, and minimal service exposure for good network security.
