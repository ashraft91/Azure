# Secure Hub-and-Spoke Network Architecture on Azure

![Build Status](https://img.shields.io/badge/build-passing-brightgreen) ![Bicep](https://img.shields.io/badge/IaC-Bicep-blue) ![Azure](https://img.shields.io/badge/Cloud-Azure-blue)

## Project Overview
This repository contains Infrastructure as Code (IaC) templates using **Azure Bicep** to automatically provision a secure, enterprise-grade Hub-and-Spoke network topology in Microsoft Azure. 

This architecture isolates workloads while maintaining centralized control over network traffic, security, and identity—aligning with Microsoft's Cloud Adoption Framework (CAF) best practices.



## Architecture Details
The deployment provisions the following resources:
* **Hub Virtual Network:** Acts as the central point of connectivity for your cross-premises network.
  * *Azure Firewall:* Inspects and filters all East-West and North-South traffic.
  * *Bastion Host:* Provides secure, seamless RDP/SSH connectivity to VMs directly from the Azure portal.
* **Spoke Virtual Networks:** Used to isolate distinct workloads (e.g., Production, Development).
  * VNet Peering configured between the Hub and Spokes.
  * User-Defined Routes (UDRs) forcing spoke traffic through the central Azure Firewall.
* **Network Security Groups (NSGs):** Applied to all subnets for granular micro-segmentation.

## Prerequisites
* An active [Azure Subscription](https://azure.microsoft.com/)
* [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) installed locally (version 2.20.0 or later)
* [Bicep CLI](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/install) installed

## Deployment Instructions

**1. Clone the repository:**
```bash
git clone [https://github.com/yourusername/azure-secure-hub-spoke-bicep.git](https://github.com/yourusername/azure-secure-hub-spoke-bicep.git)
cd azure-secure-hub-spoke-bicep
