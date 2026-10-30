
# Active Directory Lab Architecture

## Overview

This lab simulates a small corporate Active Directory
environment for IT Support and troubleshooting practice.

## Infrastructure

- Hypervisor: Oracle VirtualBox
- Network: IT_SUPPORT_LAN
- Domain: corp.example.test
- NetBIOS: CORM

### Domain Controller — IT-DC01

- Operating System: Windows Server 2022
- Static IPv4: 10.20.XX.XX/24
- DNS: 10.20.XX.XX
- Roles: Active Directory Domain Services, DNS

### Workstation — CLIENT01

- Operating System: Windows 11 Pro
- Joined domain: corp.example.test
- DNS Server: 10.20.XX.XX
- Network: IT_SUPPORT_LAN

## Network Design

The domain controller and client communicate over
an isolated VirtualBox internal network.

The domain controller provides Active Directory
authentication, DNS resolution, and Group Policy
management.

CLIENT01 uses the domain controller as its DNS
server for domain discovery and authentication.

## Validation

Completed tests:
- Active Directory domain creation
- Organizational Unit and user account creation
- Security group configuration
- Domain join of CLIENT01
- Domain user authentication
- Initial Group Policy application

## Future Improvements

- Helpdesk troubleshooting scenarios
- DNS diagnostics
- Account lockout and password reset procedures
- Group Policy troubleshooting
- PowerShell administration scripts
