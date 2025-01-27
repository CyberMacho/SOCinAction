# Fortifying the Cloud: Building a SOC + Honeynet in Azure with Live Traffic Analysis  
![SOC + Honeynet in Azure](https://github.com/user-attachments/assets/74afe2e9-d2f1-466a-a31d-ce1d1c16f723)


## Overview  

In this project, I created a Security Operations Center (SOC) combined with a honeynet in Microsoft Azure. The goal was to monitor live traffic, detect malicious activity, and evaluate the effectiveness of security controls. Metrics were collected from an insecure environment, and the same metrics were analyzed after implementing security hardening measures to demonstrate the importance of robust cybersecurity practices.

## Project Objectives  

- **Honeynet Deployment:** Simulate a vulnerable environment exposed to real-world internet traffic.  
- **Data Collection:** Log and analyze key security metrics using Azure tools.  
- **Security Hardening:** Implement strong security controls to mitigate vulnerabilities and malicious activity.  
- **Impact Assessment:** Measure and compare metrics before and after applying security measures.  

## Architecture  

### Before Security Hardening  
![Architecture Diagram Before Hardening](https://github.com/user-attachments/assets/b70c53eb-380a-4cfe-8546-c0ace02e41d2)

  

In the insecure state, the environment was deliberately exposed:  
- **Virtual Machines:** Two Windows and one Linux VM with no firewall or security restrictions.  
- **Network Security Groups (NSG):** Fully open inbound and outbound traffic.  
- **Public Endpoints:** Resources were directly accessible from the internet, exposing them to potential threats.  

### After Security Hardening  
![Architecture Diagram After Hardening](https://github.com/user-attachments/assets/5a61402f-8261-4612-b4e8-daff35a8c784)



Enhanced security measures were applied:  
- **Restricted NSG Rules:** Allowed traffic only from administrative workstations.  
- **Private Endpoints:** Blocked internet access to critical resources.  
- **Built-In Firewalls:** Active on all deployed resources to enforce security policies.  

## Technology Stack  

The mini honeynet architecture in Azure is comprised of the following components:
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
  
Initially, resources were deployed with minimal security configurations, leaving them vulnerable to external access. The Virtual Machines had permissive Network Security Groups (NSGs) and firewalls, allowing unrestricted inbound and outbound traffic. Other resources were exposed to the internet through public endpoints, with no implementation of Private Endpoints for additional protection.

Security configurations were tightened by restricting Network Security Groups (NSGs) to block all traffic except from my administrative workstation. Additionally, all other resources were safeguarded using their internal firewalls and secured via Private Endpoints, ensuring limited and controlled access.

## Metrics Collection  

### Before Hardening  


During the initial 24-hour period, significant malicious activity was observed:  

| **Metric**                | **Count** |  
|---------------------------|-----------|  
| SecurityEvent             | 19,470    |  
| Syslog                    | 3,028     |  
| SecurityAlert             | 10        |  
| SecurityIncident          | 348       |  
| AzureNetworkAnalytics_CL  | 843       |  

### After Hardening  

After implementing security measures, malicious activity was drastically reduced:  

| **Metric**                | **Count** |  
|---------------------------|-----------|  
| SecurityEvent             | 8,778     |  
| Syslog                    | 25        |  
| SecurityAlert             | 0         |  
| SecurityIncident          | 0         |  
| AzureNetworkAnalytics_CL  | 0         |  

## Visual Insights  

![4](https://github.com/user-attachments/assets/b038770e-76a0-4f3e-b784-98271786d33c)
![5](https://github.com/user-attachments/assets/5018bcb9-f101-481a-8cbe-94760b9e3dbf)
![6](https://github.com/user-attachments/assets/40aee065-26ec-4e7f-bfe6-b6cd80322a3b)


### Before Hardening  
Attack maps revealed substantial malicious activity, such as:  
- Failed RDP and SMB authentication attempts on Windows VMs.  
- Unauthorized access attempts on Linux systems.  

### After Hardening  
After security controls were applied, no malicious activity was detected, confirming the effectiveness of the implemented measures.  

## Conclusion  

This project demonstrates the creation of a SOC and honeynet in Azure to capture and analyze live traffic. By applying effective security measures and leveraging tools like Microsoft Sentinel and Log Analytics, this exercise highlights the importance of proactive monitoring and robust defense strategies in securing cloud environments.  
