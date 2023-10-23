# Azure cloud SOC

<img width="348" alt="image" src="https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/923b0e01-b332-4300-ac8c-2c19fdc9f0b2">


## Introduction

We build a mini honeynet in Azure, ingested log sources from various resources into Log Analytics workspace, which is then used by Microsoft Sentinel to build attack maps, trigger alerts, and create incidents. We measured some security metrics in the insecure environment for 24 hours, hardended the environemt by adding basic security controls, then measured again 24 hours later.  Systems used are as follows:  

- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)

The architecture of the mini honeynet in Azure are as follows:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel

For the "BEFORE" metrics, all resources were originally deployed, exposed to the internet. The Virtual Machines had both their Network Security Groups and built-in firewalls wide open, and all other resources are deployed with public endpoints visible to the Internet; aka, no use for Private Endpoints.

For the "AFTER" metrics, Network Security Groups were hardened by blocking ALL traffic with the exception of my admin workstation, and all other resources were protected by their built-in firewalls as well as Private Endpoint

## Attack Maps Before Hardening / Security Controls-Russia
<img width="806" alt="image" src="https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/bae83ccd-1472-4578-8df9-e7f4c82d9ac7">

## Attack Maps Before Hardening / Security Controls-Mixico
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
<img width="508" alt="image" src="https://github.com/tristach/Azure-Cloud-SOC/assets/5705748/ae3aa4d4-0f07-4a88-838c-7da8442b51c7">



## Conclusion -->

In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. It is noteworthy that the number of security events and incidents were drastically reduced after the security controls were applied, demonstrating their effectiveness.

It is worth noting that if the resources within the network were heavily utilized by regular users, it is likely that more security events and alerts may have been generated within the 24-hour period following the implementation of the security controls.
