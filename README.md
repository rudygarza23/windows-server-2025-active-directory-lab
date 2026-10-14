```text
╔════════════════════════════════════════════════════════════╗
║                    WINDOWS SERVER 2025                     ║
╚════════════════════════════════════════════════════════════╝

    █████╗  ██████╗████████╗██╗██╗   ██╗███████╗
   ██╔══██╗██╔════╝╚══██╔══╝██║██║   ██║██╔════╝
   ███████║██║        ██║   ██║╚██╗ ██╔╝█████╗
   ██╔══██║██║        ██║   ██║ ╚████╔╝ ██╔══╝
   ██║  ██║╚██████╗   ██║   ██║  ╚██╔╝  ███████╗
   ╚═╝  ╚═╝ ╚═════╝   ╚═╝   ╚═╝   ╚═╝   ╚══════╝

       D I R E C T O R Y    S E R V I C E S

              ┏━━━━━━━━━━━━━━━━━━┓
              ┃       L A B      ┃
              ┗━━━━━━━━━━━━━━━━━━┛
```

Hands-on Windows Server 2025 Active Directory lab demonstrating AD DS, DNS, DHCP, Group Policy, security groups, file permissions, and PowerShell administration.

# Windows Server 2025 Active Directory Lab

## Project Overview

This project demonstrates the installation, configuration, administration, and troubleshooting of a Windows Server 2025 Active Directory environment.

## Technologies Used

- Windows Server 2025
- Active Directory Domain Services
- DNS
- DHCP
- Group Policy
- PowerShell

---

## Step 1 - DC01 Virtual Machine Configuration

![DC01 Virtual Machine Configuration](images/01-dc01-virtual-machine-configuration.png)


DC01 Virtual Machine Configuration: Created the Windows Server 2025 domain controller VM with dedicated NAT and internal network adapters. The dual-NIC configuration separates Internet connectivity from the private Active Directory lab network.

---

## Step 2 - DC01 Static Network Configuration

![DC01 Static Network Configuration](images/02-dc01-static-network-configuration.png)

 
DC01 Static Network Configuration: Configured the Windows Server 2025 domain controller with separate Internet and internal network interfaces. The internal interface uses the static address 172.16.0.1/24 and will provide DNS, DHCP, and Active Directory services to the isolated lab network.

---

## Step 3 - Active Directory Domain Services Installation

![Active Directory Domain Services Installation](images/03-active-directory-domain-services-installed.png)


Active Directory Domain Services Installation: Installed the AD DS server role on Windows Server 2025 in preparation for promoting DC01 to the first domain controller in the new Active Directory forest.

---

## Step 4 - Active Directory Forest and Domain Deployment

![DC01 Domain Controller](images/04-dc01-domain-controller.png)


Active Directory Forest and Domain Deployment: Promoted DC01 to the first domain controller in the corp.rudylab.test Active Directory forest and installed integrated DNS services.

---

## Step 5 - Active Directory Organizational Unit Structure

![Active Directory OU Structure](images/05-active-directory-ou-structure.png)


Active Directory Organizational Unit Structure: Designed and implemented an OU hierarchy for administrators, security groups, departmental users, workstations, and servers. The structure provides logical separation of Active Directory objects and establishes the foundation for targeted Group Policy management.

---

## Step 6 - Active Directory Users and Security Groups

![Active Directory Users and Security Groups](images/06-ad-users-and-security-groups.png)

 
Active Directory Users and Security Groups: Created departmental user accounts using a standardized first.lastname naming convention and organized users into IT, HR, and Finance OUs. Global security groups were created to manage department-based access and permissions.

---

## Step 7 - DHCP Scope Configuration

![DHCP Scope Configuration](images/07-dhcp-scope-configuration.png)


DHCP Scope Configuration: Configured DHCP on Windows Server 2025 to automatically provide ADLAB clients with IPv4 addresses, the domain controller as their default gateway, and Active Directory-integrated DNS settings.

---

## Step 8 - CLIENT01 Domain Join

![CLIENT01 Domain Join](images/08-client01-domain-join-success.png)


CLIENT01 Domain Join: Successfully joined the Windows 11 Pro workstation to the corp.rudylab.test Active Directory domain after verifying DHCP, DNS, and network connectivity to the domain controller.

---

## Step 9 - Domain User Authentication

![Domain User Login](images/09-domain-user-login.png)


Domain User Authentication: Successfully logged into the Windows 11 workstation using the Active Directory account CORP\rudy.garza, confirming centralized domain authentication through DC01.

---

## Step 10 - Workstation OU Management

![CLIENT01 Workstations OU](images/10-client01-workstations-ou.png)


Workstation OU Management: Moved the domain-joined CLIENT01 computer account into the Workstations organizational unit to prepare the device for centralized Group Policy management.

---

## Step 11 - Workstation Group Policy

![Workstation GPO Linked](images/11-workstation-gpo-linked.png)


Workstation Group Policy: Created and linked a Group Policy Object to the Workstations OU to centrally configure Windows 11 domain computers.

---

## Step 12 - Group Policy Logon Message Verification

![Group Policy Logon Message](images/12-group-policy-logon-message.png)


Group Policy Verification: Verified successful application of a computer-based GPO on CLIENT01 by displaying a centrally configured logon security message.

---

## Step 13 - gpresult Policy Verification

![gpresult Policy Verification](images/13-gpresult-policy-verification.png)

 
Group Policy Verification: Used gpresult on CLIENT01 to confirm that the workstation successfully received and applied the domain-based Workstation Logon Message GPO from Active Directory.

---

## Step 14 - Workstation Screen Lock Policy

![Workstation Screen Lock GPO](images/14-workstation-screen-lock-gpo.png)


Workstation Security Policy: Created and linked a Group Policy Object that automatically locks domain workstations after five minutes of inactivity, demonstrating centralized security policy enforcement.

---

## Step 15 - Department SMB File Shares

![Department SMB File Shares](images/15-department-smb-file-shares.png)

  
Department File Shares: Created SMB network shares for IT, HR, and Finance on Windows Server 2025 and assigned department-based access using Active Directory security groups and NTFS permissions.

---

## Step 16 - Finance Share Access Denied

![Finance Share Access Denied](images/16-finance-share-access-denied.png)

 
Department File Access Verification: Verified that the IT user account rudy.garza could not access or create files in the Finance department share, confirming that Active Directory group-based NTFS permissions prevented unauthorized cross-department access.

---

## Step 17 - HR Share Access Denied

<img src="./images/17-hr-share-access-denied.png" alt="HR Share Access Denied">

Department File Access Verification: Verified that the IT user account rudy.garza could not access or create files in the HR department share, confirming that Active Directory group-based NTFS permissions prevented unauthorized cross-department access.

---

## Step 18 - IT Share Access Success

![IT Share Access Success](images/18-it-share-access-success.png)

 
Department File Access Verification: Verified that the IT user account rudy.garza could successfully access and create files in the IT department share through Active Directory group-based NTFS permissions.

---

## Step 19 - Automated IT Drive Mapping

![IT Drive Mapped by Group Policy](images/19-it-drive-mapped-by-group-policy.png)

  
Automated Network Drive Mapping: Used Group Policy Preferences to automatically map the IT department network share as drive I: for users in the IT organizational unit.

---

## Step 20 - Department-Based Drive Mapping

![Department Drive Mapping GPOs](images/20-department-drive-mapping-gpos.png)

Department-Based Drive Mapping: Configured separate Group Policy Objects for IT, HR, and Finance users. Each department automatically receives its authorized SMB network drive based on the user's Active Directory OU.

---

## Step 21 - Active Directory User Provisioning with PowerShell

![PowerShell AD User Automation](images/21-powershell-ad-user-automation.png)

Active Directory User Provisioning with PowerShell: Used a CSV-driven PowerShell script to automatically create departmental user accounts using the first.lastname naming convention and assign each account to the correct Active Directory security group.

---

## Step 22 - Automated User Provisioning Verification

![Automated AD Users Verified](images/22-automated-ad-users-verified.png)

Automated User Provisioning Verification: Verified that PowerShell-created users were placed in the correct Active Directory organizational units and assigned to their appropriate departmental security groups.

---

## Step 23 - Final Group Policy Verification

![Final Group Policy Verification](images/23-final-group-policy-verification.png)

 
Final Group Policy Verification: Confirmed that CLIENT01 successfully received and enforced multiple domain-based Group Policy Objects, including the workstation logon message and automatic screen-lock policy.

---

## Troubleshooting and Validation

Throughout the lab, I verified connectivity, DNS resolution, domain authentication, Group Policy processing, file-share permissions, and automated user provisioning.

Validation methods included:

- `ipconfig /all`
- `ping`
- `nslookup`
- `gpupdate /force`
- `gpresult`
- Active Directory Users and Computers
- Group Policy Management
- DHCP management
- SMB share testing
- NTFS permission testing
- PowerShell verification

Issues were resolved by checking DNS configuration, network connectivity, Active Directory object placement, security group membership, and Group Policy scope.

---

## Skills Demonstrated

- Windows Server 2025 administration
- Active Directory Domain Services
- DNS configuration
- DHCP configuration
- Organizational Unit design
- Active Directory user administration
- Security group management
- Windows 11 domain joining
- Domain authentication
- Group Policy creation and management
- Group Policy verification
- Workstation security policies
- SMB file shares
- NTFS permissions
- Role-based access control
- Network drive mapping
- PowerShell automation
- CSV-based user provisioning
- Troubleshooting
- Technical documentation

---

## Lab Environment

| System | Purpose |
|---|---|
| DC01 | Windows Server 2025 Domain Controller |
| CLIENT01 | Windows 11 Pro domain workstation |
| Domain | `corp.rudylab.test` |
| Internal Network | `172.16.0.0/24` |
| Domain Controller IP | `172.16.0.1` |
| Services | AD DS, DNS, DHCP, Group Policy, SMB |

---

## Project Summary

This lab demonstrates the deployment and administration of a Windows Server 2025 Active Directory environment from initial virtual machine configuration through centralized authentication, Group Policy, departmental file access, and PowerShell automation.

The project was designed to demonstrate practical systems administration skills including identity management, access control, endpoint management, infrastructure services, security policy enforcement, automation, and troubleshooting.
