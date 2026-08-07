---
title: "System Requirements"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/system_requirements.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# System Requirements


Make sure that machines that you plan to use as Veeam Backup Enterprise Manager infrastructure components meet the following system requirements.

Veeam Backup Enterprise Manager

Server Side

Enterprise Manager on Linux (Veeam Software Appliance)

Enterprise Manager on Linux (Veeam Software Appliance)

| Specification | Requirement |
| Hardware | CPU: x86-64 processor with a minimum of 2 cores (vCPUs). 4 or more cores (vCPUs) are recommended, depending on the load.  Memory: Minimum of 6 GB RAM. 16 GB RAM is recommended.  Disk Selection Logic: When selecting a disk for system and adjacent functions, Veeam Software Appliance automatically chooses an SSD over an HDD, and selects the smaller disk of the two available. The sizing recommendations for Disk 1 below remain valid for the system disk.  Disk 1: 240 GB1 minimum. This disk hosts Veeam JeOS, Enterprise Manager Veeam Backup & Replication software, configuration database and instant recovery cache.  Recommended sizing depends on the number of protected workloads. Sizing also accounts for configuration database growth as you add more workloads to protect:   * 480 GB1 SSD for small environments (up to a few hundred workloads). * 960 GB1 SSD for medium-sized environments (up to a few thousand workloads). * Multi-TB1 SSD for large environments. Larger capacity increases the disk space available to instant recovery cache, allowing for running more machines for longer time.   Note: After Veeam Software Appliance deployment, adding new storage devices or resizing existing ones is not supported. Plan your disk capacity carefully before you start the deployment.  Disk 2: 240 GB1 minimum. This disk hosts guest file system catalogs and backups, therefore recommended sizing depends on your backup storage needs. Any additional disks found in the system during Veeam Software Appliance deployment will be automatically joined with Disk 2 into the single Logical Volume Manager (LVM) spanned volume.  Note: Veeam Software Appliance only supports local disks and hardware RAID. RAID controller with battery or capacitor backed write cache is highly recommended for performance and reliability reasons.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported.  Server Hardware: Veeam offers [Veeam Ready - Appliance](https://www.veeam.com/solutions/alliance-partner/integrations-qualifications.html?programCategory=veeam-ready-appliance) certification for hardware vendors. This certification guarantees verified and certified compatibility, delivering an optimal customer experience through additional requirements for direct technical collaboration between vendors. Veeam also acknowledges that some customers may need to use existing hardware. As a current compatibility guidance, we expect that most systems compatible with RHEL 9.2 listed on the [RHEL Hardware Compatibility List (HCL)](https://catalog.redhat.com/en/search?searchType=Hardware&certified_RedHat_Platforms=Red+Hat+Enterprise+Linux&certified_architectures=x86_64) will be compatible with Veeam Software Appliance. Hardware that is not listed on the RHEL HCL will likely work, but no official compatibility support will be provided.  1 Here GB is considered as 10^9 bytes, TB as 10^12 bytes. |
| Configuration Database | If you are planning to use a remote installation of the PostgreSQL on Linux, ensure that the following packages are installed on it:   * postgresql17.x86\_64 * postgresql17-contrib.x86\_64 * postgresql17-libs.x86\_64 * postgresql17-plperl.x86\_64 * postgresql17-server.x86\_64   All of them must be of version 17.6 or later. |
| Software | * VMware vSphere ESXi 7.0 U2 (7.0.2) or later for OVA deployments. * Veeam Software Appliance ISO deployment to a virtual machine is supported for all hypervisors for which Veeam offers host-based VM backup functionality. For details, see [Supported Platforms, Applications and Workloads](https://helpcenter.veeam.com/docs/vbr/userguide/platform_support.html?ver=13). |

Enterprise Manager on Windows

Enterprise Manager on Windows

| Specification | Requirement |
| Hardware | * CPU: x86-64 processor. * Memory: 8 GB RAM (minimum recommended). * Hard disk space: 2 GB for product installation plus sufficient disk space to store guest file system catalog from connected backup servers (according to data retention policy). * Network: 1 Mbps or faster connection to Veeam Backup & Replication servers. Slow or unstable links will impact the performance of Veeam Backup Enterprise Manager data collection operations from Veeam Backup servers. |
| OS | 64-bit versions of the following operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows 11 (from version 22H2 to version 25H2)  * Microsoft Windows 10 22H2 * Microsoft Windows 10 LTSC 2021 |
| PostgreSQL | Local or remote installation of PostgreSQL 14.x, 15.x or 17.x (version 17.10 is included in the setup).  Note that Veeam Backup Enterprise Manager does not support PostgreSQL installations on cloud database services (for example, Amazon Relational Database Service (RDS). |
| Microsoft SQL Server | Local or remote installation of the following versions of Microsoft SQL Server (both Full and Express Editions are supported):   * Microsoft SQL Server 2025 * Microsoft SQL Server 2022 * Microsoft SQL Server 2019 * Microsoft SQL Server 2017 * Microsoft SQL Server 2016   All editions of Microsoft SQL Server are supported. The usage of Microsoft SQL Server Express Edition is limited by the database size up to 10 GB. If you plan to have larger databases, use other editions of Microsoft SQL Server.  Veeam Backup & Replication and Veeam Backup Enterprise Manager configuration databases can be deployed in Microsoft SQL AlwaysOn Availability Groups. For more information, see [this Veeam KB article](https://www.veeam.com/kb2301). |
| Software | During setup, the system configuration check is performed to determine if all prerequisite software is available on the machine where you plan to install Enterprise Manager. If some of the required software components are missing, the setup wizard will offer you to install missing software automatically. This refers to the following software:   * Microsoft .NET Framework 4.8 * Microsoft .NET Hosting 10.0 * Microsoft SQL Server System CLR Types 2014 (both for SQL Server and PostgreSQL) * Microsoft Visual C++ 2017-2026 Redistributable 14.50.35719.0 * Application Request Routing 3.0.05311 * ASP.NET Core Module 8.0.21   The following software must be installed manually if missing:   * Microsoft Windows Installer 5.0 * Microsoft Internet Information Services 7.5 or later * Microsoft URL Rewrite 2.0 for IIS 7 |

Client Side

Client Side

| Specification | Requirement |
| Browsers | Mozilla Firefox, Google Chrome and Microsoft Edge. The browser must have JavaScript and WebSocket protocol enabled.  Enterprise Manager User Interface may not work correctly in Mozilla Firefox running on Microsoft Windows 11 22H2. |
| Microsoft Excel | Microsoft Excel (to view reports exported to Microsoft Excel format). |

[Optional] VMware Cloud Director

[Optional] VMware Cloud Director

| Specification | Requirement |
| VMware Cloud Director | VMware Cloud Director 10.4.x to 10.6.x. |
| Other software | If your Enterprise Manager deployment uses IIS 8.5, a URL rewrite module is required to work with Veeam Self-Service Backup Portal for VMware Cloud Director. |

[Optional] Veeam Plug-in for VMware vSphere Client

[Optional] Veeam Plug-in for VMware vSphere Client

| Specification | Requirement |
| VMware vSphere | VMware vSphere 7.0 to 9.0. |

Page updated 2026-07-24

