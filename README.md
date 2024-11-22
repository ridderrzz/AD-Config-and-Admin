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
4) Select VMware Workstation Pro and then select the latest version for your operating system (If you are to do this project on Mac OS, you will need to Select VMWare Fusion instead).
5) Accept the terms and conditions, download the installer and follow the installation instructions.

## Configuring Virtual Machines

1) Firstly, you will need to download the disk images for Windows Server 2022 and Windows 11 Enterprise. A free evaluation copy can be downloaded from the [Microsoft Evaluation Centre](https://www.microsoft.com/en-gb/evalcenter)
2) Inside VMWare, select create a new virtual machine and follow the instructions.
3) When asked for the OS Image, select "I will install the OS myself later" ![New Virtual Machine Wizard](/assets/images/VMware3.jpg)
4) Name the first virtual machine Windows Server 2022, as that is what will be installed first. 
5) Continue the setup with the default settings. Then in the hardware settings, mount the OS Image that you downloaded earlier.
6) Repeat steps 1-5 for Windows 11 Enterprise