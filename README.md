
# Active Directory & IT Support Lab

Hands-on IT Support lab focused on Windows Server 2022, Active Directory administration, DNS, Group Policy, and Windows client troubleshooting.

## Project Overview

This project simulates a small corporate Windows domain environment using Oracle VirtualBox.

The primary objective is to develop practical IT Support and system administration skills through hands-on configuration, troubleshooting, and realistic helpdesk scenarios.

## Lab Environment

| Component | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Domain Controller | Windows Server 2022 |
| Client | Windows 11 Pro |
| Domain | corp.example.test |
| NetBIOS Name | CORM |
| Domain Controller Hostname | IT-DC01 |
| Domain Controller IP | 10.20.XX.XX/24 |
| DNS Server | 10.20.XX.XX |
| Virtual Network | IT_SUPPORT_LAN |

## Completed Milestones

### 1. Windows Server & Active Directory
- Installed Windows Server 2022.
- Configured static IP addressing.
- Installed Active Directory Domain Services (AD DS).
- Created a new Active Directory forest and domain.

### 2. Identity Administration
- Created Organizational Units (OUs).
- Created domain user accounts.
- Configured security groups.
- Verified Active Directory objects using PowerShell.

### 3. Windows Client Integration
- Installed Windows 11 Pro.
- Configured DNS for domain discovery.
- Joined CLIENT01 to corp.example.test.
- Successfully tested domain user authentication.

### 4. Group Policy
- Created and applied an initial Group Policy Object.
- Verified successful policy application on CLIENT01.

## Planned Helpdesk Scenarios

- Password resets and account unlocks.
- User onboarding and offboarding.
- DNS resolution troubleshooting.
- Group Policy troubleshooting using gpresult.
- Domain connectivity and authentication issues.
- Basic PowerShell administration tasks.

## Skills Demonstrated

Active Directory Domain Services, Windows Server, DNS, Group Policy, Windows client administration, PowerShell, VirtualBox, and technical troubleshooting.

## Project Status

**Status: Active Development**

Core Active Directory infrastructure is operational. The next phase focuses on practical helpdesk tickets and troubleshooting documentation.
