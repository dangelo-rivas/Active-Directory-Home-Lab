
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


### 01 - Windows Server Setup

Deployed Windows Server 2025 Standard Evaluation in ZimaVM, configured virtual hardware, resolved a UEFI boot issue, completed installation, and configured the ACME-DC01 server.

[View Windows Server Setup Documentation](01-Windows-Server-Setup/README.md)


### 02 - Active Directory Configuration

Installed Active Directory Domain Services (AD DS) on Windows Server 2025 and promoted ACME-DC01 to a domain controller for the ad.acme.test domain.

Configured and verified Active Directory DNS, confirmed LDAP SRV records, and created Organizational Units for IT, Human Resources, Finance, and Sales.

[View Active Directory Configuration Documentation](02-Active-Directory-Configuration/README.md)


### 03 - Users and Security Groups

Created eight simulated employee accounts across IT, Human Resources, Finance, and Sales in the `ad.acme.test` domain.

Organized accounts into departmental Organizational Units, created Global Security Groups, assigned departmental memberships, and verified group membership using Active Directory Users and Computers and Windows command-line tools.

[View Users and Security Groups Documentation](03-Users-and-Security-Groups/README.md)


### 04 - Domain-Joined Workstation

Joined the Windows 11 Pro workstation `ACME-PC-001` to the `ad.acme.test` Active Directory domain and moved its computer account into the `ACME Computers` Organizational Unit.

Verified domain user authentication with `ACME\mtorres`, confirmed IT security group membership using `whoami /groups`, and successfully discovered the domain controller using `nltest`.

[View Domain-Joined Workstation Documentation](04-Domain-Joined-Workstation/README.md)


### 05 - Group Policy Management

Created and deployed two Active Directory Group Policy Objects (GPOs) to centrally manage Windows 11 workstation settings and departmental access restrictions.

**Workstation Logon Policy:** Configured an ACME Corporation authorized-access notice and verified successful deployment using `gpresult` and the Windows sign-in screen.

**Sales Control Panel Restriction:** Created a user-based GPO linked to the Sales OU, restricting access to Control Panel and Windows Settings. Verified successful policy application and confirmed the restriction while signed in as a Sales employee.

[View Group Policy Management Documentation](05-Group-Policy-Management/README.md)


### 06 - Active Directory Troubleshooting

Simulated and resolved common Active Directory support incidents involving user authentication, account management, permissions, and domain connectivity.

**Completed Scenarios:**
- 01 - Disabled User Account: Diagnosed a failed Windows domain login, identified a disabled account in Active Directory, restored access, and verified successful authentication.

Additional troubleshooting scenarios are in progress.

[View Active Directory Troubleshooting Documentation](06-Active-Directory-Troubleshooting/README.md)


Each section includes configuration steps, screenshots, verification results, and skills demonstrated.



## Project Status

**Core Lab Configuration Complete — Active Directory Troubleshooting In Progress**

Successfully deployed and configured an Active Directory environment using Windows Server 2025 and Windows 11 Pro.

Completed the following:

- Windows Server installation and configuration
- Active Directory Domain Services deployment
- DNS configuration and verification
- Organizational Unit creation
- Employee account and security group management
- Windows 11 domain joining
- Domain authentication verification
- Workstation Group Policy deployment
- Department-specific access restrictions

All five foundational lab sections have been documented with configuration steps, screenshots, and verification results.

### Troubleshooting Progress

- **Scenario 01 — Disabled User Account:** Completed. Diagnosed a failed domain login, identified a disabled employee account, restored access, and verified successful authentication using `whoami`.
- **Scenario 02 — Account Lockout:** Planned
- **Scenario 03 — Expired Password:** Planned
- **Scenario 04 — Shared Folder Permissions:** Planned
- **Scenario 05 — Group Policy Troubleshooting:** Planned
- **Scenario 06 — Domain Trust Failure:** Planned

Additional Active Directory troubleshooting exercises will be completed and documented as the lab develops.

---

## Project Outcomes

Successfully designed, deployed, and administered a virtualized Active Directory environment using Windows Server 2025, Windows 11 Pro, and ZimaOS.

The environment simulates a small business IT infrastructure with centralized user authentication, organizational management, DNS services, Group Policy administration, and practical help-desk troubleshooting.

### Key Accomplishments

- **Windows Server Administration:** Installed and configured Windows Server 2025 as a domain controller within a virtualized environment.

- **Active Directory Deployment:** Installed Active Directory Domain Services and created the `ad.acme.test` domain.

- **DNS Administration:** Configured Active Directory DNS and verified domain controller discovery using DNS and LDAP SRV records.

- **User Management:** Created eight simulated employee accounts across IT, Human Resources, Finance, and Sales.

- **Security Group Management:** Created departmental Global Security Groups and assigned employee memberships.

- **Domain Administration:** Joined a Windows 11 Pro workstation to Active Directory and organized the computer account into a dedicated Organizational Unit.

- **Authentication Verification:** Successfully authenticated domain users and verified group membership and domain controller discovery using `whoami`, `whoami /groups`, and `nltest`.

- **Group Policy Management:** Created, linked, deployed, and verified two Group Policy Objects controlling workstation logon notices and department-specific Windows restrictions.

- **Account Troubleshooting:** Reproduced an employee authentication failure caused by a disabled Active Directory account, identified the root cause, restored account access, and verified successful domain authentication.

- **Technical Documentation:** Documented server deployment, configuration procedures, troubleshooting steps, verification results, and administrative tasks using GitHub.

### Final Result

Completed five foundational Active Directory configuration sections and the first of six planned troubleshooting scenarios.

Demonstrated practical experience with Windows Server administration, Active Directory, DNS, user provisioning, security groups, domain authentication, Group Policy, and user account troubleshooting.

The project provides documented examples of skills relevant to entry-level IT help desk, desktop support, and junior systems administration positions.
