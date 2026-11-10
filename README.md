# Active Directory & IT Support Lab

Hands-on IT Support and Windows Server administration lab focused on Active Directory, DNS, Group Policy, file server management, PowerShell, and real-world helpdesk troubleshooting.

## Project Overview

This project simulates a small corporate Windows domain environment using Oracle VirtualBox.

The primary objective is to develop practical **IT Support, Helpdesk L1/L2, and Junior System Administrator skills** through hands-on infrastructure configuration, troubleshooting, and realistic employee support scenarios.

The project goes beyond basic Active Directory deployment by introducing deliberately simulated incidents, structured diagnostics, root cause analysis, remediation, and documented verification.

Each completed helpdesk scenario includes its own README, technical explanations, troubleshooting commands, and screenshots.

**Current progress: 6 completed helpdesk tickets.**

## Lab Environment

| Component | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Domain Controller | Windows Server 2022 |
| File Server | Windows Server 2022 Server Core |
| Client | Windows 11 Enterprise |
| Domain | corp.example.test |
| NetBIOS Name | CORM |
| Domain Controller | DC01 (IT-DC01 VM) |
| Domain Controller IP | 10.20.XX.XX/24 |
| DNS Server | 10.20.XX.XX |
| File Server | FS01 (IT-FS01 VM) |
| File Server Data Drive | Y: |
| Domain Client | CLIENT01 (IT-CLIENT01 VM) |
| Virtual Network | IT_SUPPORT_LAN |

### Infrastructure Architecture

```text
                 corp.example.test
                        |
                 IT_SUPPORT_LAN
                        |
          +-------------+-------------+
          |             |             |
        DC01          FS01        CLIENT01
          |             |             |
       AD DS         File Server    Windows 11
       DNS           SMB Shares     Domain Login
       GPO           NTFS           Troubleshooting
       Users         Y:\Shares      Mapped Drives
       Groups
```

The environment includes a dedicated Domain Controller, a separate File Server, and a domain-joined Windows workstation.

The use of separate server roles provides a more realistic corporate infrastructure and allows independent troubleshooting of authentication, networking, file sharing, and client configuration.

## Active Directory Structure

The domain contains Organizational Units representing different departments.

```text
corp.example.test
|
+-- Company
    |
    +-- IT
    +-- HR
    +-- Finance
    +-- Sales
    +-- Workstations
```

The environment includes fictional employee accounts and department-based security groups.

### Security Groups

- GG_IT
- GG_HR
- GG_Finance
- GG_Sales

These groups are used to practice identity management, access control, and administration of corporate resources.

## Completed Infrastructure Milestones

### 1. Windows Server & Active Directory Deployment

- Installed Windows Server 2022.
- Configured static IP addressing and internal networking.
- Installed Active Directory Domain Services (AD DS).
- Configured DNS.
- Created a new Active Directory forest and domain.
- Verified domain functionality using PowerShell.

### 2. Identity Administration

- Created Organizational Units (OUs).
- Created domain user accounts.
- Configured department-based security groups.
- Assigned users to appropriate groups.
- Verified Active Directory objects using PowerShell.
- Practiced user account administration.

### 3. Windows Client Integration

- Installed Windows 11.
- Configured TCP/IP and DNS for domain discovery.
- Joined CLIENT01 to corp.example.test.
- Successfully tested domain user authentication.
- Verified communication with the Domain Controller.

### 4. Group Policy Administration

- Created and applied Group Policy Objects.
- Configured department-specific restrictions.
- Verified policy processing using `gpupdate` and `gpresult`.
- Investigated Group Policy-related events using Event Viewer.
- Practiced troubleshooting GPO links and policy application.

### 5. Windows File Server Deployment

- Deployed a dedicated Windows Server 2022 Server Core machine (FS01).
- Joined FS01 to the existing Active Directory domain.
- Configured a separate NTFS data volume.
- Installed and verified File Server functionality.
- Created departmental folders.
- Configured SMB network shares.
- Assigned NTFS and SMB permissions using Active Directory security groups.
- Verified network file access from CLIENT01.

### 6. Network Drive Deployment via Group Policy

- Created a dedicated Group Policy Object for HR.
- Configured Group Policy Preferences (Drive Maps).
- Automatically mapped an SMB share to drive letter H:.
- Tested user-side GPO processing.
- Verified network drive availability after sign-in.
- Practiced troubleshooting missing mapped drives.

---

## Completed Helpdesk Tickets

Each ticket represents a simulated IT Support incident performed in the home lab.

| Ticket | Scenario | Key Skills | Status |
|---|---|---|---|
| HD-001 | Active Directory Password Reset | ADUC, PowerShell, Account Management | Completed |
| HD-002 | Account Lockout Investigation | Account Lockout Policy, Event ID 4740 | Completed |
| HD-003 | Active Directory DNS Troubleshooting | DNS, Resolve-DnsName, nltest | Completed |
| HD-004 | Group Policy Troubleshooting | GPMC, gpresult, Event Viewer | Completed |
| HD-005 | Shared Folder Access Denied | SMB, NTFS, File Server, PowerShell | Completed |
| HD-006 | Network Drive Mapping via GPO | Group Policy Preferences, Drive Maps, SMB | Completed |

### HD-001 — Active Directory Password Reset

Simulated an employee unable to access their domain account after forgetting their password.

**Key activities:**
- Verified account status using PowerShell.
- Reset the password using Active Directory Users and Computers.
- Required a password change at the next login.
- Verified successful domain authentication.

### HD-002 — Account Lockout Investigation

Investigated a domain account locked after multiple failed authentication attempts.

**Key activities:**
- Configured and verified the Account Lockout Policy.
- Reproduced an account lockout.
- Investigated Windows Security Event ID 4740.
- Unlocked the affected account.
- Verified restored authentication.

### HD-003 — Active Directory DNS Troubleshooting

Simulated a client unable to locate domain services due to an incorrect DNS configuration.

**Key activities:**
- Investigated client DNS settings.
- Tested network connectivity.
- Used `Resolve-DnsName` and `nltest`.
- Identified incorrect DNS configuration.
- Restored domain connectivity.

### HD-004 — Group Policy Troubleshooting

Investigated a departmental policy that stopped applying to a domain user.

**Key activities:**
- Examined Group Policy links and scope.
- Used `gpupdate` and `gpresult`.
- Reviewed Group Policy events.
- Identified a disabled GPO link.
- Restored policy application.

### HD-005 — Shared Folder Access Denied

Deployed a dedicated File Server and investigated a simulated access-denied incident affecting an HR employee.

**Key activities:**
- Deployed Windows Server 2022 Server Core.
- Configured SMB and NTFS permissions.
- Implemented security group-based access control.
- Reproduced an access-denied incident.
- Compared Share Permissions and NTFS Permissions.
- Identified and removed an incorrect SMB Deny entry.
- Verified restored folder access.

### HD-006 — Network Drive Mapping via GPO

Configured automated network drive mapping and investigated a missing drive after a Group Policy configuration change.

**Key activities:**
- Created a dedicated drive mapping GPO.
- Configured Group Policy Preferences.
- Mapped the HR share to H:.
- Reproduced a missing network drive.
- Verified DNS and SMB connectivity.
- Investigated `gpresult` and Event Viewer.
- Identified a disabled Drive Maps preference item.
- Restored automatic drive mapping.

---

## Troubleshooting Methodology

Each helpdesk scenario follows a structured troubleshooting workflow:

1. **Incident Identification** — Understand the reported symptoms and expected behavior.
2. **Environment Assessment** — Identify affected users, systems, and services.
3. **Initial Diagnostics** — Collect information using PowerShell, Windows tools, and logs.
4. **Root Cause Analysis** — Determine the underlying cause rather than focusing only on symptoms.
5. **Remediation** — Apply the necessary corrective action.
6. **Validation** — Confirm functionality has been restored.
7. **Documentation** — Record the investigation, results, and lessons learned.

The goal is to develop a repeatable troubleshooting approach applicable to real IT Support environments.

## Tools & Technologies

| Category | Technologies |
|---|---|
| Virtualization | Oracle VirtualBox |
| Server Administration | Windows Server 2022, Server Core |
| Identity Management | Active Directory DS, ADUC |
| Networking | TCP/IP, DNS, SMB |
| Policy Management | Group Policy, Group Policy Preferences |
| File Services | SMB Shares, NTFS Permissions |
| Troubleshooting | Event Viewer, gpresult, nltest |
| Scripting | Windows PowerShell |
| Client Administration | Windows 11 |
| Documentation | GitHub, Markdown, Screenshots |

## Skills Demonstrated

- Windows Server installation and configuration
- Active Directory Domain Services administration
- User and security group management
- Domain joining and workstation configuration
- DNS troubleshooting
- Group Policy administration
- Windows Event Viewer analysis
- Windows Server Core administration
- File Server deployment and management
- SMB and NTFS permissions troubleshooting
- Network drive mapping through Group Policy
- PowerShell-based administration
- Incident investigation and root cause analysis
- Technical documentation

---

## Upcoming Helpdesk Scenarios

The next phase focuses on more advanced, multi-step troubleshooting scenarios that better reflect real IT Support L1/L2 responsibilities.

| Ticket | Planned Scenario | Focus |
|---|---|---|
| HD-007 | File Access Failure After Department Transfer | AD Groups, NTFS, Authentication Tokens, SMB |
| HD-008 | DNS / DHCP Troubleshooting | IP Configuration, DNS, DHCP |
| HD-009 | Windows Update Failure Investigation | Update Services, Logs, Remediation |
| HD-010 | Remote Desktop Connection Failure | RDP, Firewall, Permissions |
| HD-011 | PowerShell User Provisioning | Automation, AD Administration |
| HD-012 | Employee Onboarding / Offboarding | User Lifecycle, Access Management |
| HD-013 | Windows Services Troubleshooting | Services, Dependencies, Event Viewer |
| HD-014 | Printer Deployment and Troubleshooting | Windows Print Services, GPO |

Future scenarios will place greater emphasis on independent diagnosis, interpreting evidence, identifying multiple potential causes, and verifying resolutions.

## Project Status

**Status: Active Development**

The core Active Directory infrastructure is operational and has been expanded with a dedicated File Server and Group Policy-based network drive deployment.

**Completed:**
- Active Directory infrastructure deployment
- Domain client integration
- Departmental OU and security group configuration
- Group Policy administration
- File Server deployment
- SMB and NTFS access control
- Automatic network drive mapping
- Six documented helpdesk troubleshooting scenarios

**Next objective:** HD-007 — File Access Failure After Department Transfer.

## Disclaimer

This project was developed in an isolated home laboratory using virtual machines and fictional employee accounts.

All helpdesk incidents were intentionally simulated for educational purposes.

The project documents hands-on laboratory experience and does not represent production administration or professional employment.

---

**Author:** [NikoBialkow](https://github.com/NikoBialkow)

**Career Focus:** IT Support | Helpdesk L1/L2 | Junior System Administrator
