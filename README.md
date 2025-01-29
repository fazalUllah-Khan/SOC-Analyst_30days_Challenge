# SOC-Analyst_30days_Challenge
Build an end to end SOC Analyst ennvironment

![SOC Analyst Badge](https://img.shields.io/badge/SOC_Analyst-PROGRESSING-blue)

# Content
- SOC Analysts LAB Architure diagam
- introduction to ELK
- How to setup ELK
- ingesting logs such as sysmon
- introduction to Brute Forece Attacks
- How to setup SSH and RDP servers
- Create alerts and dashboards
- Introduction to Command & Control (C&C)
- How to setup your own C2 Server (Mythic)
- Attack our public Server
- Introduction to ticketing system
- How to setup and integrate ticketing System
- Go over how to investigate Alerts (High Level)

# Architecture Diagram 

<img width="761" alt="image" src="https://github.com/user-attachments/assets/5a5848ce-b074-454d-adab-ba6781fc3fd6" />

# 1. SOC Analyst:
The SOC Analyst is at the core of this architecture. The analyst is responsible for monitoring the network and reviewing alerts and logs generated by various services.
The analyst accesses Elastic & Kibana through a web GUI, which provides an interface for analyzing security data, such as logs and events, visualizing them in dashboards, and setting alerts for suspicious activity.
# 2. AWS Cloud:
The architecture is hosted within AWS. AWS houses the main components of the infrastructure, and everything is connected to the **Internet Gateway (Internet GW)** for communication with external systems.
**VPC (Virtual Private Cloud):** The entire setup is isolated within a VPC with a private network defined by the range 172.31.0.0/24. This ensures that only authorized communication can take place within the network.
# 3. Elastic & Kibana:
These services run within the VPC. Elastic is used for storing and searching security-related logs, while Kibana provides an interactive interface to visualize this data.
Elastic and Kibana are connected to Ticketing Server and Fleet Server to send alerts and logs. The Managed Agents deployed on the servers forward logs to Elastic for analysis.
# 4. Ticketing Server:
This server is responsible for managing security incidents. Once Elastic & Kibana detects an anomaly or a security breach, it creates an alert. These alerts are sent to the Ticketing Server, where they are logged and managed for further investigation.
The SOC Analyst reviews these tickets, investigates the incidents, and takes necessary actions.
# 5. Managed Servers:
The architecture includes various servers in the private network:

  **Windows Server (RDP enabled):** A Windows-based server with RDP (Remote Desktop Protocol) enabled. It is used for administrative purposes and manages workloads that require a Windows environment.
  
  **Fleet Server:** A server that coordinates and manages agents across the network, forwarding logs to Elastic for analysis.
  
  **Ubuntu Server (SSH Enabled):** A server running Ubuntu Linux, with SSH (Secure Shell) enabled, allowing remote management and command execution for security tasks.
  
# 6. C2 Server (Mythic):
The C2 Server (Command and Control server) uses the Mythic framework. This is the attacker's server (likely a malicious entity) that communicates with compromised systems within the network.
This is a critical part of the attack flow, where malicious instructions are sent to other systems. The C2 Server communicates with the attacker's Kali Linux machine (visible on the right side of the diagram), which likely initiates and orchestrates the attack.
# 7. Attacker’s Kali Linux:
Kali Linux is used by the attacker for penetration testing or malicious activities. The attacker interacts with the C2 Server and exploits any vulnerabilities in the managed servers (Windows, Ubuntu, etc.).
# 8. Flow of Logs and Alerts:
Logs generated from managed agents on the servers are forwarded to Elastic for storage and analysis. The logs contain information about any anomalous behavior, which may indicate a breach or suspicious activity.
The Elastic & Kibana setup continuously analyzes these logs and triggers alerts. If a potential issue is found, the system raises a ticket on the Ticketing Server, which can be reviewed and acted upon by the SOC Analyst.
# 9. Key Communication Paths:
**SOC Analyst to Elastic/Kibana:** The SOC Analyst connects to Elastic & Kibana via a Web GUI for real-time monitoring and investigation.

**Managed Servers to Elastic:** Managed servers (Windows Server, Fleet Server, and Ubuntu Server) forward logs via agents to Elastic for real-time monitoring.

**Attacker to C2 Server:** The attacker sends commands to the C2 Server, which may then communicate with the compromised systems.

# 10. Security and Network:
The network is secured using SSH and RDP protocols, with each server having access restrictions to ensure that only authorized users can access them. Logs are forwarded for analysis to detect and respond to any malicious activity.



# References: 
https://www.youtube.com/@MyDFIR

RECOMMEND COURSES FOR BEGINNERS:

Coursera Google Cybersecurity Program
Affiliate Link - https://imp.i384100.net/mydfir

Microsoft Cybersecurity Analyst Professional Certificate
Affiliate Link - https://imp.i384100.net/mydfir-MS

Coursera Google IT Support Professional Certificate
Affiliate Link - https://imp.i384100.net/mydfir-IT
