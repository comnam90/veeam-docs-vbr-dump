---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# System Requirements


Make sure that servers that you plan to use as backup infrastructure components meet the listed system requirements.

|  |
| --- |
| Note |
| The information on this page is valid as of the date of the last page update. |

Backup Server

Linux-Based Backup Server (Veeam Software Appliance)

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor with 8 cores (vCPUs) minimum.  Memory: 16 GB RAM plus 500 MB RAM for each concurrent job.  Disk 1: 240 GB minimum. This disk hosts Veeam JeOS, Veeam Backup & Replication software, configuration database and instant recovery cache.  Recommended sizing depends on the number of protected workloads:   * 480 GB SSD for small environments (up to a few hundred workloads). * 960 GB SSD for medium-sized environments (up to a few thousand workloads). * Multi-TB SSD for large environments. Larger capacity increases the disk space available to instant recovery cache, allowing for running more machines for longer time.   Disk 2: 240 GB minimum. This disk hosts guest file system catalogs and backups, therefore recommended sizing depends on your backup storage needs. Any additional disks found in the system will be automatically joined with Disk 2 into the single Logical Volume Manager (LVM) spanned volume.  Note: Veeam Software Appliance only supports local disks and hardware RAID. RAID controller with battery or capacitor backed write cache is highly recommended for performance and reliability reasons.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported.  Server Hardware: Veeam offers “Veeam Ready - Appliance” certification for hardware vendors. This certification ensures verified and certified compatibility, delivering an optimal customer experience through additional requirements for direct technical collaboration between vendors. Veeam also acknowledges that some customers may need to use existing hardware. As current compatibility guidance, we expect that most systems listed on the [RHEL Hardware Compatibility List (HCL)](https://catalog.redhat.com/en/search?searchType=Hardware&certified_RedHat_Platforms=Red+Hat+Enterprise+Linux&certified_architectures=x86_64) will be compatible with Veeam Software Appliance. |
| Configuration Database | If you are planning to use a remote installation of the PostgreSQL on Linux, ensure that the following packages are installed on it:   * postgresql17.x86\_64 * postgresql17-contrib.x86\_64 * postgresql17-libs.x86\_64 * postgresql17-plperl.x86\_64 * postgresql17-server.x86\_64   All of them must be of version 17.6 or later. |
| Software | * VMware vSphere ESXi 7.0 U2 (7.0.2) or later for OVA deployments. * Veeam Software Appliance ISO deployment to a virtual machine is supported for all hypervisors for which Veeam offers host-based VM backup functionality. For details, see [Supported Platforms, Applications and Workloads](https://helpcenter.veeam.com/docs/vbr/userguide/platform_support.html?ver=13). |

Windows-Based Backup Server

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor with 8 cores (vCPUs) minimum.  Memory: 16 GB RAM plus 500 MB RAM for each concurrent job. Memory consumption varies according to the number of VMs in the job, size of VM metadata, size of production infrastructure, and so on.  [For users with tape installations] For system requirements for large number of files in the file backup to tape job, see the [Before You Begin](file_to_tape_before_you_begin.md#many_files) section for file backup to tape.  Disk Space:   * 5 GB1 for product installation and 4.5 GB for Microsoft .NET Framework 4.7.2 installation. * 10 GB per 100 VM for guest file system catalog folder (persistent data). * Additional free disk space for Instant VM Recovery cache folder (non-persistent data, at least 100 GB recommended). * At least 10 GB for storing logs, although the disk space required for logging depends on the set of features used and may significantly increase. For details on logs locations, see [Logging](logging.md). * When upgrading Veeam Backup & Replication, additional disk space is required. For details, see the [Upgrade Checklist](upgrade_vbr_byb.md#sys_req) section. * If you use a remote repository as a target for a configuration backup job, a temporary BCO file is created in the %TEMP% folder during the job (by default, this is C:\Windows\Temp). Therefore, additional free space is required for the temporary BCO file. For more information, see [Creating Configuration Backups](export_vbr_config.md).   Network: 1 Gbps or faster for on-site backup and replication, 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported.  1 Here and throughout this document GB is considered as 2^30 bytes, TB as 2^40 bytes. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported1:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)   1 Running Veeam backup server or any of Veeam backup infrastructure components on Insider versions of Microsoft Windows OS (both Client and Server) is not supported. |
| Configuration Database | Local or remote installation of the following versions of PostgreSQL1:   * PostgreSQL 17.x (PostgreSQL 17.6 is included in the Veeam Backup & Replication 13 setup) * PostgreSQL 15.x * PostgreSQL 14.x   Note that Veeam Backup Enterprise Manager does not support PostgreSQL installations on cloud database services (for example, Amazon Relational Database Service (RDS).  The PostgreSQL instance must have UTF-8 as the default encoding for the database.  Local or remote installation of the following versions of Microsoft SQL Server1:   * Microsoft SQL Server 2022 * Microsoft SQL Server 2019 * Microsoft SQL Server 2017 * Microsoft SQL Server 2016   All editions of Microsoft SQL Server are supported. The usage of Microsoft SQL Server Express Edition is limited by the database size up to 10 GB. If you plan to have larger databases, use other editions of Microsoft SQL Server.  If you plan to use a database engine other than PostgreSQL 17.x, included in the Veeam Backup & Replication setup, you must install it yourself. If you want to use an already installed PostgreSQL instance for the configuration database, make sure the instance contains the default postgres database. If you allow the setup to install a new PostgreSQL instance, the postgres database will be created on the instance automatically. Since Veeam Backup & Replication connects to the postgres database to access the configuration database, do not rename the postgres database upon the installation.  Veeam Backup & Replication does not support Microsoft SQL Server database with case-sensitive collations.  Veeam Backup & Replication and Veeam Backup Enterprise Manager configuration databases can be deployed in Microsoft SQL Always On Availability Groups. For more information, see [this Veeam KB article](https://www.veeam.com/kb2301).  1 Consider the following:   * Veeam Backup & Replication does not support PostgreSQL and Microsoft SQL Server installations on cloud database services (for example, Amazon Relational Database Service (RDS). * We do not recommend sharing a local instance of PostgreSQL with any other services. It should be dedicated to host the backup server database only. * If you are planning to use Veeam Backup & Replication with Veeam Cloud Connect, note that system requirements for the backup server are different. For more information, see the [Veeam Cloud Connect Guide](https://helpcenter.veeam.com/docs/vbr/cloud/system_requirements.html?ver=13#veeam-backup-server). |
| Software | During setup, the system configuration check is performed to determine if all prerequisite software is available on the machine where you plan to install Veeam Backup & Replication. If some of the required software components are missing, the setup wizard will offer you to install missing software automatically. This refers to:   * Microsoft .NET Framework 4.8  * Microsoft .NET Hosting 8.0.21 * Microsoft .NET Desktop Runtime 8.0.21 * Microsoft SQL Server System CLR Types 2014 (both for SQL Server and PostgreSQL installations) * Microsoft Visual C++ 2015-2022 Redistributable 14.40.33810  * Microsoft Windows PowerShell 7.4.13   Note: The Veeam Backup & Replication uninstaller does not remove any prerequisite software that was previously installed, to avoid causing problems with other programs. When upgrading to a newer version, if a previously required prerequisite is no longer needed, it will also not be uninstalled.  The backup server installation also requires the automatic installation of the prerequisite software for [Veeam Cloud Plug-Ins](#platformservices).  The following software must be installed manually if missing:   * Windows Installer 4.5 or later |

Consider the following:

* If you plan to back up VMs running Microsoft Windows Server 2012 R2 or later, and Data Deduplication is enabled for some VM volumes, it is recommended that you deploy the Veeam Backup & Replication console and mount server on a machine running the same or later version of Microsoft Windows Server with Data Deduplication feature enabled. Otherwise, some types of restore operations for these VMs (such as Microsoft Windows File-Level Recovery) may fail.

* Due to its limitations, Microsoft SQL Server Express Edition can only be used for evaluation purposes or in case of a small-scale production environment. For environments with a lot of VMs, it is necessary to install a fully functional commercial version of Microsoft SQL Server.

* [For Microsoft Hyper-V] RDP client version 7.0 or later must be also installed manually (required to open the VM console during SureBackup recovery verification of Microsoft Hyper-V VMs). The RDP client is pre-installed on Microsoft Windows 10/Windows Server 2012 OS or later.
* [For Microsoft Hyper-V] [Optional] You can add to Veeam Backup & Replication infrastructure SCVMM servers from version 2012 SP1 to 2022. To be able to use them, you must also install SCVMM Admin UI on the backup server. The Admin UI version must match the SCVMM server version.

For more information, see the [Backup Server](backup_server.md) section.

Veeam Infrastructure Appliance

Veeam Infrastructure Appliance is a Linux distribution delivered by Veeam as a bootable JeOS (Just Enough Operating System) ISO file. It contains only services and components required to deploy and manage Veeam infrastructure components with specific roles including hardened repositories and backup proxies.

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum running at 1 GHz or higher.  Memory: 8 GB RAM.  Disk 1: 120 GB minimum. This disk hosts Veeam JeOS, Veeam Backup & Replication software and instant recovery cache.  Disk 2: 120 GB minimum. This disk hosts backups, therefore recommended sizing depends on your backup storage needs. Any additional disks found in the system will be automatically joined with Disk 2 into the single Logical Volume Manager (LVM) spanned volume.  Note: Veeam Infrastructure Appliance only supports local disks and hardware RAID. RAID controller with battery or capacitor backed write cache is highly recommended for performance and reliability reasons.  Network: 1 Gbps or faster for on-site backup and replication, 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported.  Server Hardware: Veeam offers “Veeam Ready - Appliance” certification for hardware vendors. This certification ensures verified and certified compatibility, delivering an optimal customer experience through additional requirements for direct technical collaboration between vendors. Veeam also acknowledges that some customers may need to use existing hardware. As current compatibility guidance, we expect that most systems listed on the [RHEL Hardware Compatibility List (HCL)](https://catalog.redhat.com/en/search?searchType=Hardware&certified_RedHat_Platforms=Red+Hat+Enterprise+Linux&certified_architectures=x86_64) will be compatible with Veeam Software Appliance |
| Software | Veeam Infrastructure Appliance ISO deployment to a virtual machine is supported, provided the hypervisor is listed as supported by Veeam. |

For more information, see the [Deploying Linux Infrastructure Components](linux_infrastructure.md) section.

Veeam Backup & Replication Web UI

| Specification | Requirement |
| --- | --- |
| Browsers | Mozilla Firefox, Google Chrome or Microsoft Edge must be of the latest available version. |
| Microsoft Excel | Microsoft Excel (to view reports exported to Microsoft Excel format). |

For more information, see the [Veeam Backup & Replication Web UI](vbr_web_console.md) section.

Veeam Backup & Replication Console

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor.  Memory: 8 GB RAM  Disk Space: 500 MB for product installation and 4.5 GB for Microsoft .NET Framework 4.7.2 installation.  Network: 1 Mbps connection to the backup server. High latency and low bandwidth impact user interface responsiveness. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (versions 22H2) * Microsoft Windows 10 LTS (versions LTSC 2021) |
| Software | During setup, the system configuration check is performed to determine if all prerequisite software is available on the machine where you plan to install the Veeam Backup & Replication Console. If some of the required software components are missing, the setup wizard will offer you to install missing software automatically. This refers to:   * Microsoft .NET Framework 4.8 * Microsoft .NET Desktop Runtime 8.0 * Microsoft Edge WebView2 Runtime * Microsoft Windows PowerShell 7.4.13   The following software must be installed manually:   * Windows Installer 4.5 or later |

For more information, see the [Backup & Replication Console](backup_console.md) section.

Remote PowerShell Console

| Specification | Requirement |
| --- | --- |
| Operating Systems | 64-bit versions of the following Linux distributions are supported:   * RHEL 9.2 * Rocky Linux 9.2 |
| Software | Microsoft Windows PowerShell 7.5.1 |

For more information, see [Veeam PowerShell Reference](https://helpcenter.veeam.com/docs/vbr/powershell/getting_started.html?ver=13).

VMware Backup Proxy

VMware backup proxies can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled using the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements.md#jeos) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage backup proxies on supported operating systems of your choice.

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum, plus 1 core (vCPU) for each 2 additional concurrent tasks. Using faster processors improves data processing performance. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md#proxy).  Memory: 2 GB RAM plus 1 GB for each concurrent task. The actual size of memory required may be larger and depends on the amount of data to back up, machine configuration, and job settings. Using faster memory improves data processing performance.  Disk Space: 750 MB for Microsoft Windows-based proxies; 400 MB for Linux-based proxies.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported. Note that bash shell and SSH are required.   * Debian 11.0 to 13 * Oracle Linux 7 to 10 * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5 or later, 15 SP3 or later * Ubuntu: 20.04 LTS, 22.04 LTS, 24.04 LTS |

For more information, see the [VMware Backup Proxies](backup_proxy.md) section.

Hyper-V Off-Host Backup Proxy/Hyper-V Host as Backup Proxy

You can deploy and manage backup proxies on supported operating systems of your choice.

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: modern x86-64 processor with 2 cores (vCPUs) minimum. It is recommended to add 1 core (vCPU) for each 2 additional concurrent tasks. Using faster processors improves data processing performance. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md#proxy).  Memory: 2 GB RAM plus 500 MB for each concurrent task. The actual size of memory required may be larger and depends on the amount of data to back up, machine configuration, and job settings. Using faster memory improves data processing performance.  Disk Space: 300 MB.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 |
| Software | For off-host backup from CSV (SAN): VSS hardware provider that supports transportable shadow copies. The VSS hardware provider is typically distributed as a part of client components supplied by the storage vendor.  Not required for off-host backup from SMB shared storage. |

For more information, see the [Off-Host Backup Proxies](offhost_backup_proxy.md) section.

If you use the on-host backup mode, note that the source Hyper-V host performing the role of the backup proxy will require additional computing resources similar to those specified as the off-host backup proxy requirements. For more information, see [On-Host Backup](onhost_backup.md).

General-Purpose Backup Proxy

General-purpose backup proxies can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled using the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements.md#jeos) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage backup proxies on supported operating systems of your choice.

The following table shows the minimum system requirements for a general-purpose backup proxy used for unstructured data backup and Veeam Agent and storage system snapshot integration.

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum. 4 cores (vCPUs) are recommended (2 cores are required) for each additional concurrent task. Using multi-core processors enhances data processing performance and enables the processing of more tasks simultaneously.  Memory: [For unstructured data backup] 4 GB RAM plus 4 GB RAM for each concurrent task.  [For Veeam Agent and storage system snapshot integration] 2 GB RAM plus 1 GB RAM for each concurrent task.  Using faster memory improves data processing performance. For all-in-one installations, where the server performs several roles, it must have enough memory resources for all components.  Disk Space: 300 MB.  Network: High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported:   * Debian 11.0 to 12.11 * Oracle Linux 7 to 10 * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   Note: The VSS snapshot creation for SMB File Shares feature requires that all requirements listed in [this Veeam KB article](https://www.veeam.com/kb3099) are met.  [For Veeam Agent and storage system snapshot integration] Backup proxies and Veeam agent computers must run Microsoft Windows Server OS versions. Backup proxies cannot run the OS versions that are earlier than the Veeam Agent computer OS version. |

For more information, see the [General-Purpose Backup Proxies](backup_proxy_general.md) section.

Nutanix AHV Worker, Proxmox VE Worker and Scale Computing HyperCore Worker

Workers process the backup workload and distribute the backup traffic when transferring data to backup repositories. If you deploy a worker using the default configuration, the following compute resources will be allocated:

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: 6 cores (vCPUs).  Memory: 6 GB RAM  Disk Space: 100 GB for product installation and logs. |

With the default configuration, the worker can handle up to 4 concurrent backup and restore tasks. While deploying a new worker or editing settings of an existing one, you can increase the maximum number of concurrent tasks. However, you must allocate 1 vCPU and 1 GB RAM for each additional task. When configuring the maximum number of concurrent tasks, you must also take into account the network traffic throughput in your virtual infrastructure.

For more information, see the [Veeam Plug-In for Nutanix AHV User Guide](https://helpcenter.veeam.com/docs/vbahv/userguide/overview.html?ver=9),  [Veeam Plug-In for Proxmox VE User Guide](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/system_requirements.html?ver=3) and  [Veeam Plug-In for Scale Computing HyperCore User Guide](https://helpcenter.veeam.com/docs/vpsch/userguide/system_requirements.html?ver=2).

CDP Proxy

The following table shows the minimum system requirements for a CDP proxy.

| Specification | Requirement |
| --- | --- |
| Hardware | CPU : x86-64 processor with 4 cores (vCPUs) minimum. Using multi-core processors improves data processing performance and allows for more tasks to be processed concurrently. Enabling the encryption may cause the performance reduction: in this case, increase the vCPU count up to 2 times.  Memory: 8 GB RAM minimum. Using more memory allows for longer peak write I/O periods before a CDP policy switches to the disk-based write I/O cache. Using faster memory improves data processing performance.  Disk Space: 300 MB plus disk-based write I/O cache (non-persistent data, at least 50 GB recommended). Larger cache allows for longer network downtime periods before a CDP policy switches to the CBT mode.  Network: 100 Mbps or faster. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported. Note that bash shell and SSH are required.   * Debian 11.0 to 13 * Oracle Linux from 8.3 (UEK R6 U2) to 9 (UEK R7) * Oracle Linux 7 to 9 (RHCK) * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5 or later, 15 SP3 or later * Ubuntu: 20.04 LTS, 24.04.3 LTS |

For more information, see the [CDP Proxies](cdp_proxy.md) section.

Backup Repository

A Linux Hardened Repository server can be deployed from the [Veeam JeOS](linux_infrastructure.md) image by selecting the corresponding option. This enables certificate-based authentication over secure, industry-leading communication protocols, eliminates the need to open SSH and additional ports, and minimizes the potential attack surface. In addition to this option, you can deploy and manage the following operating systems on your own.

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor. The number of cores depends on the concurrent task settings. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md#repo).  Memory: 4 GB RAM, plus not less than 1 GB RAM for each concurrently processed machine disk. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md#repo).  [For unstructured data backup] Not less than 4 GB RAM for each concurrently processed unstructured data source (file share or object storage); in case of deduplicating storage appliances, up to 8 GB RAM. Additionally, 1GB RAM is required for indexing each 200 million objects (files and folders). In case of all-in-one installations for unstructured data backup, where the server performs several roles, it must have enough memory resources for all components.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  Note that there can be some issues with Microsoft Windows Server 2025 with the ReFS file system. For details, see [this Veeam KB article](https://www.veeam.com/kb2792).  64-bit versions of the following Linux distributions are supported:   * Debian 11.0 to 13.1 * Oracle Linux 7 to 10 * RHEL 8.6 to 10.0  * Rocky Linux 9 and 10 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 or later, 16 * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   Bash shell and SSH are required to deploy the management agent (SSH connection is not required for updating Veeam components and can be disabled afterwards).  For advanced XFS integration (fast clone), only the following 64-bit Linux distributions are supported:   * Debian 11.0 to 13.1  * RHEL 8.6 to 10.0  * Rocky Linux 9.4 to 10.0  * SLES 15 SP3 or later, 16 * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   For other distributions, XFS integration support is experimental, with kernel version 5.4 or later recommended. For more information, see [this Veeam KB article](https://www.veeam.com/kb2976). |

For more information, see the [Backup Repositories](backup_repository.md) section.

|  |
| --- |
| Note |
| Consider the following:   * If you plan to use a Microsoft Windows backup repository with Data Deduplication, make sure that you set up the Microsoft Windows server correctly. For more information, see [this Veeam KB article](https://www.veeam.com/kb1893). * In rare cases, Veeam backups may become corrupted when stored on the exFAT file system. We strongly discourage using the exFAT filesystem for backup storage when attached to Windows 10 or Windows Server 2019 and later. For more information, see [this Veeam KB article](https://www.veeam.com/kb4233). |

Cache Repository

The following storage types can be used as a cache repository for unstructured data backup:

* Direct attached storage. You can add virtual and physical servers as cache repositories:

* [Microsoft Windows server](ms_server.md) (only 64-bit versions are supported).
* [Linux server](linux_server.md) (only 64-bit versions are supported).

* Network attached storage. You can add [SMB (CIFS) Share](smb_share.md) or [NFS Share](nfs_share.md) as a cache repository.

| Specification | Requirement |
| --- | --- |
| Hardware | Cache repository hardware requirements depend on the target backup repository.  For direct attached storage, network attached storage (NAS) or deduplicating storage appliance as the backup target:   * CPU: x86-64 processor with 2 cores (vCPUs), plus 4 cores (vCPUs) for each concurrently processed unstructured data source.  * Memory: 4 GB RAM, plus 4 GB RAM for each concurrently processed unstructured data source.  * Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported.   For object storage as the backup target:   * CPU: x86-64 processor with 2 cores (vCPUs), plus 6 cores (vCPUs) for each concurrently processed unstructured data source. * Memory: 4 GB RAM, plus 16 GB RAM for each concurrently processed unstructured data source. * Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported:   * Debian 11.0 to 12.11 * Oracle Linux 7 to 10 * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 or later * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   Bash shell and SSH are required to deploy the management agent (SSH connection is not required for updating Veeam components and can be disabled afterwards). Perl is required only for [non-persistent Veeam Data Movers](veeam_transport_service.md). Check the full list of required Perl modules in [this Veeam KB article](https://www.veeam.com/kb2216).  For advanced XFS integration (fast clone), only the following 64-bit Linux distributions are supported:   * Debian 11.0 to 12.11  * RHEL 8.6 to 9.6  * Rocky Linux 9.4 to 9.6  * SLES 15 SP3 or later * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   For other distributions, XFS integration support is experimental, with kernel version 5.4 or later recommended. For more information, see [this Veeam KB article](https://www.veeam.com/kb2976). |

For more information, see Cache Repository in the [Backup Infrastructure for Unstructured Data Backup](unstructured_data_backup_infrastructure.md) section.

Cache Repository for Object Storage Repository

If the cache repository works with an unstructured data source being backed up to an object storage repository, it also processes active metadata that is heavily used during backup and restore operations. So you will require more disk space for the cache repository. The volume of this disk space depends on the number of the file versions on the data source and the number of unstructured data backup jobs that protect this data source. We recommend allocating not less than 1 GB of disk space for active metadata of each 1,000,000 file versions protected with 1 file backup job or object storage backup job. If you protect the same data source, for example, with 2 different backup jobs, the volume of metadata will double. For more information, see the [Unstructured Data Backups in Object Storage Repositories](unstructured_data_backup_in_object_storage.md) section.

|  |
| --- |
| Tip |
| We strongly recommend utilizing a fast storage disk, for example, an SSD in the role of the cache repository used for working with an object storage repository. |

Tape Server

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum. Using multi-core processors improves data processing performance and allows for more tasks to be processed concurrently.  Memory: 2 GB RAM plus 500MB for each concurrent task. Depending on the source of tape jobs, different entities are considered tasks: for machine backup to tape, a task covers a source job or a source chain if tape paralleling is enabled; for file backup to tape, a task covers an entire server or a file share. Restoring VMs directly from tape requires 400MB of RAM per 1TB of the restored virtual disk size. Tape cloning requires 1GB RAM for each concurrent task.  Disk Space: 300 MB, plus 10 GB for temporary data storage for backup and restore operations.  Network: 1 Gbps or faster.  For system requirements for backup to tape jobs, see the [Before You Begin](tape_before_you_begin.md#requirements) section for backup to tape.  For system requirements for large number of files in the file backup to tape job, see the [Before You Begin](file_to_tape_before_you_begin.md#many_files) section for file backup to tape. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported1:   * Debian 11.0 to 13.0 * Oracle Linux 7 (UEK3) to 10 (UEK R7) * Oracle Linux 7 to 10 (RHCK) * RHEL 8.6 to 10.0 * Rocky Linux 9.4 to 10.0 * SLES 12 SP5, 15 SP3 or later * Ubuntu: 20.04 LTS, 22.04 LTS, 24.04 LTS   1 Note that the tape server requires root access rights. For this reason, Veeam Software Appliance, [Veeam Infrastructure Appliance](linux_infrastructure_appliance_install.md) and hardened repository cannot be used as the tape server. |

For more information, see the [Tape Servers](tape_servers.md) section.

WAN Accelerator

WAN accelerators can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled via the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements.md#jeos) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage backup proxies on supported operating systems of your choice.

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor. Using multi-core processors improves data processing performance, and is highly recommended on WAN links faster than 10 Mbps.  Memory: 8 GB RAM. Using faster memory improves data processing performance.  Disk Space: Disk space requirements depend on the WAN Accelerator role. Source WAN Accelerator requires 20 GB per 1 TB of source data to store digests of data blocks of source VM disks. Disk space consumption is dynamic and changes as unique VMs are added to (or removed from) jobs with WAN Acceleration enabled. Target WAN Accelerator requires global cache size as defined by user (fixed amount). Disk space is reserved immediately upon selecting the WAN Accelerator as a target one in any job. For more information, see [WAN Accelerator Sizing](wan_accelerator_sizing.md).  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the following Linux distributions are supported1:   * Debian 11.0 to 12.9 * Oracle Linux 7 (UEK3) to 9 (UEK R7) * Oracle Linux 7 to 9 (RHCK) * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 or later * Ubuntu: 20.04 LTS, 22.04 LTS, 24.04 LTS |

For more information, see the [WAN Accelerators](wan_accelerator.md) section.

|  |
| --- |
| Note |
| Global cache is not leveraged by source WAN accelerators, or by WAN accelerators operating in the High bandwidth mode, so it does not need to be allocated and populated in such cases. |

Backup Target

Backed up data can be stored in the following disk-based systems:

* Local (internal) storage of the backup repository
* Direct Attached Storage (DAS)

The DAS must be connected to the backup repository, including external USB/eSATA drives, USB pass through and raw device mapping (RDM) volumes.

* Storage Area Network (SAN)

The backup repository must be connected into the SAN fabric through hardware or virtual HBA, or software iSCSI initiator.

* Network Attached Storage (NAS)

The NAS must be able to present its capacity as NFS share (protocol versions 3.0 and 4.1 only) or SMB (CIFS) share (any protocol versions). Using SMB (CIFS) protocol for non-continuously available (CA) file shares is not recommended for reliability reasons. Using consumer-grade NAS storage without an enterprise-grade RAID controller with battery-backed write cache (BBWC) is not recommended for reliability considerations.

* Veeam Data Cloud Vault
* Amazon S3
* Google Cloud Storage
* IBM Cloud Object Storage
* Microsoft Azure Blob Storage
* Wasabi Hot Cloud Storage
* 11:11 Cloud Object Storage
* Any S3-compatible object storage (on-premises appliance, or cloud storage provider)
* Dell Data Domain (DD OS version 7.9 to 8.6) with DDBoost license. Both Ethernet and Fibre Channel (FC) connectivity options are supported.
* ExaGrid1 (firmware version 7.2.0 P08 or later)
* Fujitsu ETERNUS CS8001 (CS800 software version 5.2.0 or later)
* HPE StoreOnce (firmware version 3.18.18 or later for Gen3, 4.2.3 or later for Gen4, 5.1.0 or later for Gen 5) with Catalyst license

Both Ethernet and Fibre Channel (FC) connectivity are supported. Note that HPE StoreOnce Federated Catalyst is not supported.

* Infinidat InfiniGuard1 (InfiniGuard software 3.12 or later)
* Quantum DXi1 (DXi software 5.2.0 or later)

Supported Quantum DXi systems include DXiV5000, DXi4800, DXi4801, DXi9000, DXi9100, DXi9200, DXiT10.

1 These storage systems use the Veeam Transport Service. Make sure that they also meet [system requirements for the backup repository](#repo).

Once backups are created, they can be copied (for redundancy) or offloaded (for long-term retention) to hot or cold storage classes of the following object storage systems using the [Scale-Out Backup Repository](backup_repository_sobr.md) [Capacity Tier](capacity_tier.md):

* Veeam Data Cloud Vault
* Amazon S3 (including AWS Snowball Edge)
* Google Cloud Storage
* IBM Cloud Object Storage
* Microsoft Azure Blob storage (including Microsoft Azure Data Box)
* Wasabi Hot Cloud Storage
* 11:11 Cloud Object Storage
* Any S3-compatible object storage (on-premises appliance, or cloud storage provider)

Once backups are created, they can be further offloaded to archive storage classes of the following object storage systems using the [Scale‑Out Backup Repository](backup_repository_sobr.md) [Archive Tier](archive_tier.md):

* Amazon S3 Glacier Instant Retrieval
* Amazon S3 Glacier Flexible Retrieval
* Amazon S3 Glacier Deep Archive
* Microsoft Azure Archive Tier
* Microsoft Azure Cold Tier
* Any S3-compatible object storage with data archiving enabled

For the full list of partner-tested solutions including primary backup storage solutions, S3-compatible object storage solutions and offline storage solutions, see [this Veeam page](https://www.veeam.com/ready.html).

For information on unstructured data backup target, see Storage Repositories in the [Backup Infrastructure for Unstructured Data Backup](unstructured_data_backup_infrastructure.md#backup_repository) section.

Veeam CDP Source and Target Datastores

The following source and target datastores are supported for Veeam CDP:

* NFS on file storage
* VMFS on block storage
* VMFS on internal ESXi storage
* VSAN

VSAN is supported for all hyper-converged infrastructure (HCI) appliances.

* vVol

vVol is supported for the following vendors: NetApp, HPE Nimble, Pure Storage and HPE 3PAR. For the list of tested vendor product lines, see [this Veeam KB article](https://www.veeam.com/kb4225).

Support for HCI appliances is pending validation by Veeam. The documentation will be updated based on the testing results. For the updates, see [CDP Requirements and Limitations](cdp_requirements.md).

|  |
| --- |
| Note |
| Consider the following:   * Cisco HyperFlex 4.5 (2a) and later can be used as a source or target only with VMware vSphere 7.0 U2 and later. With the previous versions of VMware vSphere, Cisco HyperFlex is not supported. * vVol and VSAN of each vendor have limits for the number of storage objects. Once the limit is reached, CDP starts to fail because creation of new objects cannot be completed. To restore the CDP process, remove some objects from VSAN/vVol. * CDP performance depends on your datastore characteristics. For better performance, check that your target datastore is able to process the I/O workload produced on the source datastore. |

Tape

| Specification | Requirement |
| --- | --- |
| Hardware | The following types of tape libraries (including VTL) and standalone drives are supported:   * LTO3-LTO10 * IBM 3592 (TS1160 and TS1170)   Tape device must be directly attached to the backup server or to a tape proxy server through SAS, FC or iSCSI interface. Note that VMware [does not support](https://knowledge.broadcom.com/external/article/310914/configuring-vendorsupported-tape-drives.html) connecting tape libraries to ESXi for VM pass-through. |
| Software | * Tape devices without device-specific, vendor-supplied OEM drivers for Windows will appear in Windows Device Manager as Unknown or Generic and require enabling native SCSI commands mode.  * If multiple driver installation modes are available for your tape device, use the one that allows for multiple open handles from a host to a drive to exist at the same time. Usually, such drivers are referred to as “non-exclusive”.  * No other backup server must be interacting with the tape device. |

For more information, see the [Tape Device Support](working_with_tapes.md) section.

Storage Systems

Veeam Backup & Replication provides different types of snapshot integrations and these integrations support different storage systems. For details, see the following table.

|  |
| --- |
| NOTE |
| [For VMware integration] You may encounter scenarios when Veeam Backup & Replication and the storage system support different versions of the virtual platform. In such cases, we recommend using versions supported by the storage system. If other versions are used, Veeam support will assist only with issues unrelated to version compatibility. |

|  | Microsoft Windows-based Backup Server | | Linux-based Backup Server | |
| --- | --- | --- | --- | --- |
| NAS Integration | VMware and Agent Integrations | NAS Integration | VMware and Agent Integrations |
| Built-In Storage Systems | | | | |
| Cisco HyperFlex HX-Series | ✕ | * VMware integration only (experimental, see [this Veeam KB article](https://www.veeam.com/kb2976)) * NFS connectivity only * HyperFlex 5.0 (2x) or later (Backup from Storage Snapshots, Full Integration mode) * Basic authentication is not supported for SSO users in HyperFlex | ✕ | * VMware integration only (experimental, see [this Veeam KB article](https://www.veeam.com/kb2976)) * NFS connectivity only * HyperFlex 5.0 (2x) or later (Backup from Storage Snapshots, Full Integration mode) * Basic authentication is not supported for SSO users in HyperFlex |
| Dell PowerScale (formerly Isilon) | * Filer integration for NAS backup functionality * NFS or SMB (CIFS) connectivity * OneFS 8.1.2 to 9.11 | ✕ | * Filer integration for NAS backup functionality * NFS or SMB (CIFS) connectivity * OneFS 8.1.2 to 9.11 | ✕ |
| Dell Unity (XT) | ✕ | * NFS, Fibre Channel (FC) or iSCSI connectivity  * Dell Unity XT/Unity OE versions 5.0 to 5.5 | ✕ | * NFS, Fibre Channel (FC) or iSCSI connectivity  * Dell Unity XT/Unity OE versions 5.0 to 5.5 |
| Fujitsu ETERNUS HX/AX | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported | * NFS, Fibre Channel or iSCSI connectivity * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.10 to 9.17.1 * ONTAP 7-mode is not supported | ✕ |
| HPE 3PAR StoreServ | ✕ | * Fibre Channel (FC) or iSCSI connectivity * 3PAR OS versions 3.2.2 up to 3.3.2 * WSAPI 1.5 and later  * iSCSI VLAN tags are supported | ✕ | * Fibre Channel (FC) or iSCSI connectivity * 3PAR OS versions 3.2.2 up to 3.3.2 * WSAPI 1.5 and later  * iSCSI VLAN tags are supported |
| HPE Alletra 5000/6000 | ✕ | * Fibre Channel (FC) or iSCSI connectivity * OS version 6.1 | ✕ | * Fibre Channel (FC) or iSCSI connectivity * OS version 6.1 |
| HPE Alletra 9000 | ✕ | * Fibre Channel (FC), iSCSI or NVMe-oF connectivity * OS version 9.3 or later | ✕ | * Fibre Channel (FC), iSCSI or NVMe-oF connectivity * OS version 9.3 or later |
| HPE Alletra Storage MP B10000 | ✕ | * Fibre Channel (FC), iSCSI or NVMe-oF connectivity   iSCSI is supported starting from OS version 10.3.   * OS version 10.2 or later | ✕ | * Fibre Channel (FC), iSCSI or NVMe-oF connectivity   iSCSI is supported starting from OS version 10.3.   * OS version 10.2 or later |
| HPE Nimble Storage AF-Series, | ✕ | * Fibre Channel (FC) or iSCSI connectivity * Nimble OS from 5.2 up to 6.1.2 | ✕ | * Fibre Channel (FC) or iSCSI connectivity * Nimble OS from 5.2 up to 6.1.2 |
| HPE Primera | ✕ | * Fibre Channel (FC) or iSCSI connectivity   iSCSI is supported starting starting from OS versions 4.3 or later.   * OS versions 4.x | ✕ | * Fibre Channel (FC) or iSCSI connectivity   iSCSI is supported starting starting from OS versions 4.3 or later.   * OS versions 4.x |
| Lenovo ThinkSystem DM/DG Series | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported | * NFS, Fibre Channel or iSCSI connectivity * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.10 to 9.17.1 * ONTAP 7-mode is not supported | ✕ |
| NetApp FAS/AFF/ASA, | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported * NetApp ASA r2 systems (ASA A1K, ASA A70, and ASA A90) are not supported | * NFS, Fibre Channel or iSCSI connectivity * ONTAP cluster-mode versions 9.7 to 9.17.1 * ONTAP 7-mode is not supported * NetApp ASA r2 systems (ASA A1K, ASA A70, and ASA A90) are not supported. | * NFS or SMB (CIFS) connectivity  * ONTAP cluster-mode versions 9.10 to 9.17.1 * ONTAP 7-mode is not supported * NetApp ASA r2 systems (ASA A1K, ASA A70, and ASA A90) are not supported | ✕ |
| Nutanix Files | * Filer integration for NAS backup functionality * NFS or SMB (CIFS) connectivity * Nutanix File Server 3.8.1.3 to 5.2 | ✕ | * Filer integration for NAS backup functionality * NFS or SMB (CIFS) connectivity * Nutanix File Server 3.8.1.3 to 5.2 | ✕ |
| Universal Storage API Integrated Systems | | | | |
| DataCore SANsymphony | ✕ | * Fibre Channel (FC) or iSCSI connectivity  * DataCore SANsymphony 10.0 PSP12 or later | ✕ | ✕ |
| Dell PowerMax | ✕ | * Fibre Channel (FC) or iSCSI connectivity * Dell PowerMax/VMAX All Flash (PowerMax OS microcode 5978.711.711 or later 5978 family updates, and PowerMaxOS 10.1.0.0 or later) * Unisphere for PowerMax 9.2.1.6 or later   For information on supported PowerMax versions, see [this Veeam KB article](https://www.veeam.com/kb4200). | ✕ | ✕ |
| Dell PowerStore | ✕ | * Fibre Channel (FC) or iSCSI connectivity * Dell PowerStore (PowerStore OS 3.0 to 4.2) | ✕ | ✕ |
| Dell SC Series (formerly Compellent) | ✕ | * Fibre Channel (FC) or iSCSI connectivity  * Storage Center OS 7.4.2 or later * FluidFS volumes and Live Volumes are not supported | ✕ | ✕ |
| Fujitsu ETERNUS AF and DX Series | ✕ | * Fibre Channel (FC) or iSCSI connectivity * ETERNUS AF series: AF250 S2, AF650 S2, AF150 S3, AF250 S3, AF650 S3 * ETERNUS DX series: DX60 S4, DX100 S4, DX200 S4, DX500 S4, DX600 S4, DX8900 S4, DX60 S5, DX100 S5, DX200 S5, DX500 S5, DX600 S5, DX900 S5, DX600 S6, DX900 S6, DX8900 S6 * Storage firmware version:  * ETERNUS AF S2 and DX S4 series (except DX8900 S4): V10L88-1000 or later * ETERNUS AF S3 and DX S5 series, DX8900 S4: V11L30-5000 or later * ETERNUS DX S6 series: V12L10-0000 or later | ✕ | ✕ |
| Hitachi VSP/VSP One Block | ✕ | * Fibre Channel (FC) or iSCSI connectivity  * VSP E series (93-03-01-60/00 or later) * VSP F series (88-07-01-x0/00 or later) * VSP G series (88-07-01-x0/00 or later) * VSP 5100 and VSP 5500 (90-05-01-00/00 or later) * VSP 5200 and VSP 5600 (90-08-01-00/00 or later) * VSP One Block series (A3-03-01-x0/01 or later) | ✕ | * Fibre Channel (FC) or iSCSI connectivity  * VSP E series (93-03-01-60/00 or later) * VSP F series (88-07-01-x0/00 or later) * VSP G series (88-07-01-x0/00 or later) * VSP 5100 and VSP 5500 (90-05-01-00/00 or later) * VSP 5200 and VSP 5600 (90-08-01-00/00 or later) * VSP One Block series (A3-03-01-x0/01 or later) |
| IBM FlashSystem (formerly Spectrum Virtualize,  includes IBM StorWize and IBM SVC) | ✕ | * Fibre Channel (FC) or iSCSI connectivity * IBM Spectrum Virtualize OS version 8.4 or later * Policy-based replication relationships are not detected   You will not be able to select this feature for backup and snapshot orchestration with secondary storage arrays.   * Policy-based high availability (PBHA) configurations are not supported   Volumes covered by PBHA cannot be used for the storage integration feature. | ✕ | * Fibre Channel (FC) or iSCSI connectivity * IBM Spectrum Virtualize OS version 8.4 or later * Policy-based replication relationships are not detected   You will not be able to select this feature for backup and snapshot orchestration with secondary storage arrays.   * Policy-based high availability (PBHA) configurations are not supported   Volumes covered by PBHA cannot be used for the storage integration feature. |
| INFINIDAT Infinibox F-Series | ✕ | * NFS, Fibre Channel (FC) or iSCSI connectivity * InfiniBox 5.0 or later   Note: You must add to the backup infrastructure only one of the two InfiniBox storage arrays for which Active/Active Replication is configured, or exclude the replicating volumes on one of these arrays from rescan. For details on how to exclude volumes from rescan, see [Rescanning Storage Systems](storage_rescan.md). | ✕ | ✕ |
| NEC Storage M Series | ✕ | * Fibre Channel (FC) or iSCSI connectivity  * M120, M320, M320F, M520, M720, M720F (Storage Control Software revision 1234 or later) | ✕ | ✕ |
| NetApp SolidFire/HCI | ✕ | * iSCSI connectivity * Element OS version 10.0 or later | ✕ | ✕ |
| Pure Storage FlashArray | ✕ | * NFS, Fibre Channel (FC) or iSCSI connectivity * Purity 6.3 or later | ✕ | ✕ |
| Tintri IntelliFlash  (formerly Western Digital IntelliFlash, Tegile) | ✕ | * NFS, Fibre Channel (FC) or iSCSI connectivity * Tintri IntelliFlash 3.11 or later | ✕ | ✕ |

Gateway Server

Gateway servers can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled using the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements.md#jeos) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage gateway servers on supported operating systems of your choice.

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum.  Memory: 4 GB RAM, plus up to 4 GB RAM for each concurrently processed machine, file share or object storage. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md). For RAM allocation recommendations for unstructured data backup, see [Limitations and recommendations for unstructured data backup](#nas_recommendations).  Disk space: 750 MB for Microsoft Windows-based proxies; 400 MB for Linux-based proxies.  Note: If a unstructured data backup stored in an object storage does not have metadata in the cache repository, during the restore or health check operation this metadata will be downloaded to the gateway server. That can consume up to 80% of the gateway server disk space.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  Note that the fast cloning on ReFS volumes feature requires a Microsoft Windows gateway server.  64-bit versions of the following Linux distributions are supported:   * Debian 11.0 to 13.1 * Oracle Linux 7 to 10 * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   Note: If you use RHEL or Rocky Linux version 9 or later, and do not use [Veeam Infrastructure Appliance](linux_infrastructure.md), you must install the following packages before adding the server to the backup infrastructure: cifs-utils (for the gateway server assigned to a SMB backup repository) or nfs-utils (for the gateway server assigned to a NFS backup repository). |

For more information, see the [Gateway Server](gateway_server.md) section.

Mount Server

Mount servers can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled using the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements.md#jeos) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage backup proxies on supported operating systems of your choice.

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor with 2 cores (vCPUs) minimum, plus 1 core (vCPU) for each 2 additional concurrent tasks. Using faster processors improves data processing performance.  Memory: 4 GB RAM, plus not less than 1 GB RAM for each concurrently processed machine disk.  The following jobs consume not less than 400 MB RAM per guest VM on mount server:   * Windows file level restore   The following jobs consume 1 GB RAM per guest VM disk on mount server + 100 MB RAM per VM:   * SureBackup * Instant Recovery * Instant Disk Recovery   Disk Space: 1.4 GB for product installation and 4.5 GB for Microsoft .NET Framework 4.7.2 installation. If Microsoft .NET Framework 4.7.2 is not installed on the machine, Veeam Backup & Replication will install it automatically.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (version 22H2) * Microsoft Windows 10 LTS (version LTSC 2021)  64-bit versions of the Linux operating systems:   * RHEL 9.6 * Rocky Linux 9.6   Note: If you use RHEL or Rocky Linux version 9 or later, and do not use [Veeam Infrastructure Appliance](linux_infrastructure.md), you must install the following packages before adding the server to the backup infrastructure: aspnetcore-runtime (version 8.0 or later), bindfs, samba-client and ntfs-3g.  Note: If you use the Microsoft Windows-based mount server and plan to restore guest OS files from workloads that run Microsoft Windows with ReFS volumes, or from workloads with data deduplication enabled for some volumes, you must assign the mount server role to the machines running the required OS versions. For more information, see [ReFS](guest_restore_before_you_begin.md#refs) and [Data Deduplication](guest_restore_before_you_begin.md#dedup) subsections in Restoring VM Guest OS Files. |

For more information, see the [Mount Server](mount_server.md) section.

Linux Helper Host

Linux helper hosts can be deployed using the [Veeam JeOS](linux_infrastructure.md) image by selecting the Infrastructure Appliance option. This enables certificate-based authentication, secure industry-standard communication protocols, and automated updates that are centrally controlled using the [Veeam Backup & Replication server](backup_server.md).

|  |
| --- |
| Note |
| Component hardware requirements must be added to the [Veeam JeOS](system_requirements.md#jeos) system requirements to ensure that the assigned role has sufficient CPU and RAM resources. |

In addition to this option, you can deploy and manage backup proxies on supported operating systems of your choice.

|  |
| --- |
| Note |
| Bash shell and SSH are required. |

| OS | Version/Distribution |
| --- | --- |
| Linux | 64-bit versions of the following Linux distributions are supported:   * Debian 11.0 to 13.1 * Oracle Linux 7 to 10 * RHEL 8.6 to 9.6  * Rocky Linux 9 latest supported minor release, see [Rocky Linux Wiki Rocky Linux Release and Version Guide](https://wiki.rockylinux.org/rocky/version/#current-supported-releases)  * SLES 12 SP5, 15 SP3 * Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS   Note: If you use RHEL or Rocky Linux version 9 or later, do not use [Veeam Infrastructure Appliance](linux_infrastructure.md), and mount disks with the NTFS file system, you must install the ntfs-3g package before adding the server to the backup infrastructure. |
| IBM AIX | The following versions of the operating system are supported:  IBM AIX 7.1 – 7.3 TL2 |
| Oracle Solaris | The following versions of the operating system are supported:  Oracle Solaris 10 1/13, 11.0 – 11.4 |

For more information, see [Guest OS File Restore](guest_file_recovery.md).

Veeam Backup Enterprise Manager Server

The machine where you plan to install [Veeam Backup Enterprise Manager](enterprise_manager.md) must meet the requirements listed in the [System Requirements](https://helpcenter.veeam.com/docs/vbr/em/system_requirements.html?ver=13) section of the Enterprise Manager User Guide.

Veeam Plug-Ins

The machine where you plan to install Veeam Plug-Ins must meet the following requirements:

|  |
| --- |
| Important |
| The Microsoft .NET Core Runtime and Microsoft ASP.NET Core Shared Framework must be of the same version (up to the minor version number). Otherwise, starting the Veeam Plug-In will fail. |

| Veeam Plug-In | Requirement |
| --- | --- |
| AWS Plug-In for Veeam Backup & Replication version 13.10.0.xxx and later | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Backup for AWS User Guide](https://helpcenter.veeam.com/docs/vbaws/guide/system_requirements.html?ver=10). |
| Microsoft Azure Plug-In for Veeam Backup & Replication version 13.8.1.xxx and later | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Backup for Microsoft Azure User Guide](https://helpcenter.veeam.com/docs/vbazure/guide/system_requirements.html?ver=8.1). |
| Veeam Plug-in for Google Cloud version 13.0.0.xxx and later1 | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Backup for Google Cloud User Guide](https://helpcenter.veeam.com/docs/vbgc/guide/system_requirements.html?ver=7). |
| Veeam Plug-In for Nutanix AHV version 13.9.0.xxx and later | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Plug-In for Nutanix AHV User Guide](https://helpcenter.veeam.com/docs/vbahv/userguide/system_requirements.html?ver=9). |
| oVirt KVM Plug-In for Veeam Backup & Replication version 13.7.0.xxx and later1 | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [oVirt KVM Plug-In for Veeam Backup & Replication User Guide](https://helpcenter.veeam.com/docs/vbrhv/userguide/system_requirements.html?ver=7). |
| Veeam Plug-In for Proxmox Virtual Environment version 13.3.0.xxx and later | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Plug-In for Proxmox VE User Guide](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/system_requirements.html?ver=3). |
| Veeam Plug-In for Scale Computing HyperCore version 13.2.0.xxx | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Plug-In for Scale Computing HyperCore User Guide](https://helpcenter.veeam.com/docs/vpsch/userguide/system_requirements.html?ver=2). |
| Veeam Kasten Plug-In for Veeam Backup & Replication version 13.2.1.xxx and later | Microsoft .NET Core Runtime 8  Microsoft ASP.NET Core Shared Framework 8  For other system requirements of the plug-in, see the [Veeam Kasten Integration Guide](https://helpcenter.veeam.com/docs/vbr/kasten_integration/system_requirements.html?ver=13). |

1 This plug-ins work only with Microsoft Windows-based backup servers.

Veeam Plug-Ins for Enterprise Applications

Backup Server

Besides [general system requirements for the backup server](system_requirements.md#backup_server), we recommend adding an extra 1 CPU Core and 2.5 GB RAM to your configuration for each 5 machines protected with Veeam Plug-Ins for Enterprise Applications.

Machines with Veeam Plug-Ins for Enterprise Applications

* [Veeam Plug-In for Oracle RMAN](plugins_rman_system_requirements.md)
* [Veeam Plug-In for SAP HANA](system_requirements_saphana.md)
* [Veeam Plug-In for SAP on Oracle](sysreqs_sap_orcl.md)
* [Veeam Plug-In for SAP MaxDB](plugins_sap_maxdb_preparation_sys_reqs.md)
* [Veeam Plug-In for Microsoft SQL Server](system_requirements_mssql.md)
* [Veeam Plug-In for IBM Db2](db2_plugin_system_requirements.md)

MongoDB Backup

[Machines with MongoDB Backup](mongo_plan_and_manage_requirements.md)

Veeam Explorers

* [Veeam Explorer for Microsoft Active Directory](https://helpcenter.veeam.com/docs/vbr/explorers/vead_prerequisites.html?ver=13)
* [Veeam Explorer for Microsoft Exchange](https://helpcenter.veeam.com/docs/vbr/explorers/vex_prerequisites.html?ver=13)
* [Veeam Explorer for Microsoft SharePoint](https://helpcenter.veeam.com/docs/vbr/explorers/vesp_prerequisites.html?ver=13)
* [Veeam Explorer for Microsoft SQL Server](https://helpcenter.veeam.com/docs/vbr/explorers/vesql_prerequisites.html?ver=13)
* [Veeam Explorer for Microsoft Teams](https://helpcenter.veeam.com/docs/vbr/explorers/vet_prerequisites.html?ver=13)
* [Veeam Explorer for Microsoft OneDrive for Business](https://helpcenter.veeam.com/docs/vbr/explorers/veod_planning_and_prep.html?ver=13)
* [Veeam Explorer for MongoDB](https://helpcenter.veeam.com/docs/vbr/explorers/vemdb_prerequisites.html?ver=13)
* [Veeam Explorer for Oracle](https://helpcenter.veeam.com/docs/vbr/explorers/veo_prerequisites.html?ver=13)
* [Veeam Explorer for PostgreSQL](https://helpcenter.veeam.com/docs/vbr/explorers/vep_prerequisites.html?ver=13)
* [Veeam Explorer for SAP HANA](https://helpcenter.veeam.com/docs/vbr/explorers/vehana_prerequisites.html?ver=13)

Veeam Agents

The machines where you plan to install Veeam Agents must meet the following requirements:

* [System Requirements for Microsoft Windows Computers](agents_system_requirements_windows.md)
* [System Requirements for Linux Computers](agents_system_requirements_linux.md)
* [System Requirements for Unix Computers](agents_system_requirements_unix.md)
* [System Requirements for Mac Computers](agents_system_requirements_mac.md)

Limitations and Recommendations

Coexistence with Mission-Critical Production Servers

We do not recommend you to install Veeam Backup & Replication and its components on mission-critical machines in the production environment such as vCenter Server, Microsoft Hyper-V Server, Domain Controller, Microsoft Exchange Server, Windows Server Essentials and so on. If possible, install Veeam Backup & Replication and its components on dedicated machines. Backup infrastructure component roles can be co-installed.

Microsoft Windows Server Core

You can assign roles of a backup proxy, backup repository, WAN accelerator, Veeam Cloud Connect infrastructure components and tape infrastructure components to machines running Microsoft Windows Server Core.
Installing Veeam Backup & Replication and Veeam Backup Enterprise Manager on a Windows OS machine without Desktop Experience (Core) is not supported.

Windows Server IoT/Windows Storage Server Support

For information about support of Windows Server IoT/Windows Storage Server, see [this Veeam KB article](https://www.veeam.com/kb1923).

Domain Member

The machine on which you plan to install Veeam Backup & Replication does not necessarily need to be a domain member. However, if you plan to restore Microsoft Exchange items from the Veeam Backup Enterprise Manager UI, you must install Veeam Backup Enterprise Manager on the domain member server from the Microsoft Active Directory forest in which Microsoft Exchange mailboxes are located.

All-in-One Installations

For [all-in-one installations](simple.md), you can subtract 2 GB of memory resources from each but one role. These 2 GB are allotted to the OS itself, assuming each component is installed on the dedicated server.

Sharing Backup Infrastructure Components Across Veeam Installations

Using Linux-based shared backup infrastructure components across different Veeam installations is not supported.

As for non-Linux backup infrastructure components, we do not recommend using them shared across different Veeam installations due to several reasons:

* Veeam installations compete for resources.
* Backup components cannot simultaneously interact with Veeam Backup & Replication of different versions.
* Adding the same repository to different Veeam Backup & Replication installations may lead to corrupted backup and data in the database.

Native Hyper-V Replication

Do not use native Hyper-V replication especially if replication is targeted at the same scope (host, cluster, SCVMM) where the source VM resides. This can cause VM ID collision. Instead, we recommend you use Veeam replication. For more information, see [Replication](replication.md).

Unstructured Data Backup

Each of the following components for unstructured data backup may consume up to 4 GB RAM per task (in case of deduplicating storage appliances, up to 8 GB RAM): [backup repository](#repo), [general-purpose backup proxy](#file_proxy), [cache repository](#cache_repo). Make sure you allocate enough memory resources for your installation. For all-in-one installations, where the server performs several roles, it must have enough memory resources for all components.


