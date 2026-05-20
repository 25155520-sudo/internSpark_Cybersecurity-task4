Cybersecurity Incident Simulation and Analysis Report
Project Overview:
This project simulates a small cybersecurity incident on a Windows system and performs forensic analysis using PowerShell history, Windows Event Viewer logs, running processes, active network connections, and authentication events.
The investigation focused on identifying suspicious activities, possible Indicators of Compromise (IOCs), and documenting containment and response actions based strictly on collected system evidence.

Goal:
Simulate a small cybersecurity incident and perform basic forensic analysis using:
Windows Event Logs
PowerShell activity
Running services and processes
Network connections
Authentication events

Requirements:
Analyze suspicious log activity
Identify possible Indicators of Compromise (IOCs)
Review PowerShell history and encoded commands
Analyze failed authentication attempts
Inspect active processes and services
Review active network connections
Document containment and response actions

Tools & Utilities Used:
Tool / Utility	               Purpose
Windows PowerShell	           Command execution and history analysis
Event Viewer (eventvwr.msc)	   Security log investigation
tasklist	                     Process enumeration
netstat -ano	                 Network connection analysis
services.msc	                 Service inspection
ipconfig	                     Network configuration review

Target System Information:
Parameter	        Value
Hostname	        BT0959
Username	        KIIT
Operating System	Windows
IPv4 Address	    192.168.31.49
Default Gateway	  192.168.31.1

Incident Scenario:
The simulated incident included:
Failed login attempts
PowerShell reconnaissance commands
Encoded PowerShell execution
Process and service enumeration
Network activity inspection
Windows Event Viewer analysis
The goal was to simulate attacker-like behavior and perform forensic investigation.

Evidence Collection:
1. PowerShell History Analysis
Command Used
Get-History
Collected Commands:
whoami
ipconfig
tasklist
net user
powershell -EncodedCommand ZQBjAGgAbwAgACIASABhAGMAawBlAGQAIgA=

2. Encoded PowerShell Execution
Observed Command:
powershell -EncodedCommand ZQBjAGgAbwAgACIASABhAGMAawBlAGQAIgA=
Decoded Content:
echo "Hacked"
Analysis:
Encoded PowerShell commands are commonly used to:
Obfuscate malicious activity
Bypass monitoring solutions
Hide attacker actions
Reconnaissance Activity:
Commands Observed:
Command	       Purpose
whoami	       Identify current user
ipconfig	     Collect network information
tasklist	     Enumerate running processes
net user	     Enumerate user accounts

Analysis:
These commands are commonly associated with attacker reconnaissance during early-stage compromise activity.

Failed Login Attempt Analysis:
Event Source:
Windows Security Logs
Event ID:
4625
Important Event Details:
Field                   Value
Event ID	              4625
Target Username	        KIIT
Status Code	            0xc000006d
SubStatus Code	        0xc000006a
Logon Type	            2
Source IP Address       127.0.0.1
Process Name	          C:\Windows\System32\svchost.exe
Authentication Package	Negotiate

Event Interpretation:
Status Code:
0xc000006d
Meaning:
Authentication failure
SubStatus Code:
0xc000006a
Meaning:
Incorrect password
Logon Type:
2
Meaning:
Interactive local login

Analysis:
The failed authentication originated locally from the system itself using an incorrect password.
Possible implications include:
Credential guessing attempts
Unauthorized login attempts
Brute-force behavior simulation

Running Process Analysis:
Command Used:
tasklist
Interesting Processes Identified:
Process	                    Observation
powershell.exe	            Multiple PowerShell sessions
openvpnserv.exe	            VPN service active
Cloudflare WARP.exe	        Tunnel/VPN application
chrome.exe	                Multiple browser processes
msedgewebview2.exe	        Numerous web components
oracle.exe	                Database-related process
tmlaridae.exe	              Suspicious/unverified process
Suspicious Process:
Process Name:
tmlaridae.exe
Analysis:
The process name appears unusual and should be verified against trusted software inventories to determine whether it represents:
Malware
Persistence mechanism
Unauthorized software

Network Connection Analysis:
Command Used:
netstat -ano
Active Listening Ports:
Port	          Service
135	            RPC
445	            SMB/File Sharing
5040	          Windows Services
59999	          Application Service
VPN Activity Observed:
Port	      Purpose
UDP 500	    IPsec
UDP 4500	  NAT Traversal/IPsec
Associated applications:
OpenVPN
Cloudflare WARP
Suspicious Connection States:
State	      Observation
CLOSE_WAIT	Improperly terminated sessions
FIN_WAIT_2	Hanging TCP sessions
External Connections Identified:
Connections were observed to infrastructure associated with:
Google
Cloudflare
Microsoft
Facebook
Epic Games

Services Analysis:
Tool Used:
services.msc
Security Services Observed:
Service	                 Status
Windows Defender	       Running
Apex One NT Framework	   Running
Trend Micro Components	 Running
OpenVPN Services	       Running
Analysis:
Security and antivirus services were active during investigation, reducing the likelihood of successful malware persistence.

Event Viewer Investigation:
Tool Used:
eventvwr.msc
Logs Reviewed:
Security Logs
Administrative Events
PowerShell Logs
Windows Logs
Important Event IDs:
Event ID	Description
4624	    Successful login
4625	    Failed login
4688	    Process creation

Indicators of Compromise (IOCs):
IOC Type	                        Indicator
Encoded PowerShell	              powershell -EncodedCommand
Failed Authentication	            Event ID 4625
Incorrect Password	              0xc000006a
Reconnaissance Commands	          whoami, tasklist, net user
Suspicious Process	              tmlaridae.exe
VPN Activity	                    OpenVPN and WARP
Unusual Connections	              CLOSE_WAIT and FIN_WAIT_2

Containment & Response Actions:
Step 1 — Log Investigation:
Reviewed:
PowerShell history
Security logs
Running processes
Active services
Step 2 — Authentication Monitoring:
Investigated:
Failed login attempts
Authentication events
Security log entries
Step 3 — Process Verification:
Reviewed suspicious processes for potential malware indicators.
Step 4 — Network Inspection:
Analyzed:
Active TCP connections
UDP connections
Listening ports
VPN activity
Step 5 — Security Validation:
Verified antivirus and endpoint protection services were operational.

Recommendations:
Enable account lockout policies
Monitor repeated Event ID 4625 occurrences
Restrict PowerShell encoded command execution
Investigate suspicious processes such as tmlaridae.exe
Review active network connections regularly
Enable enhanced PowerShell logging
Conduct regular endpoint security scans
Restrict unnecessary open ports

Deliverables:
Incident Report (PDF/DOC)
List of detected anomalies
IOC summary
Forensic evidence documentation

Final Conclusion:
The simulated investigation successfully demonstrated common attacker behaviors including:
Failed authentication attempts
System reconnaissance
Encoded PowerShell execution
Network enumeration
Although no confirmed malware compromise was identified, the activities observed resemble tactics commonly used during early attack stages.
The investigation highlights the importance of:
Continuous monitoring
Log analysis
Endpoint protection
Network visibility
Security event correlation
in detecting and responding to suspicious system activity.
