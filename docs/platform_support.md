---
title: "Supported Platforms, Applications and Workloads"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support.html"
last_updated: "2/12/2026"
product_version: "13.0.1.1071"
---

# Supported Platforms, Applications and Workloads


|  |
| --- |
| Note |
| The information on this page is valid as of the date of the last page update. |

Veeam Backup & Replication supports backup and recovery operations for the following virtualization platforms:

* [VMware vSphere](#vm_virt)
* [Microsoft Hyper-V](#hv)
* [Azure Local (formerly Azure Stack HCI)](#hv)
* [Nutanix AHV](#ahv_platform_short)
* [Proxmox VE](#proxmox_platform_short)
* [Scale Computing HyperCore](#sch_platform)
* [Oracle Linux Virtualization Manager](#rhv_platform_short)
* [Red Hat Virtualization](#rhv_platform_short)

Veeam Backup & Replication also supports backup and recovery for the following applications and workloads:

* [Applications](#guest):

* [Application-aware image processing and Veeam Explorers](#application_aware_processing_explorers)
* [Veeam Plug-Ins for Enterprise Applications](#enterprise_applications)
* [MongoDB Backup](#mongo)
* [Microsoft Entra ID Plug-In for Veeam Backup & Replication](#entra_id)

* [Unstructured data](#nas):

* [Object storage repositories](#nas_object_storage)
* [Files shares](#nas_file_shares)
* [File servers](#nas_file_servers)
* [Enterprise NAS systems](#nas_systems)

* [Physical and cloud machines](#agents):

* [Microsoft Windows](agents_system_requirements_windows.md)
* [Linux](agents_system_requirements_linux.md)
* [Unix](agents_system_requirements_unix.md)
* [Mac](agents_system_requirements_mac.md)

* [Operating systems for Universal CDP](#uni)

VMware vSphere Platform

VMware vSphere Virtual Infrastructure

Veeam Backup & Replication supports the following VMware vSphere platforms.

| Specification | Requirement |
| --- | --- |
| Platform | * vSphere 9.01 * vSphere 8.x * vSphere 7.x * VMware Cloud Foundation (VCF)   This platform is supported as individual VMware software components. VMware components listed on this page can be part of VCF. For the information on the correspondence of VMware components to the VCF version, see [this VMware KB article](https://kb.vmware.com/s/article/52520).   * Google Cloud VMware Engine (GCVE)   For more information on GCVE support, see [this Veeam KB article](https://www.veeam.com/kb3178).   * IBM Cloud for VMware Solutions   For more information on IBM Cloud for VMware Solutions support, see [this Veeam KB article](https://www.veeam.com/kb4006).   * Microsoft Azure VMware Solution (AVS)   For more information on AVS support, see [this Veeam KB article](https://www.veeam.com/kb4012).   * Oracle Cloud VMware Solution   For more information on Oracle Cloud VMware Solutions support, see [this Veeam KB article](https://www.veeam.com/kb4007).   * VMware Cloud on AWS   For more information on VMware Cloud on AWS support, see [this Veeam KB article](https://www.veeam.com/kb2414).   * VMware Cloud on Dell   1 Backup and restore of 4Kn drives is not supported. |
| Hypervisor | * vSphere 9.0  * ESXi 8.x * ESXi 7.x   Free ESXi is not supported. Veeam Backup & Replication leverages vSphere and vStorage APIs that are disabled by VMware in free ESXi. |
| Management Server | * vCenter Server or vCenter Server Appliance 9.0 (optional) * vCenter Server or vCenter Server Appliance 8.x (optional) * vCenter Server or vCenter Server Appliance 7.x (optional) |

Veeam Continuous Data Protection (CDP)

The following infrastructure requirements apply only when you protect VMs with Continuous Data Protection (CDP):

* VMware vSphere edition must be VMware vSphere Essentials Kits editions or higher.

* vCenter Server is required. Standalone ESXi hosts are not supported.
* Minimum 16GB RAM is required for source and target ESXi hosts.

* All hosts in a cluster must be of the same major version. For example, 7.x or 8.x (7.0.0, or 7.0.2, or a combination of 7.0.0 and 7.0.2 is supported).
* You can replicate data between vCenter Servers of different versions. However, if you replicate data within one vCenter Server, and this vCenter Server includes hosts of different versions (8 and 7), your CDP policy may fail. In this case, go to the vSphere Client and delete the Veeam CDP Replication VM storage policy applied to each VM included in the CDP policy. For more information on how to delete a VM storage policy, see [VMware Docs](https://knowledge.broadcom.com/external/article/375858/deleting-a-virtual-machine-storage-polic.html). Then, in the Veeam Backup & Replication console, relaunch the CDP policy.

* The maximum number of disks per ESXi host is 500.

* Backup server, CDP proxies, vCenter Server and ESXi hosts must be able to resolve each other DNS names.
* VMware Cloud on AWS is not supported.

For more information on Veeam CDP, its requirements and limitations, see [Continuous Data Protection (CDP)](cdp_replication.md).

VMware vSphere VMs

| Specification | Requirement |
| --- | --- |
| Virtual Hardware | * All types and versions of virtual hardware are supported, including 62 TB VMDK. * Virtual machines with virtual NVDIMM devices, with virtual disks engaged in SCSI bus sharing or residing on PMem datastores are not supported for VM backup, because VMware does not support snapshotting such VMs. To protect such VMs, use Veeam Agent backup. * RDM virtual disks in physical mode, independent disks, and disks connected through in-guest iSCSI initiator are not supported for VM backup, and are skipped from processing automatically. If backup of these disks is required, use Veeam Agent backup.   Network shares and mount points targeted to 3rd party storage devices are also skipped as these volumes/disks are not visible in the VM configuration file.  RDM virtual disks in virtual mode are supported to create backups based on VMware Changed Block Tracking technology, although there are some restrictions on the virtual disk restore operation. To learn more about them, see [Restoring Virtual Disks](disk_restore_before_you_begin.md). |
| OS | * All operating systems supported by VMware. Guest processing is supported for OS versions released before the [Veeam Backup & Replication build release date](https://www.veeam.com/kb2680).  * Guest processing (which includes application-aware processing and indexing) is supported for the following Microsoft Windows operating systems except Nano Server:  * Microsoft Windows Server 2012 R2 SP1 or later * Microsoft Windows 10 22H2 for GA channel or later * Microsoft Windows 10 1507 for LTSB/LTSC channels or later * Microsoft Windows 11 22H2 or later.  * Guest processing (which includes application-aware processing and indexing) is supported for 64-bit versions of the following Linux operating systems:  * Alma Linux 8.10 and 9.4 * Debian 11.0 to 13.1 * Oracle Linux 7 (UEK 3) to 9.6 (UEK 8) * Oracle Linux 7 to 9.6 (UEK/RHCK) * RHEL 8.4 to 10 * Rocky Linux 8.10, 9.4 and 9.6 * SLES 12 SP5 or later, 15 SP3 or later * Ubuntu: 16.04 LTS, 18.04 LTS, 20.04 LTS, 22.04 LTS, 24.04 LTS |
| Software | * For Linux operating systems, GLIBC 2.16 or later. GLIBC is used for the following operations: application-aware processing, file-level restore to Linux guest OS, installing persistent agent components, and adding VM as a managed server. * VMware Tools (optional, recommended). VMware Tools are required for the following operations: application-aware processing, file-level restore from Microsoft Windows guest OS, and SureBackup testing functions. * Open VM Tools (OVT, optional). Open VM Tools are a set of services and modules used by VMware for interaction with VMs running Linux or other VMware supported Unix-like guest operating systems. * All latest OS service packs and patches (required for application-aware processing). |

Guest OS File Restore

File-level restore is supported for the following file systems, including Microsoft Windows Logical Disk Manager (LDM) dynamic disks and Linux Logical Volume Manager (LVM):

| OS | Supported File Systems |
| --- | --- |
| Microsoft Windows | * FAT, FAT32 * NTFS * ReFS   Windows file-level restore to original location is supported for the following Microsoft Windows operating systems except Nano Server:   * Microsoft Windows Server 2012 R2 SP1 or later * Microsoft Windows 10 22H2 for GA channel or later * Microsoft Windows 10 1507 for LTSB/LTSC channels or later * Microsoft Windows 11 22H2 or later. |
| Linux | * ext2, ext3, ext4 * ReiserFS * JFS * XFS * Btrfs * NTFS   DRBD (Distributed Replicated Block Devices) are not supported. |
| BSD | UFS, UFS2 |
| Mac | HFS, HFS+ (volumes up to 2 TB) |
| OpenText OES (formerly Micro Focus OES) | NSS  AD-enabled NSS volumes on Open Enterprise Server 2015 are supported. Besides restore of standard file and folder permissions, restore of NSS trustee rights on files and folders is supported.  File-level restore is supported for the following OSes:   * Open Enterprise Server (OES) versions 2015(SP1), 2018(SP1-SP3). Versions 2023, 24.1, 24.4 and 25.4 are supported with limitations. For more information, see [this Veeam KB article](https://www.veeam.com/kb4492). * NetWare 6.5 (only [restore to a new location](guest_restore_save.md#new) is supported) |
| Solaris | * UFS * ZFS (except any pool versions of Oracle Solaris)   The helper appliance uses module ZFSonLinux version 2.1.5. For this reason, Veeam Backup & Replication supports only those versions of pools and features that are available in ZFSonLinux version 2.1.5. |

For other requirements and limitations of guest OS file restore, see [Requirements and Limitations](guest_restore_before_you_begin.md).

VMware Cloud Director

| Specification | Requirement |
| --- | --- |
| VMware Cloud Director | VMware Cloud Director 10.4 to 10.6 |

Hyper-V Platform

Hyper-V Virtual Infrastructure

Veeam Backup & Replication provides support for the following versions of the Microsoft Hyper-V platform.

| Specification | Requirement |
| --- | --- |
| Platform | * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Azure Stack HCI OS   For the supported versions, see [this Veeam KB article](https://www.veeam.com/kb4047).   * Microsoft Windows 111 * Microsoft Windows 101 |
| Hypervisor | * Windows Server Hyper-V 2025 * Windows Server Hyper-V 2022 * Windows Server Hyper-V 2019 * Windows Server Hyper-V 2016 * Azure Local (formerly Azure Stack HCI) * Microsoft Hyper-V Server (free hypervisor) is supported   Server Core installations are fully supported.  Microsoft Nano Server with Hyper-V role installed cannot be [added to the backup infrastructure as a managed server](setup_add_server.md) and no role can be assigned to it. However, you can back up and replicate such servers, but application-aware processing is not supported for them.  Note that you must keep your servers up-to-date. |
| Management Server (optional) | * Microsoft PowerShell Engine 2.0 or later (optional, enables networkless guest processing) * Microsoft System Center Virtual Machine Manager 2025 * Microsoft System Center Virtual Machine Manager 2022 * Microsoft System Center Virtual Machine Manager 2019 * Microsoft System Center Virtual Machine Manager 1807 * Microsoft System Center Virtual Machine Manager 1801 * Microsoft System Center Virtual Machine Manager 2016 |

1 Windows 10/11 is supported only as a target for Instant Recovery and as a host on which a [virtual lab](virtual_lab.md) for SureBackup jobs can be created.

Hyper-V VMs

| Specification | Requirement |
| --- | --- |
| Hardware | * Supported virtual hardware versions are 5.0 to 12.0 (valid for Hyper-V 2016 to 2025). * Both Generation 1 and 2 virtual machines are supported, including 64 TB VHDX disks. * Pass-through virtual disks and guest disks connected through in-guest FC or iSCSI initiators are not supported for VM backup. VMs with pass-through disks cannot be snapshotted, which prevents snapshot-based backup. In-guest connected disks are skipped from processing automatically. If backup of these VMs/disks is required, use Veeam Agent backup. * [For Hyper-V Server 1803 or later] Backup of VMs with VMPmemController is not supported. * [For Hyper-V 2016 and later] Veeam Backup & Replication does not support processing of VMs with shared VHDX disks. You must change the disk format to VHD Set (VHDS). * [For Hyper-V 2016 and later] VMs with pass-through virtual disks cannot be processed due to Hyper-V 2016 checkpoints limitation. * [For Hyper-V 2012 R2] Veeam Backup & Replication backs up shared VHDX disks in a crash-consistent state. * [For Hyper-V 2012 R2 and earlier] Backup and replication of VMs whose data resides on a Hyper-V host volume of 64 TB and larger is not supported. |
| OS | All operating systems supported by Hyper-V. Guest processing is supported for OS versions released before the [Veeam Backup & Replication build release date](https://www.veeam.com/kb2680).   * For Microsoft Windows OSes, guest processing (which includes application-aware processing and indexing) is supported for all OSes supported by Hyper-V. * For Linux OSes, guest processing is supported for the [same Linux OSes as for the VMware vSphere platform](#lin_guest). This excludes any OSes that Hyper-V does not support.   Note: You can back up VMs of Hyper-V clusters in rolling upgrade. However, Veeam Backup & Replication does not use the [Resilient Changed Tracking](changed_block_tracking_hv.md#rct) mechanism in such scenario. To perform backup with RCT enabled, make sure your Microsoft Hyper-V environment meets [these requirements](changed_block_tracking.md#reqs). It is recommended to complete the rolling upgrade within four weeks. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/windows-server/failover-clustering/cluster-operating-system-rolling-upgrade). |
| Software | Hyper-V integration components (optional, required for application-aware processing). |

Consider the following:

* [For Microsoft Windows 2003 and Nano Server] Application-aware processing is not supported due to the absence of VSS framework.
* [For Hyper-V 2016 and later] Application-aware processing for Microsoft Windows VMs with volumes larger than 64 TB is not supported, because Veeam Backup & Replication uses the Microsoft Software Shadow Copy Provider to create a volume shadow copy during the backup or replication. For more information, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/2967756/usability-limit-for-volume-shadow-copy-service-vss-in-windows).

* [For Hyper-V 2016 and later] Veeam Backup & Replication cannot interact with the guest OS of a shielded VM and get information about its OS, IP address and so on. For this reason, the following operations are not supported for shielded VMs:

+ Application-aware image processing
+ Restore of VM guest OS files to the original location
+ Restore of application items to the original location

* [For Hyper-V 2016 and later] Shielded VMs can run only on trusted hosts guarded with the Host Guardian Service. Consider that when selecting a target host for VM replication or VM restore. If the target host is not guarded with the same Host Guardian Service as the source host, you will not be able to power on the replicated or restored VM.
* The two previous limitations also apply to Generation 1 of Microsoft Hyper-V VMs that use Key Storage Drive. For more information about Key Storage Drive, see [Microsoft Docs](https://technet.microsoft.com/en-us/windows-server-docs/compute/hyper-v/learn-more/Generation-1-virtual-machine-security-settings-for-Hyper-V).

Guest OS File Restore

File-level restore is supported for the following file systems, including Microsoft Windows LDM dynamic disks and Linux LVM:

| OS | Supported File Systems |
| --- | --- |
| Microsoft Windows | * FAT, FAT32 * NTFS * ReFS   Windows file-level restore to original location is supported for the following Microsoft Windows operating systems except Nano Server:   * Microsoft Windows Server 2012 R2 SP1 or later * Microsoft Windows 10 22H2 for GA channel or later * Microsoft Windows 10 1507 for LTSB/LTSC channels or later * Microsoft Windows 11 22H2 or later. |
| Linux | * ext2, ext3, ext4 * ReiserFS * JFS * XFS * Btrfs   DRBD (Distributed Replicated Block Devices) are not supported. |
| BSD | UFS, UFS2 |
| Mac | HFS, HFS+ (volumes up to 2 TB) |
| Solaris | * UFS * ZFS (except any pool versions of Oracle Solaris)   The helper appliance uses module ZFSonLinux version 0.7.0. For this reason, Veeam Backup & Replication supports only those versions of pools and features that are available in ZFSonLinux version 0.7.0. |

For other requirements and limitations of guest OS file restore, see [Requirements and Limitations](guest_restore_before_you_begin.md).

Nutanix AHV Platform

Veeam Plug-In for Nutanix AHV is a solution developed for protection and disaster recovery tasks for the Nutanix AHV environment. For more information on Veeam Plug-In for Nutanix AHV features and system requirements, see the [Veeam Plug-In for Nutanix AHV User Guide](https://helpcenter.veeam.com/docs/vbahv/userguide/system_requirements.html?ver=9).

Proxmox VE Platform

Veeam Plug-In for Proxmox VE is a solution developed for protection and disaster recovery tasks for Proxmox Virtual Environment (Proxmox VE). For more information on Veeam Plug-In for Proxmox VE features and system requirements, see the [Veeam Plug-In for Proxmox VE User Guide](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/system_requirements.html?ver=3).

Scale Computing HyperCore Platform

Veeam Plug-In for Scale Computing HyperCore is a solution developed for protection and disaster recovery tasks for Scale Computing HyperCore. For more information on Veeam Plug-In for Scale Computing HyperCore features and system requirements, see the [Veeam Plug-In for Scale Computing HyperCore User Guide](https://helpcenter.veeam.com/docs/vpsch/userguide/system_requirements.html?ver=2).

Oracle Linux Virtualization Manager and Red Hat Virtualization Platforms

Veeam Backup for Oracle Linux Virtualization Manager and Red Hat Virtualization is a solution developed for protection and disaster recovery tasks for oVirt KVM environments. For more information on Veeam Backup for OLVM and RHV features and system requirements, see the [Veeam Backup for OLVM and RHV User Guide](https://helpcenter.veeam.com/docs/vbrhv/userguide/system_requirements.html?ver=7).

Applications

Application-Aware Image Processing and Veeam Explorers

You can create transactionally-consistent backups or replicas of VMs that run the following applications.

| Application | Requirement |
| --- | --- |
| Microsoft Active Directory | Veeam Backup & Replication supports backup of domain controllers running on the following operating systems:  * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2   Minimum supported domain and forest functional level is Windows 2012 R2. |
| Microsoft Exchange | Veeam Backup & Replication supports backup of the following Microsoft Exchange versions:  * Microsoft Exchange Server Subscription Edition  * Microsoft Exchange Server 2019 * Microsoft Exchange Server 2016 |
| Microsoft SharePoint | Veeam Backup & Replication supports backup of the following Microsoft SharePoint versions:  * Microsoft SharePoint Server Subscription Edition * Microsoft SharePoint Server 2019  * Microsoft SharePoint Server 2016   All editions are supported (Subscription, Foundation, Standard, Enterprise).  Restore of Microsoft SharePoint data may require an available staging Microsoft SQL Server. To learn how to configure this server, see [Staging SQL Server Settings](https://helpcenter.veeam.com/docs/vbr/explorers/vesp_configuring_sql_settings.html?ver=13). |
| Microsoft SQL Server | Veeam Backup & Replication supports backup of the following Microsoft SQL Server versions:  * Microsoft SQL Server 2025 (only for Windows) * Microsoft SQL Server 2022 (only for Windows) * Microsoft SQL Server 2019 (only for Windows) * Microsoft SQL Server 2017 (only for Windows) * Microsoft SQL Server 2016 SP2 * Microsoft SQL Server 2014 SP3 * Microsoft SQL Server 2012 SP4   All editions of Microsoft SQL Server except LocalDB are supported.  The database whose logs you want to back up must use the Full or Bulk-logged recovery model. In this case, all changes of the Microsoft SQL Server state will be written to transaction logs, and you will be able to replay transaction logs to restore the Microsoft SQL Server. You can use the Microsoft SQL Server Management Studio to switch to one of these models. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/recovery-models-sql-server?view=sql-server-2017).  Restore of Microsoft SQL Server data may require an available staging Microsoft SQL Server. To learn how to configure this server, see [Configuring Staging SQL Server](vesql_configure_staging.md). |
| Oracle on Windows OS | Veeam Backup & Replication supports backup of Oracle Database running on the following Microsoft Windows operating systems:  * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  Veeam Backup & Replication supports backup of the following Oracle Database versions on Microsoft Windows machines:  * Oracle Database 21c * Oracle Database 19c * Oracle Database 18c * Oracle Database 12c Release 2 * Oracle Database 12c Release 1 * Oracle Database 11g Release 2 |
| Oracle on Linux OS | Veeam Backup & Replication supports backup of Oracle Database running on the following Linux distributions:  * RHEL 8.4 to 9.4 * SLES 12 SP5, 15 SP3 or later * Oracle Linux 7 (UEK3) to 9 (UEK R7) * Oracle Linux 7 to 9 (RHCK)  Veeam Backup & Replication supports backup of the following Oracle Database versions on Linux machines:  * Oracle Database 21c * Oracle Database 19c * Oracle Database 18c * Oracle Database 12c Release 2 * Oracle Database 12c Release 1 * Oracle Database 11g Release 2 |
| Oracle Database configuration | Consider the following:   * Automatic Storage Management (ASM) is supported for Oracle 11g and later; requires ASMlib present.  * Oracle Real Application Clusters (RAC) are not supported within the image-level backup functionality. Use Veeam Plug-In for Oracle RMAN. For details, see [Veeam Plug-In for Oracle RMAN](rman_plugin.md). * Oracle Database Express Edition (XE) is supported for Windows-based machines only.  * [For Microsoft Windows-based Oracle machines] Configurations with different versions of Oracle Database deployed on the same server are not supported.  * To create Oracle database backups, all Oracle servers that use Data Guard must be added to the backup job. * You can use Veeam Plug-In for Oracle RMAN to integrate RMAN with Veeam Backup & Replication repositories. For details, see the [Veeam Plug-In for Oracle RMAN](rman_plugin.md) section. |
| PostgreSQL | Veeam Backup & Replication supports backup of the following PostgreSQL versions on Linux machines:  * PostgreSQL 18 * PostgreSQL 17 * PostgreSQL 16 * PostgreSQL 15 * PostgreSQL 14 * PostgreSQL 13  Veeam Backup & Replication does not support backup of PostgreSQL clusters. |

|  |
| --- |
| Note |
| Consider that 32-bit Oracle running on 64-bit operating systems and Oracle Express Edition (XE) on Linux are not supported. |

Veeam Plug-Ins for Enterprise Applications

Veeam Plug-Ins for Enterprise Applications further enhance Veeam Backup & Replication by enabling transactionally consistent backups of the following databases and enterprise applications:

|  |
| --- |
| Tip |
| For more information on Veeam Plug-Ins for Enterprise Applications, see [Databases and Enterprise Applications](protect_applications.md). |

| Application | Veeam Product | Requirement |
| --- | --- | --- |
| Oracle database | [Veeam Plug-In for Oracle RMAN](rman_plugin.md) | Veeam Plug-In for Oracle RMAN supports Standard and Enterprise Editions of the following Oracle Database versions:  * Oracle Database 23ai * Oracle Database 21c * Oracle Database 19c * Oracle Database 18c * Oracle Database 12c * Oracle Database 11g Release 2  Notes:   * Oracle Express Edition (XE) is not supported. * Oracle databases residing in OS-level containerized environments (for example: Docker, Podman) are not supported. * Support for Oracle Database 23ai is limited to virtual machines in cloud deployments (for example: Oracle Cloud Infrastructure, Oracle Exadata Cloud) and Oracle Engineered Systems (for example: Oracle Exadata, Oracle Database Appliance). |
| SAP HANA database | [Veeam Plug-In for SAP HANA](sap_hana_plugin.md) | Veeam Plug-In for SAP HANA supports SAP HANA 2.0: SPS 02, SPS 03, SPS 04, SPS 05, SPS 06, SPS 07, SPS 08.  Notes:   * Only Backint version 1.0 is supported. * SAP HANA Express Edition is not supported. * To check whether an OS version is compatible with the SAP HANA release you want to use, see the [SAP HANA Administration Guide](https://launchpad.support.sap.com/#/notes/2235581) (requires an SAP ID). |
| Oracle database and SAP software | [Veeam Plug-In for SAP on Oracle](sap_orcl_plugin.md) | Veeam Plug-In for SAP on Oracle supports Standard and Enterprise Editions of the following Oracle Database versions:   * 19c * 18c * 12c * 11g Release 2   Note: Oracle Express Edition (XE) and Oracle Real Application Cluster (RAC) environment are not supported.  Veeam Plug-In for SAP on Oracle supports BR\*Tools version 7.20, Patch 42 or later. |
| SAP MaxDB database | [Veeam Plug-In for SAP MaxDB](plugins_sap_maxdb.md) | Veeam Plug-In for SAP MaxDB supports SAP MaxDB 7.9.11. |
| Microsoft SQL Server | [Veeam Plug-In for Microsoft SQL Server](mssql_plugin.md) | Veeam Plug-In for Microsoft SQL Server supports the Standard, Developer, Web and Enterprise editions of the following Microsoft SQL Server versions:   * Microsoft SQL Server 2025 * Microsoft SQL Server 2022 * Microsoft SQL Server 2019 * Microsoft SQL Server 2017 * Microsoft SQL Server 2016 * Microsoft SQL Server 2014 SP3   Notes:   * Standalone Microsoft SQL Servers are supported. * SQL Server Express edition is not supported. * Windows Server Failover Clusters are supported, both with shared disks and Cluster Shared Volumes (CSV).  * Always On availability groups, Always On clusterless availability groups and Always On failover cluster instances are supported. Contained availability groups and distributed availability groups are not supported.  Veeam Plug-In Toolbar requires Microsoft SQL Server Management Studio 21.  Note: Remote connections from Microsoft SQL Server Management Studio are not supported. |
| IBM Db2 | [Veeam Plug-In for IBM Db2](db2_plugin.md) | Veeam Plug-In supports the following configurations of IBM Db2:   * Versions: 10.5, 11.1, 11.5, 12.1 * Editions: Standard, Advanced * Environments: standalone servers, high availability disaster recovery (HADR), failover clusters   In case of HADR and failover clusters, Veeam Plug-In supports the following cluster management software: TSA, Pacemaker for Linux OSes, PowerHA for IBM AIX. |

MongoDB Backup

| Application | Veeam Product | Requirement |
| --- | --- | --- |
| MongoDB | [MongoDB Backup](mongo_backup.md) | Veeam Backup & Replication supports the following solutions for MongoDB 7.0, 8.0:   * MongoDB Community Edition * MongoDB Enterprise Advanced * Percona Server for MongoDB   Depending on the protection group configuration, Veeam Backup & Replication connects to MongoDB using MongoDB Wire Protocol and one of the following methods:   * SCRAM * SCRAM with TLS * x509 certificate with TLS   For details, see [Authentication Against Replica Set](mongo_auth_methods.md).  Notes:   * Standalone servers with MongoDB deployments are not supported. * MongoDB sharded clusters are not supported. |

Microsoft Entra ID Plug-In for Veeam Backup & Replication

Veeam Backup for Microsoft Entra ID is a solution developed for protection and disaster recovery tasks for Microsoft Entra ID.

For more information, see the [User Guide for Microsoft Entra ID](https://helpcenter.veeam.com/docs/vbr/entraid/overview.html?ver=13).

Microsoft Entra ID Backup Repository

* PostgreSQL 17.x
* PostgreSQL 16.x
* PostgreSQL 15.x
* PostgreSQL 14.x

Unstructured Data

Object Storage Repositories

The following object storage sources are supported:

* Amazon S3 object storage
* Microsoft Azure Blob storage
* Azure Data Lake Gen2 storage (HNS)
* S3-compatible object storage

File Shares

The following file share sources are supported:

* SMB version 1.x, 2.x or 3.x.
* NFS protocol version 3 or 4.1.

Requirements and Limitations for File Shares

Consider the following requirements and limitations for file shares:

* Only 64-bit versions of operating systems are supported for managed Microsoft Windows or Linux server file share.
* Backup of file shares on Linux hosts [added with single use credentials](hardened_repository.md) is not supported.
* NFS file share must run NFS protocol version 3 or 4.1. Parallel NFS (pNFS) is not supported.
* Network shares and files on them targeted to 3rd party storage devices may have difficulties being restored, or may not be restored at all. Such shares/files often rely upon specific software/OS filters to be recalled from the alternate storage location, which is not available when performing a file share data recovery. See your software vendor documentation to learn how to back up such files.
* Anonymous or AD/Kerberos authentication is not supported for access to file shares through NFS.

In NFS settings of the source file share, you must explicitly specify what servers will have access to the file share.

* SMB file share must run on SMB version 1.x, 2.x or 3.x.
* To support the VSS for SMB File Shares feature, make sure that requirements listed in [this Veeam KB article](https://www.veeam.com/kb3099) are met.
* To correctly back up SACL (Ownership) files and folders from the SMB file share and restore them:

1. When you are [specifying access settings for the SMB file share](file_share_backup_smb_share_path_credentials.md), select the This share requires access credentials check box.
2. Make sure that the account you use to [Unstructured Data Backup](unstructured_data_backup.md) access the file share is either added to the Backup Operators group or has the SeBackupPrivilege and SeRestorePrivilege privileges in Windows Server on the file share.

Files Servers

The following Microsoft Windows operating systems are supported:

* Microsoft Windows Server 2025
* Microsoft Windows Server 2022
* Microsoft Windows Server 2019
* Microsoft Windows Server 2016
* Microsoft Windows 11 (versions 22H2, 23H2, 24H2)
* Microsoft Windows 10 22H2
* Microsoft Windows 10 LTSC 2021

64-bit versions of the following Linux distributions are supported:

* Debian 11.0 to 12.11
* Oracle Linux 7 to 10
* RHEL 8.6 to 9.6
* Rocky Linux 9.4 to 9.6
* SLES 12 SP5, 15 SP3
* Ubuntu 20.04 LTS, 22.04 LTS, 24.04 LTS

Enterprise NAS Systems

The following enterprise NAS systems are supported:

* NetApp FAS/AFF/ASA, FlexArray (V-Series), ONTAP Edge/Select/Cloud VSA with ONTAP cluster-mode versions from 9.10 up to 9.17.1
* Lenovo ThinkSystem DM/DG Series with ONTAP cluster-mode versions 9.10 to 9.17.1
* Fujitsu ETERNUS HX/AX with ONTAP cluster-mode versions 9.10 to 9.17.1
* Dell PowerScale (formerly Isilon) with OneFS versions 8.1.2 to 9.11
* Nutanix Files Storage versions 3.8.1.3 to 5.2

Physical and Cloud Machines

To back up physical, virtual, or cloud-based machines machines running Microsoft Windows, Linux, Unix or macOS operating systems, Veeam Backup & Replication allows remote deployment and central administration of Veeam Agents.

For more information on system requirements for Veeam Agent management components, see the followings sections:

* [System Requirements for Microsoft Windows Computers](agents_system_requirements_windows.md)
* [System Requirements for Linux Computers](agents_system_requirements_linux.md)
* [System Requirements for Unix Computers](agents_system_requirements_unix.md)
* [System Requirements for Mac Computers](agents_system_requirements_mac.md)

Operating Systems for Universal CDP

A workload that you plan to protect with Universal CDP must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x64.  Memory: 2 GB RAM or more. Memory consumption varies depending on the number and size of processed disks.  System firmware: BIOS or UEFI. |
| OS | 64-bit versions of the following operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 |
| File System | Microsoft Windows RAW, FAT, FAT32, exFAT, NTFS and ReFS file systems are supported. |

For the full list of limitations and considerations, see [Universal CDP - Considerations and Limitations](uni_cdp_considerations.md).

Network

Consider the following requirements and limitations:

* Names of port groups/segments/networks must be unique.

* [For VMware vSphere] VMware NSX-T 2.3 or later is supported with N-VDS for VMware vSphere and VMware Cloud on AWS/Dell.
* [For VMware vSphere] VMware NSX-T 3.0 or later is supported with VDS for VMware vSphere and VMware Cloud on AWS/Dell.
* [For VMware vSphere] VMware NSX-V is supported (see details on the support of vSphere and VMware Cloud version in [VMware vSphere Virtual Infrastructure](#vm_virt_infrastructure)).


