# Visualized-Cyber-Defense-Center

This project is designed to implement a comprehensive SOC setup, providing an opportunity to explore and experiment with modern SOC architecture. It leverages open-source components available at the time of the first commit, offering a robust foundation for security analysis and operations.


# 📑Index:
 - [Architecture Diagram](#Architecture-Diagram)
 - [Components used in this Project](#Components)
 - [Installation Requirements](#Installation-Requirements)
 - [Installation Guide First Phase](https://github.com/archanchoudhury/SOC-OpenSource/blob/main/installation/install1.md)
 - [Installation Guide Second Phase](https://github.com/archanchoudhury/SOC-OpenSource/blob/main/installation/install2.md)
 - [Installation Guide Beats Agent](https://github.com/archanchoudhury/SOC-OpenSource/blob/main/installation/beats.md)
 - [Shuffle Automation Install Guide](https://github.com/archanchoudhury/SOC-OpenSource/blob/main/installation/Shuffle-install.md)
 - [Integration Guide First Phase](https://github.com/archanchoudhury/SOC-OpenSource/blob/main/integration/integration.md)
 - [Shuffle Workflow Implementation](#Shuffle-Workflow-Implementation)
 - [Elastic EDR Implementation](#EDR-Implementation)
 - [Contributing](#Contributing)
 - [Support](#Support)

This Projects serves below usecases:
 - **Centralized Data Collection** Aggregate logs from various sources into a single system.
 - **Data Normalization & Parsing** Structure data for consistency and ease of analysis.
 - **Visualize Data** Use Kibana to generate insights into security threats.
 - **Security Analytics & Visualization** Use Kibana to generate insights into security threats.
 - **Incident & Case Management** Automate case creation from security alerts.
 - **Threat Hunting & Automation** Threat Hunting & Automation
 - **Scalable Observable Analysis**Automate analysis of observables at scale by querying a single tool instead of multiple systems.
 - **Active Threat Response & Collaboration** Enable real-time interaction between security teams and stakeholders.
 - **Threat Intelligence Integration** Enrich data feeds with Open Source Threat Intelligence platforms to enhance detection and response capabilities.

 
# ☸Architecture-Diagram(Ongoing):
<p align="center"> <img src="images/simpler-soc.png"> </p>


# ☸Components(First Phase of Implementation):
All of the components used in this projects are Open Source.
 - **TheHive**: TheHive is a scalable 3-in-1 open source Security Incident Response Platform designed to support SOCs, CSIRTs, CERTs, and security teams in investigating and responding to incidents.
    - Official GitRepo **[HERE](https://github.com/TheHive-Project/TheHive)**
 - **Cortex**: An open-source tool by TheHive Project for analyzing observables such as IP addresses, domain names, and hashes at scale via a Web interface or REST API.
    - Official GitRepo of Cortex is **[HERE](https://github.com/TheHive-Project/Cortex)**
 - **MISP**: A threat intelligence platform for sharing, storing, and analyzing security incidents and malware indicators.
   - Official GitRepo of MISP is **[HERE](https://github.com/MISP/MISP)**
- **Wazuh**: Wazuh is an open-source security monitoring solution for host-based intrusion detection, log analysis, and threat intelligence.
   - Official GitRepo of Wazuh is **[HERE](https://wazuh.com/)**


# ☸Additional Components(Second Phase of Implementation):
 - **Filebeat**:Filebeat is a lightweight shipper for forwarding and centralizing log data.
 - **Company Ticketing System**: An integrated system for tracking and managing security incidents efficiently.
 

# 🔽Installation-Requirements: 
We have deployed this project in a VM-based environment. You can follow the same setup or choose an alternative platform based on your infrastructure requirements.
## ☁VVirtual Machine (VM) Specifications:
Below are the recommended VM configurations for each component:
- MISP - Ubuntu 20 - t3.micro (Lightweight instance for threat intelligence sharing)
- Cortex - Ubuntu 20 - t3a.medium (Can also run on t2.medium)
- TheHive - Ubuntu 20 - t2.medium (Optimized for incident response and case management)
- Wazuh - Ubuntu 20 - t2.medium (Security monitoring and log analysis)
- Filebeat - Ubuntu 20 - t2.micro (Log shipper for data collection)
- Company Ticketing System - Ubuntu 20 - t2.micro (For tracking and managing security incidents)
## 🌏Network Rules:
| Ports | Allowed IPs | Purpose |
| --- | --- | --- |
| 22 | Your IP | SSH access to VMs |
| 443 | Your IP | Accessing MISP UI via browser|
| 9200 | Your IP | Accessing ElasticSearch|
| 5601 | Your IP | Accessing Kibana UI
| 9001 | Your IP | Accessing Cortex UI|
| 9000 | Your IP | Accessing TheHive UI|
| All TCP | Cortex VM IP | Accssing inbound API|
| All TCP | MISP VM IP | Accssing inbound API|
| All TCP | TheHive VM IP | Accssing inbound API|

# 🤝Contributing
We welcome your contributions. Please feel free to fork the code, play with it, make some patches and send us pull requests. 

# 🔼Enhancements:
 - As per the architecture document and Components mentioned we will keep on updating this repo with the staged implementation.
 - All of the required staged implemtation will be added in the Index page, so you can access them easily from there.

