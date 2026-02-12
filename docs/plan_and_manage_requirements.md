---
title: "System Requirements"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plan_and_manage_requirements.html"
last_updated: "2/10/2026"
product_version: "13.0.1.1071"
---

# System Requirements


Make sure that components in the plug-in management infrastructure meet system requirements listed in this section.

Veeam Backup Server

For details on system requirements for the Veeam backup server and other Veeam Backup & Replication components, see [System Requirements](system_requirements.md).

Computer with Veeam Plug-In for Oracle RMAN

A computer with databases you want to protect using Veeam Plug-In for Oracle RMAN must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| OS | Veeam Plug-In for Oracle RMAN is supported for the following Microsoft Windows versions:   * Microsoft Windows Server 2025  * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2  Veeam Plug-In for Oracle RMAN is supported for the following x86\_64 versions of Linux distributions:   * SUSE Linux Enterprise Server 12 SP5, 15 SP3 and SP7 (x86 and x86\_64) * RHEL 8.4 – 9.x, 10.0 including Extended Update Support Add-On * Oracle Linux 7 – 9.x * CentOS 6.4 – 8.x: For non-production environments, as it is not officially supported by Oracle for their databases.  Note: Veeam Plug-In for Oracle RMAN in managed operation mode is not supported for Oracle Solaris and IBM AIX. |
| Software | [For Microsoft Windows computers] Microsoft .NET Framework 4.6 is included in the Veeam Plug-In for Oracle RMAN Redistributable. During the deployment process, Veeam Backup & Replication checks whether Microsoft .NET Framework 4.6 is available on the target computer. If Microsoft .NET Framework 4.6 is missing, Veeam Backup & Replication will install missing software automatically. |
| Oracle database | Veeam Plug-In for Oracle RMAN supports Standard and Enterprise Editions of the following Oracle Database versions:   * 23ai * 21c * 19c * 18c * 12c * 11g Release 2  The Oracle database configuration must meet the following requirements:   * Oracle database must be in the OPEN state. * Oracle database must work in the ARCHIVELOG mode.   Notes:   * Oracle Express Edition (XE) is not supported. * Oracle databases residing in OS-level containerized environments (for example: Docker, Podman) are not supported. * Support for Oracle database 23ai is limited to virtual machines in cloud deployments (for example: Oracle Cloud Infrastructure, Oracle Exadata Cloud) and Oracle Engineered Systems (for example: Oracle Exadata, Oracle Database Appliance). |
| Oracle RMAN features | Veeam Plug-In for Oracle RMAN supports the following Oracle RMAN features:   * Veeam Plug-In will be registered as an SBT\_TAPE device. All Oracle RMAN functionality that is supported with the SBT\_TAPE device type will work. For example, Automatic Storage Management (Oracle ASM) and Container DBs (CDBs). * Veeam Plug-In supports Oracle Real Application Clusters (Oracle RAC). Other cluster databases are not supported. |

Computer with Veeam Plug-In for SAP HANA

A computer with databases you want to protect using Veeam Plug-In for SAP HANA must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| OS | Veeam Plug-In for SAP HANA supports 64-bit versions of the following distributions:   * SLES 15: SP3, SP4, SP5, SP6, SP7 * SLES for SAP Applications 15: SP3, SP4, SP5, SP6, SP7 * SLES 12 SP5  * SLES for SAP Applications 12 SP5 * RHEL 9 for SAP HANA: 9.0, 9.2, 9.4, 9.6 * RHEL 8 for SAP HANA: 8.4, 8.6, 8.8, 8.10 * RHEL 9 for SAP Solutions: 9.0, 9.2, 9.4, 9.6 * RHEL 8 for SAP Solutions: 8.4, 8.6, 8.8, 8.10  Note: Veeam Plug-In for SAP HANA in managed operation mode is not supported for Linux on Power. |
| SAP HANA database | Veeam Plug-In for SAP HANA supports SAP HANA 2.0: SPS 02, SPS 03, SPS 04, SPS 05, SPS 06, SPS 07, SPS 08.  Notes:   * Only with Backint version 1.0 is supported. * SAP HANA Express Edition is not supported. * To check whether an OS version is compatible with the SAP HANA release you want to use, see the [SAP HANA Administration Guide](https://launchpad.support.sap.com/#/notes/2235581) (requires an SAP ID). |

Computer with Veeam Plug-In for SAP on Oracle

A computer with databases you want to protect using Veeam Plug-In for SAP on Oracle must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| OS | Veeam Plug-In for SAP on Oracle is supported for the following distributions:   * SUSE Linux Enterprise Server versions 12 SP5, 15 SP3 (x86\_64) * RHEL for SAP Applications versions 8.4, 9 (x86\_64) * Oracle Linux versions 7, 8 |
| Oracle database | Veeam Plug-In for SAP on Oracle supports Standard and Enterprise Editions of the following Oracle Database versions:   * 19c * 18c * 12c * 11g Release 2   Note: Oracle Express Edition (XE) and Oracle Real Application Cluster (RAC) environment are not supported. |
| SAP software | Veeam Plug-In for SAP on Oracle supports BR\*Tools version 7.20, Patch 42 or later.  Note: In the managed operation mode, Veeam Plug-In for SAP on Oracle does not support SAP Java systems. |

Computer with Veeam Plug-In for Microsoft SQL Server

A computer with databases you want to protect using Veeam Plug-In for Microsoft SQL Server must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| OS | Veeam Plug-In for Microsoft SQL Server supports 64-bit versions of the following distributions:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2   Note: Server Core installations of Microsoft Windows Server OSes are not supported. |
| Microsoft SQL Server | Veeam Plug-In for Microsoft SQL Server supports the Standard, Developer, Web and Enterprise editions of the following Microsoft SQL Server versions:   * Microsoft SQL Server 2025 * Microsoft SQL Server 2022 * Microsoft SQL Server 2019 * Microsoft SQL Server 2017 * Microsoft SQL Server 2016 * Microsoft SQL Server 2014 SP3  Notes:   * Standalone Microsoft SQL Servers are supported. * SQL Server Express edition is not supported. * Windows Server Failover Clusters are supported, both with shared disks and Cluster Shared Volumes (CSV).  * Always On availability groups, Always On clusterless availability groups and Always On failover cluster instances are supported. Contained availability groups and distributed availability groups are not supported. |

Veeam Backup & Replication

Periodically, Veeam releases a new version of Veeam Backup & Replication that contains new features and bug fixes. The release package also contains a new version of Veeam Plug-Ins.

Veeam Backup & Replication 13 supports different versions of Veeam Plug-In depending on which OS is running on the backup server:

* Veeam Backup & Replication on Linux supports management of Veeam Plug-Ins 13. Management of previous versions of Veeam Plug-Ins is not supported.
* Veeam Backup & Replication on Microsoft Windows supports management of Veeam Plug-Ins 12.3.2.4165 and later.

|  |
| --- |
| Note |
| Veeam Plug-In for Microsoft SQL Server supports the managed operation mode starting from version 13.0.1.180-1. If you have have an earlier supported version of Veeam Plug-In for Microsoft SQL Server, you must upgrade it. After that, you can start using Veeam Plug-In in the managed operation mode. For details, see [Upgrading Veeam Plug-In for Microsoft SQL Server](update_mssql_plugin.md). |

Note that Veeam Backup & Replication must be the same or later than the version of Veeam Plug-In. If you want to use the latest functionality, you must upgrade both Veeam Backup & Replication and Veeam Plug-In to the latest version. If you use an earlier Veeam Plug-In build, it may not have all the features and bug fixes introduced in your Veeam Backup & Replication version. To learn more about the Veeam Plug-In builds included in Veeam Backup & Replication installation ISO files, see [this Veeam KB article](https://www.veeam.com/kb4474).

Veeam Backup & Replication version 13 (build 13.0.1.180-1) comes with the following Veeam Plug-Ins stored in the ISO file:

* Veeam Plug-In for SAP HANA
* Veeam Plug-In for Oracle RMAN
* Veeam Plug-In for SAP on Oracle
* Veeam Plug-In for Microsoft SQL Server

Network

Veeam Plug-In must be able to establish a direct IP connection to the Veeam Backup & Replication server. Thus, Veeam Plug-In cannot work with the Veeam Backup & Replication server that is located behind the NAT gateway.


