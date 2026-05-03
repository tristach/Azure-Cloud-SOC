## Azure SOC Honeynet (Microsoft Sentinel)

<img width="348" alt="image" src="https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/923b0e01-b332-4300-ac8c-2c19fdc9f0b2">

## Overview

I built a honeynet environment using Azure resources and exposed it to the internet to simulate real-world attack conditions. Using Microsoft Sentinel, I collected logs, created detection rules, and analyzed malicious activity from live attackers.

## Technologies Used

- Microsoft Azure  
- Microsoft Sentinel (SIEM)  
- Log Analytics Workspace  
- KQL (Kusto Query Language)  
- Sysmon  
- Windows & Linux Virtual Machines  
- Network Security Groups (NSGs)  

## Key Features

- Detection of brute-force login attempts (Event ID 4625)  
- Custom KQL queries to identify suspicious IP activity  
- Incident creation and alerting in Microsoft Sentinel  
- Automation using Logic Apps for alert notifications  
- Visualization of attack data using dashboards and workbooks  
- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)

## Architecture

The honeynet environment in Azure includes:

- Virtual Network (VNet)
- Network Security Groups (NSGs)
- Windows & Linux Virtual Machines
- Log Analytics Workspace
- Microsoft Sentinel

## Security Hardening

**Before:**
- All resources exposed to the internet
- NSGs and firewalls left open
- Public endpoints enabled

**After:**
- NSGs restricted to allow only trusted access
- Built-in firewalls enabled
- Private endpoints used where possible
## Attack Maps Before Hardening / Security Controls-Russia
<img width="806" alt="image" src="https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/bae83ccd-1472-4578-8df9-e7f4c82d9ac7">

## Attack Maps Before Hardening / Security Controls-Mexico
![image](https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/13178d36-c772-44ab-b796-33d5d6a59d18)

## Attack Maps After Hardening / Security Controls
![image](https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/b2ad0fbb-87f7-4b6c-addb-1e63ba275c38)


## Syslog Example (KQL) 
<img width="883" alt="image" src="https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/e09c13c7-e54c-4ff2-ad20-c98978b2e2e3">

## Syslog Example (KQL) Expanded
<img width="429" alt="image" src="https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/6d2b00d8-700c-4ab7-80e5-b5a6106bce08">


##
<img width="514" alt="image" src="https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/d99f493f-cfce-44bf-9e00-bd3f3ca4f84d">

##
Metric                          Before     After     Reduction
-------------------------------------------------------------
Windows Security Events         5611       110       -98.0%
Linux Syslog Events             19059      344       -98.2%
Security Alerts                 6          0         -100%
Security Incidents              249        0         -100%
NSG Malicious Flows Allowed     1140       0         -100%


## Conclusion -->

In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. It is noteworthy that the number of security events and incidents were drastically reduced after the security controls were applied, demonstrating their effectiveness.

It is worth noting that if the resources within the network were heavily utilized by regular users, it is likely that more security events and alerts may have been generated within the 24-hour period following the implementation of the security controls.
