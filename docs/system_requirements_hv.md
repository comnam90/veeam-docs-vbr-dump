---
title: "System Requirements (Microsoft Hyper-V)"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/system_requirements_hv.html"
last_updated: "9/29/2025"
product_version: "13.0.1.1071"
---

# System Requirements (Microsoft Hyper-V)


Make sure that servers that you plan to use as backup infrastructure components to protect your Microsoft Hyper-V virtual machines meet the listed system requirements.

|  |
| --- |
| Note |
| The information on this page is valid as of the date of the last page update. |

Limitations and Recommendations

Coexistence with Mission-Critical Production Servers

We do not recommend you to install Veeam Backup & Replication and its components on mission-critical machines in the production environment such as vCenter Server, Microsoft Hyper-V Server, Domain Controller, Microsoft Exchange Server, Windows Server Essentials and so on. If possible, install Veeam Backup & Replication and its components on dedicated machines. Backup infrastructure component roles can be co-installed.

Microsoft Windows Server Core

You can assign roles of a backup proxy, backup repository, WAN accelerator, Veeam Cloud Connect infrastructure components and tape infrastructure components to machines running Microsoft Windows Server Core.

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

* RDP client version 7.0 or later must be also installed manually (required to open the VM console during SureBackup recovery verification of Microsoft Hyper-V VMs). The RDP client is pre-installed on Microsoft Windows 10/Windows Server 2012 OS or later.
* [Optional] You can add to Veeam Backup & Replication infrastructure SCVMM servers from version 2016 to 2025.

For more information, see the [Backup Server](backup_server.md) section.

Veeam Backup & Replication Console

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x86-64 processor.  Memory: 8 GB RAM  Disk Space: 500 MB for product installation and 4.5 GB for Microsoft .NET Framework 4.7.2 installation.  Network: 1 Mbps connection to the backup server. High latency and low bandwidth impact user interface responsiveness. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  * Microsoft Windows 11 (versions 22H2 – 25H2) * Microsoft Windows 10 (versions 22H2) * Microsoft Windows 10 LTS (versions LTSC 2021) |
| Software | During setup, the system configuration check is performed to determine if all prerequisite software is available on the machine where you plan to install the Veeam Backup & Replication Console. If some of the required software components are missing, the setup wizard will offer you to install missing software automatically. This refers to:   * Microsoft .NET Framework 4.8 * Microsoft .NET Desktop Runtime 8.0 * Microsoft Edge WebView2 Runtime * Microsoft Windows PowerShell 7.4.13   The following software must be installed manually:   * Windows Installer 4.5 or later |

Consider the following:

* [For Microsoft Hyper-V] RDP client version 7.0 or later must be also installed manually (required to open the VM console during SureBackup recovery verification of Microsoft Hyper-V VMs). The RDP client is pre-installed on Microsoft Windows 10/Windows Server 2012 OS or later.

For more information, see the [Backup & Replication Console](backup_console.md) section.

Hyper-V Off-Host Backup Proxy/Hyper-V Host as Backup Proxy

You can deploy and manage backup proxies on supported operating systems of your choice.

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: modern x86-64 processor with 2 cores (vCPUs) minimum. It is recommended to add 1 core (vCPU) for each 2 additional concurrent tasks. Using faster processors improves data processing performance. For more information, see [Limitation of Concurrent Tasks](limiting_tasks.md#proxy).  Memory: 2 GB RAM plus 500 MB for each concurrent task. The actual size of memory required may be larger and depends on the amount of data to back up, machine configuration, and job settings. Using faster memory improves data processing performance.  Disk Space: 300 MB.  Network: 1 Gbps or faster for on-site backup and replication, and 1 Mbps or faster for off-site backup and replication. High latency and reasonably unstable WAN links are supported. |
| OS | 64-bit versions of the following Microsoft Windows operating systems are supported, including Core edition:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022  * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 |
| Software | For off-host backup from CSV (SAN): VSS hardware provider that supports transportable shadow copies. The VSS hardware provider is typically distributed as a part of client components supplied by the storage vendor.  Not required for off-host backup from SMB shared storage. |

For more information, see the [Off-Host Backup Proxies](offhost_backup_proxy.md) section.

If you use the on-host backup mode, note that the source Hyper-V host performing the role of the backup proxy will require additional computing resources similar to those specified as the off-host backup proxy requirements. For more information, see [On-Host Backup](onhost_backup.md).

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


