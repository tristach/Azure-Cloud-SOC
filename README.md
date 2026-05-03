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
- 
## Attack Maps Before Hardening – Linux (Syslog / SSH)
<img width="577" height="299" alt="image" src="https://github.com/user-attachments/assets/c387e281-5c35-43dc-be41-91e845da2c3a" />

## Attack Maps After Hardening – Linux (Syslog / SSH)
<img width="493" height="298" alt="image" src="https://github.com/user-attachments/assets/11fb724c-8cd7-4069-a665-f164a28d7fa7" />

<br>

---

<br>

## Attack Maps Before Hardening – Windows (Security Events)
<img width="679" height="328" alt="image" src="https://github.com/user-attachments/assets/3d74b936-1c94-44a6-bfa1-23709c034672" />

## Attack Maps After Hardening – Windows (Security Events)
<img width="629" height="329" alt="image" src="https://github.com/user-attachments/assets/76fb7184-05cf-4e1f-a35c-a9eeccc88fad" />


## KQL Query – Linux SSH Authentication Failures
<img width="883" alt="image" src="https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/e09c13c7-e54c-4ff2-ad20-c98978b2e2e3">

## Expanded Results – Linux SSH Logs
<img width="429" alt="image" src="https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/6d2b00d8-700c-4ab7-80e5-b5a6106bce08">

## Results – 24 Hour Before vs After Comparison

| Metric | Before | After | Reduction |
|--------|--------|-------|----------|
| Windows Security Events | 5611 | 110 | -98.0% |
| Linux Syslog Events | 19059 | 344 | -98.2% |
| Security Alerts | 6 | 0 | -100% |
| Security Incidents | 249 | 0 | -100% |
| NSG Malicious Flows Allowed | 1140 | 0 | -100% |

**Note:** Metrics were collected over identical 24-hour periods. Reductions reflect restricted network access and applied security controls, which significantly reduced observable malicious activity.

## Conclusion

This project demonstrates how exposing cloud resources to the public internet results in significant malicious activity, including authentication attempts and automated attacks.

After applying basic security controls such as network restrictions and access hardening, observable attack activity was reduced by over 98% across all monitored data sources.

These results highlight the importance of minimizing attack surface and enforcing access controls in cloud environments.

