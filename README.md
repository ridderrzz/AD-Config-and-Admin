# Active Directory Environment Configuration and Administration

## Summary
Capstone project from TCM Security Practical Help Desk Course. This document will describe the process of installing Windows Server 2022 and Windows 11 Enterprise on virtualised hardware. Thereafter, it willl explain how to create a domain controller and link the Windows 11 machine to the domain. Lastly, this document will detail some basic administrative tasks including setting group policy objects, bulk creation of users and a setup of a password policy.

## Requirements

**Storage**: At least 30 gigabytes of storage to install a hypervisor and configure enough storage space on the virtual machines.

**RAM**: At least 8 gigabytes although 16 gigabytes is recommended.

**Processor**: A processor with 4 or more cores. The processor should also be equipped with virtualisation technologies such as AMD-V or Intel VT-x. Most processors come equipped with this.

**Hypervisor**: This project was done using VMware Workstation Pro version 17.6.1 but this project can otherwise be completed using Oracle Virtualbox.

## Installing the Hypervisor

1) You will need to download a hypervisor. For this project, VMware Workstation Pro will be used and can be downloaded [here](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion).
2) When you click on the link to download VMware, you will be redirected to the Broadcom Support Portal where you will need to create an account.
3) Once you access the support portal, navigate to Software > VMware Cloud Foundation > My Downloads.
4) Select VMware Workstation Pro and then select the latest version for your operating system (If you are to do this project on Mac OS, you will need to Select *VMWare Fusion instead*).
5) Accept the terms and conditions, download the installer and follow the installation instructions.

## Configuring Virtual Machines

1) Firstly, you will need to download the disk images for Windows Server 2022 and Windows 11 Enterprise. A free evaluation copy can be downloaded from the [Microsoft Evaluation Centre](https://www.microsoft.com/en-gb/evalcenter)
2) Inside VMWare, select create a new virtual machine and follow the instructions.
3) When asked for the OS Image, select "I will install the operating system later" ![New Virtual Machine Wizard](/assets/images/VMware3.jpg)
4) Name the first virtual machine Windows Server 2022, as that is what will be installed first. 
5) Continue the setup with the default settings. Then in the hardware settings, mount the OS Image that you downloaded earlier.
6) Repeat steps 2-5 for Windows 11 Enterprise

## Installing Windows
### It is sufficient to use the default settings and follow the Windows Setup wizard. Although it is important to make note of the following:
- When asked to select the OS to install, select *Windows Server 2022 Standard Evaluation (Desktop Experience)*
<img src="/assets/images/WindowsServer1.jpg" width="720" height="500">
- Ensure you install a custom installation for both Windows 11 and Windows Server

## Domain Controller Setup
1) In Server Manager select *add roles and features*
2) Select *role-based or feature-based installation* and specify the server that you are going to install active directory on
3) Select *Active Directory Domain Services* and add the extra features required
4) Continue the wizard with the default parameters and settings
5) Ensure that on the confirmation screen *restart the destination server automatically if required* is enabled
6) Once the active directory services have installed, select *Promote this server to a domain controller*
7) Select *add a new forest* and specify a root domain name of your choice
8) In the domain controller options specify a Directory Services Restore Mode (DSRM) password
9) Continue the wizard with the default parameters and settings
10) Once the prerequisite checks are complete, click install
11) Once the server has restarted, install *Active Directory Certificate Services (AD CS)*
12) Configure AD CS with the default settings and finish installation

## Linking Windows 11 Client with Active Domain Controller

1) On the Domain Controller, launch command prompt as an administrator and type ipconfig and note down the IPV4 Configuration
2) Navigate to Control Panel > Network and Internet > Network and Sharing Centre > Change adapter settings
3) Right click the network adapter and select properties > TCP/IPV4 and fill in the necessary fields with the values from command prompt
4) In the box corresponding to *Preferred DNS Server* assign 127.0.0.1
5) Repeat steps 1-3 for the Windows 11 client and for step 4, input the IPV4 address of the domain controller
6) On the Windows 11 Client, navigate to *add work or school account* in settings and click on *add account*
7) Select *Join a Local Microsoft Active Directory Domain*, input the domain name and authenticate using the administrator credentials
8) Restart and the Windows 11 Client should be part of the domain!