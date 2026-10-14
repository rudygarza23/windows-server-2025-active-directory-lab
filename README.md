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

## Step 1 - DC01 Virtual Machine Configuration

![DC01 Virtual Machine Configuration](images/01-dc01-vm-configuration.png)

**GitHub Caption:**  
DC01 Virtual Machine Configuration: Created the Windows Server 2025 domain controller VM with dedicated NAT and internal network adapters. The dual-NIC configuration separates Internet connectivity from the private Active Directory lab network.

