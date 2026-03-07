---
title: "Applications"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/platform_support_applications.html"
last_updated: "3/6/2026"
product_version: "13.0.1.1071"
---

# Applications


Application-Aware Image Processing and Veeam Explorers

You can create transactionally consistent backups or replicas of machines that run the following applications:

|  |
| --- |
| Note |
| To recover application data from image-level backups or replicas created with application-aware processsing, use Veeam Explorers. For more information, see [Veeam Explorers Overview](explorers_introduction.md). |

Application-Aware Image Processing and Veeam Explorers

| Application | Requirement |
| Microsoft Active Directory | Veeam Backup & Replication supports backup and recovery of domain controllers running on the following operating systems:  * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2   Minimum supported domain and forest functional level is Windows 2012 R2. |
| Microsoft Exchange | Veeam Backup & Replication supports backup and recovery of the following Microsoft Exchange versions:  * Microsoft Exchange Server Subscription Edition  * Microsoft Exchange Server 2019 * Microsoft Exchange Server 2016 |
| Microsoft SharePoint | Veeam Backup & Replication supports backup and recovery of the following Microsoft SharePoint versions:  * Microsoft SharePoint Server Subscription Edition * Microsoft SharePoint Server 2019  * Microsoft SharePoint Server 2016   All editions are supported (Subscription, Foundation, Standard, Enterprise).  Restore of Microsoft SharePoint data may require an available staging Microsoft SQL Server. To learn how to configure this server, see [Staging SQL Server Settings](https://helpcenter.veeam.com/docs/vbr/explorers/vesp_configuring_sql_settings.html?ver=13). |
| Microsoft SQL Server | Veeam Backup & Replication supports backup and recovery of the following Microsoft SQL Server versions:  * Microsoft SQL Server 2025 (only for Windows) * Microsoft SQL Server 2022 (only for Windows) * Microsoft SQL Server 2019 (only for Windows) * Microsoft SQL Server 2017 (only for Windows) * Microsoft SQL Server 2016 SP2 * Microsoft SQL Server 2014 SP3 * Microsoft SQL Server 2012 SP4   All editions of Microsoft SQL Server except LocalDB are supported.  The database whose logs you want to back up must use the Full or Bulk-logged recovery model. In this case, all changes of the Microsoft SQL Server state will be written to transaction logs, and you will be able to replay transaction logs to restore the Microsoft SQL Server. You can use the Microsoft SQL Server Management Studio to switch to one of these models. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/recovery-models-sql-server?view=sql-server-2017).  Restore of Microsoft SQL Server data may require an available staging Microsoft SQL Server. To learn how to configure this server, see [Configuring Staging SQL Server](vesql_configure_staging.md). |
| Oracle on Windows OS | Veeam Backup & Replication supports backup and recovery of Oracle Database running on the following Microsoft Windows operating systems:  * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016  Veeam Backup & Replication supports backup and recovery of the following Oracle Database versions on Microsoft Windows machines:  * Oracle Database 21c * Oracle Database 19c * Oracle Database 18c * Oracle Database 12c Release 2 * Oracle Database 12c Release 1 * Oracle Database 11g Release 2 |
| Oracle on Linux OS | Veeam Backup & Replication supports backup and recovery of Oracle Database running on the following Linux distributions:  * RHEL 8.4 to 9.4 * SLES 12 SP5, 15 SP3 or later * Oracle Linux 7 (UEK3) to 9 (UEK R7) * Oracle Linux 7 to 9 (RHCK)  Veeam Backup & Replication supports backup and recovery of the following Oracle Database versions on Linux machines:  * Oracle Database 21c * Oracle Database 19c * Oracle Database 18c * Oracle Database 12c Release 2 * Oracle Database 12c Release 1 * Oracle Database 11g Release 2 |
| Oracle Database configuration | Consider the following:   * Automatic Storage Management (ASM) is supported for Oracle 11g and later; requires ASMlib present.  * Oracle Real Application Clusters (RAC) are not supported within the image-level backup functionality. Use Veeam Plug-In for Oracle RMAN. For details, see [Veeam Plug-In for Oracle RMAN](rman_plugin.md). * 32-bit Oracle running on 64-bit operating systems is not supported. * Oracle Database Express Edition (XE) is supported for Windows-based machines only.  * [For Microsoft Windows-based Oracle machines] Configurations with different versions of Oracle Database deployed on the same server are not supported.  * To create Oracle database backups, all Oracle servers that use Data Guard must be added to the backup job. * You can use Veeam Plug-In for Oracle RMAN to integrate RMAN with Veeam Backup & Replication repositories. For details, see the [Veeam Plug-In for Oracle RMAN](rman_plugin.md) section. |
| PostgreSQL | Veeam Backup & Replication supports backup and recovery of the following PostgreSQL versions on Linux machines:  * PostgreSQL 18 * PostgreSQL 17 * PostgreSQL 16 * PostgreSQL 15 * PostgreSQL 14 * PostgreSQL 13  Veeam Backup & Replication does not support backup and recovery of PostgreSQL clusters. |

Veeam Plug-Ins for Enterprise Applications

Veeam Plug-Ins for Enterprise Applications further enhance Veeam Backup & Replication by enabling transactionally consistent backups and recovery of the following databases and enterprise applications:

|  |
| --- |
| Tip |
| Consider the following:   * For more information on Veeam Plug-Ins for Enterprise Applications, see [Databases and Enterprise Applications](protect_applications.md). * Some Veeam Plug-Ins for Enterprise Applications support data recovery using Veeam Explorers. For more information, see [Launching Veeam Explorer from Plug-in or MongoDB Backup](launching_veeam_explorers_plugin.md). |

Veeam Plug-Ins for Enterprise Applications

| Application | Veeam Product | Requirement |
| Oracle database | [Veeam Plug-In for Oracle RMAN](rman_plugin.md) | Veeam Plug-In for Oracle RMAN supports Standard and Enterprise Editions of the following Oracle Database versions:  * Oracle Database 23ai * Oracle Database 21c * Oracle Database 19c * Oracle Database 18c * Oracle Database 12c * Oracle Database 11g Release 2  Notes:   * Oracle Express Edition (XE) is not supported. * Oracle databases residing in OS-level containerized environments (for example: Docker, Podman) are not supported. * Support for Oracle Database 23ai is limited to virtual machines in cloud deployments (for example: Oracle Cloud Infrastructure, Oracle Exadata Cloud) and Oracle Engineered Systems (for example: Oracle Exadata, Oracle Database Appliance). |
| SAP HANA database | [Veeam Plug-In for SAP HANA](sap_hana_plugin.md) | Veeam Plug-In for SAP HANA supports SAP HANA 2.0: SPS 02, SPS 03, SPS 04, SPS 05, SPS 06, SPS 07, SPS 08.  Notes:   * Only Backint version 1.0 is supported. * SAP HANA Express Edition is not supported. * To check whether an OS version is compatible with the SAP HANA release you want to use, see the [SAP HANA Administration Guide](https://launchpad.support.sap.com/#/notes/2235581) (requires an SAP ID). |
| Oracle database and SAP software | [Veeam Plug-In for SAP on Oracle](sap_orcl_plugin.md) | Veeam Plug-In for SAP on Oracle supports Standard and Enterprise Editions of the following Oracle Database versions:   * 19c * 18c * 12c * 11g Release 2   Note: Oracle Express Edition (XE) and Oracle Real Application Cluster (RAC) environment are not supported.  Veeam Plug-In for SAP on Oracle supports BR\*Tools version 7.20, Patch 42 or later. |
| SAP MaxDB database | [Veeam Plug-In for SAP MaxDB](plugins_sap_maxdb.md) | Veeam Plug-In for SAP MaxDB supports SAP MaxDB 7.9.11. |
| Microsoft SQL Server | [Veeam Plug-In for Microsoft SQL Server](mssql_plugin.md) | Veeam Plug-In for Microsoft SQL Server supports the Standard, Developer, Web and Enterprise editions of the following Microsoft SQL Server versions:   * Microsoft SQL Server 2025 * Microsoft SQL Server 2022 * Microsoft SQL Server 2019 * Microsoft SQL Server 2017 * Microsoft SQL Server 2016 * Microsoft SQL Server 2014 SP3   Notes:   * Standalone Microsoft SQL Servers are supported. * SQL Server Express edition is not supported. * Windows Server Failover Clusters are supported, both with shared disks and Cluster Shared Volumes (CSV).  * Always On availability groups, Always On clusterless availability groups and Always On failover cluster instances are supported. Contained availability groups and distributed availability groups are not supported.  Veeam Plug-In for Microsoft SQL Server Toolbar requires Microsoft SQL Server Management Studio 21.  Note: Remote connections from Microsoft SQL Server Management Studio are not supported. |
| IBM Db2 | [Veeam Plug-In for IBM Db2](db2_plugin.md) | Veeam Plug-In for IBM Db2 supports the following configurations of IBM Db2:   * Versions: 10.5, 11.1, 11.5, 12.1 * Editions: Standard, Advanced * Environments: standalone servers, high availability disaster recovery (HADR), failover clusters   In case of HADR and failover clusters, Veeam Plug-In supports the following cluster management software: TSA, Pacemaker for Linux OSes, PowerHA for IBM AIX. |

MongoDB Backup

Veeam Backup & Replication allows you to create transactionally consistent backups of MongoDB data. To recover this data, use [Veeam Explorer for MongoDB](vemdb_user_guide.md).

MongoDB Backup

| Application | Veeam Product | Requirement |
| MongoDB | [MongoDB Backup](mongo_backup.md) | Veeam Backup & Replication supports the following solutions for MongoDB 7.0, 8.0:   * MongoDB Community Edition * MongoDB Enterprise Advanced * Percona Server for MongoDB   Depending on the protection group configuration, Veeam Backup & Replication connects to MongoDB using MongoDB Wire Protocol and one of the following methods:   * SCRAM * SCRAM with TLS * x509 certificate with TLS   For details, see [Authentication Against Replica Set](mongo_auth_methods.md).  Notes:   * Standalone servers with MongoDB deployments are not supported. * MongoDB sharded clusters are not supported. |

Veeam Backup for Microsoft Entra ID

Veeam Backup for Microsoft Entra ID is a solution developed for protection and disaster recovery tasks for Microsoft Entra ID.

For more information, see the [User Guide for Microsoft Entra ID](https://helpcenter.veeam.com/docs/vbr/entraid/overview.html?ver=13).

Microsoft Entra ID Backup Repository

* PostgreSQL 17.x
* PostgreSQL 16.x
* PostgreSQL 15.x
* PostgreSQL 14.x


