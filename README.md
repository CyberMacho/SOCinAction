# Fortifying the Cloud: Building a SOC + Honeynet in Azure with Live Traffic Analysis  
![SOC + Honeynet in Azure](<insert-link-here>)  

## Overview  

In this project, I created a Security Operations Center (SOC) combined with a honeynet in Microsoft Azure. The goal was to monitor live traffic, detect malicious activity, and evaluate the effectiveness of security controls. Metrics were collected from an insecure environment, and the same metrics were analyzed after implementing security hardening measures to demonstrate the importance of robust cybersecurity practices.

## Project Objectives  

- **Honeynet Deployment:** Simulate a vulnerable environment exposed to real-world internet traffic.  
- **Data Collection:** Log and analyze key security metrics using Azure tools.  
- **Security Hardening:** Implement strong security controls to mitigate vulnerabilities and malicious activity.  
- **Impact Assessment:** Measure and compare metrics before and after applying security measures.  

## Architecture  

### Before Security Hardening  
![Architecture Diagram Before Hardening](<insert-link-here>)  

In the insecure state, the environment was deliberately exposed:  
- **Virtual Machines:** Two Windows and one Linux VM with no firewall or security restrictions.  
- **Network Security Groups (NSG):** Fully open inbound and outbound traffic.  
- **Public Endpoints:** Resources were directly accessible from the internet, exposing them to potential threats.  

### After Security Hardening  
![Architecture Diagram After Hardening](<insert-link-here>)  

Enhanced security measures were applied:  
- **Restricted NSG Rules:** Allowed traffic only from administrative workstations.  
- **Private Endpoints:** Blocked internet access to critical resources.  
- **Built-In Firewalls:** Active on all deployed resources to enforce security policies.  

## Technology Stack  

- **Microsoft Azure:**  
  - Virtual Network (VNet)  
  - Network Security Group (NSG)  
  - Log Analytics Workspace  
  - Microsoft Sentinel  
- **Security Monitoring Tools:**  
  - Windows Event Logs  
  - Linux Syslogs  
  - Azure Network Analytics  
  - Azure Key Vault  

## Metrics Collection  

### Before Hardening  
![Metrics Before Hardening](<insert-link-here>)  

During the initial 24-hour period, significant malicious activity was observed:  

| **Metric**                | **Count** |  
|---------------------------|-----------|  
| SecurityEvent             | 19,470    |  
| Syslog                    | 3,028     |  
| SecurityAlert             | 10        |  
| SecurityIncident          | 348       |  
| AzureNetworkAnalytics_CL  | 843       |  

### After Hardening  
![Metrics After Hardening](<insert-link-here>)  

After implementing security measures, malicious activity was drastically reduced:  

| **Metric**                | **Count** |  
|---------------------------|-----------|  
| SecurityEvent             | 8,778     |  
| Syslog                    | 25        |  
| SecurityAlert             | 0         |  
| SecurityIncident          | 0         |  
| AzureNetworkAnalytics_CL  | 0         |  

## Visual Insights  

### Before Hardening  
Attack maps revealed substantial malicious activity, such as:  
- Failed RDP and SMB authentication attempts on Windows VMs.  
- Unauthorized access attempts on Linux systems.  

### After Hardening  
After security controls were applied, no malicious activity was detected, confirming the effectiveness of the implemented measures.  

## Conclusion  

This project demonstrates the creation of a SOC and honeynet in Azure to capture and analyze live traffic. By applying effective security measures and leveraging tools like Microsoft Sentinel and Log Analytics, this exercise highlights the importance of proactive monitoring and robust defense strategies in securing cloud environments.  
