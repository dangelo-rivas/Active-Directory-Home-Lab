
# Active Directory Home Lab

## Overview

This project documents my hands-on Active Directory home lab built using Windows Server 2025, Windows 11 Pro, and ZimaOS virtualization.

The environment simulates a small business IT infrastructure for ACME Corporation, allowing me to gain practical experience with Windows Server administration, Active Directory Domain Services (AD DS), DNS, user and group management, domain authentication, and Group Policy.

The objective is to develop real-world skills relevant to IT help desk, desktop support, and junior systems administration roles.

## Lab Environment

- ZimaOS virtualization host
- Windows Server 2025 Standard Evaluation
- Windows 11 Pro workstation
- Active Directory Domain Services (AD DS)
- Windows Server DNS
- Group Policy Management
- Active Directory Users and Computers (ADUC)
- Simulated employee accounts and departments

## Lab Architecture

```text
ZimaOS Virtualization Host
│
├── Windows Server 2025 VM
│   └── ACME-DC01
│       ├── Active Directory Domain Services
│       ├── DNS Server
│       ├── Group Policy Management
│       └── Domain: ad.acme.test
│
└── Windows 11 Pro VM
    └── ACME-PC-001
        ├── Domain-Joined Workstation
        ├── Domain User Authentication
        └── Group Policy Client
```

## Network Configuration

| Component | Configuration |
|---|---|
| Domain | ad.acme.test |
| NetBIOS Name | ACME |
| Domain Controller | ACME-DC01 |
| Domain Controller IP | 10.0.0.194 |
| Windows 11 Workstation | ACME-PC-001 |
| Workstation IP | 10.0.0.5 |
| Default Gateway | 10.0.0.1 |
| Subnet Mask | 255.255.255.0 |
| DHCP | Xfinity Gateway |
| Active Directory DNS | ACME-DC01 |

The domain controller uses a DHCP reservation to maintain a consistent IPv4 address.

Domain-connected workstations use the domain controller for Active Directory DNS resolution.

## Active Directory Structure

Created Organizational Units (OUs) to represent different departments within ACME Corporation.

```text
ad.acme.test
│
├── ACME Users
│   ├── IT
│   ├── Human Resources
│   ├── Finance
│   └── Sales
│
├── ACME Computers
│   └── ACME-PC-001
│
├── ACME Groups
│   ├── GG_IT
│   ├── GG_HR
│   ├── GG_Finance
│   └── GG_Sales
│
└── Domain Controllers
    └── ACME-DC01
```

## Active Directory Administration

### Windows Server and Domain Configuration

- Installed Windows Server 2025 with Desktop Experience.
- Configured the ACME-DC01 server.
- Installed Active Directory Domain Services.
- Created the ad.acme.test forest and domain.
- Configured Windows Server DNS.
- Verified Active Directory DNS and LDAP SRV records.

### User and Security Group Management

- Created eight simulated employee accounts across four departments.
- Organized user accounts into departmental OUs.
- Created departmental Global Security Groups.
- Assigned employees to their appropriate security groups.
- Verified group membership using Active Directory and Windows command-line tools.

### Domain-Joined Workstation

- Joined ACME-PC-001 to the ad.acme.test domain.
- Moved the workstation into the ACME Computers OU.
- Successfully authenticated domain users on Windows 11.
- Verified domain controller discovery using nltest.
- Verified user security group membership using whoami.

### Group Policy Management

**Workstation Logon Policy**

Created and linked a Group Policy Object to the ACME Computers OU.

Configured an authorized-access logon notice for domain workstations.

Verified successful policy application using gpresult and confirmed the logon message appeared.

**Sales Control Panel Restriction**

Created a user-based Group Policy linked to the Sales OU.

Configured the policy to prohibit access to Control Panel and Windows Settings.

Verified that the policy applied to the Sales domain account and confirmed the access restriction.

## Skills Practiced

- Windows Server 2025 administration
- Active Directory Domain Services
- DNS configuration and troubleshooting
- Organizational Unit management
- User account provisioning
- Global Security Group management
- Domain joining and authentication
- Group Policy creation and deployment
- Group Policy troubleshooting
- Windows 11 enterprise administration
- TCP/IP networking
- Technical documentation

## Documentation

The project is organized into five sections:

1. Windows Server Setup
2. Active Directory Configuration
3. Users and Security Groups
4. Domain-Joined Workstation
5. Group Policy Management

Each section will include configuration steps, screenshots, verification results, and skills demonstrated.

## Project Status

**In Progress**

Completed the initial Active Directory deployment, organizational structure, domain user authentication, workstation domain join, and two Group Policy exercises.

Additional administration exercises and documentation will be added as the lab develops.
