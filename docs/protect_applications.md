---
title: "Databases and Enterprise Applications"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protect_applications.html"
last_updated: "1/23/2026"
product_version: "13.0.1.1071"
---

# Databases and Enterprise Applications


Veeam Backup & Replication allows you to protect data from various applications and databases, such as Microsoft Active Directory, Microsoft SQL Server, MongoDB and others. Depending on the application you want to back up and the level on which you want to create a backup, Veeam Backup & Replication suggests the following options:

* [Image-level backup with application-aware processing](#image-level)
* [Database-level backup with Veeam Plug-Ins or MongoDB Backup](#database-level)

|  | Image-Level Backup with Application-Aware Processing | Database-Level Backup with Veeam Plug-Ins or MongoDB Backup |
| --- | --- | --- |
| Microsoft Active Directory | ✓ | ✕ |
| Microsoft Exchange | ✓ | ✕ |
| Microsoft SharePoint | ✓ | ✕ |
| Microsoft SQL Server | ✓ | ✓ |
| Oracle | ✓ | ✓ |
| MySQL | ✓\* | ✕ |
| PostgreSQL | ✓ | ✕ |
| SAP HANA | ✕ | ✓ |
| SAP MaxDB | ✕ | ✓ |
| IBM Db2 | ✕ | ✓ |
| MongoDB | ✕ | ✓ |

\*Application-aware processing for machines with the MySQL database system is available only with Veeam Agent for Linux. To learn more, see [Backup of Database Systems](agents_backup_linux_dbs_processing.md).

Image-Level Backup with Application-Aware Processing

Application-aware processing is available for most platforms protected by Veeam. With the application-aware processing enabled, Veeam Backup & Replication creates image-level backups of your workload and also backs up application logs. To configure application-aware processing, you must select the Enable application-aware processing check box in the backup job settings. For more information, see guides or sections dedicated to your platform. Make sure that you configured the infrastructure as required for the platform. For example, see [VMware vSphere](vmware_vsphere.md) for VMware vSphere VMs and [Veeam Agent Backup](protect_comp.md) for physical computers and VMs.

For recovery, Veeam Backup & Replication provides recovery of workloads themselves as well as recovery of application items. For recovery, Veeam Backup & Replication uses tools called Veeam Explorers. Veeam Explorers are distributed as part of Veeam Backup & Replication, and you do not need to install them separately. You also do not need to purchase any additional license to use Veeam Explorers. For information on how to launch Veeam Explorers to restore application items, see [Launching Veeam Explorer from Image-Level Backups](restoring_veeam_explorers.md). As an alternative, you can launch Veeam Explorers as a separate tool. For more information, see the [Veeam Explorers User Guide](https://helpcenter.veeam.com/docs/vbr/explorers/explorers_introduction.html?ver=13).

Database-Level Backup with Veeam Plug-Ins or MongoDB Backup

Backup solutions for enterprise applications (Veeam Plug-Ins and MongoDB Backup) allow you to create transactionally-consistent backups of SAP HANA, Oracle, Microsoft SQL Server, IBM Db2 databases and MongoDB replica sets. These solutions extend the functionality of Veeam Backup & Replication and are distributed as part of the Veeam Backup & Replication installation image.

Backup solutions for enterprise applications use native database instruments to create backups. Created backups contain data only for databases (including application logs) without server data. For database-level backups created with Veeam Plug-Ins, Veeam Backup & Replication provides recovery of entire databases. For MongoDB databases, you can also restore application items using Veeam Explorers. For more information, see [Restoring from Backup with Veeam Explorer](application_backups_restore_with_explorer.md). You can also recover data using native database tools.

Veeam Backup & Replication allows you to use the following backup solutions for enterprise applications:

* [Veeam Plug-In for Oracle RMAN](rman_plugin.md) — an Oracle-certified backup and recovery solution that allows you to back up and restore Oracle databases.
* [Veeam Plug-In for SAP HANA](sap_hana_plugin.md) — an SAP-certified backup and recovery solution that allows you to back up and restore SAP HANA databases.
* [Veeam Plug-In for SAP on Oracle](sap_orcl_plugin.md) — an SAP-certified backup and recovery solution that allows you to back up and restore Oracle databases to which an SAP application is connected.
* [Veeam Plug-In for SAP MaxDB](plugins_sap_maxdb.md) — a backup and recovery solution that allows you to back up and restore SAP MaxDB databases.
* [Veeam Plug-In for Microsoft SQL Server](mssql_plugin.md) — a backup and recovery solution that allows you to back up and restore Microsoft SQL Server databases.
* [Veeam Plug-In for IBM Db2](db2_plugin.md) — a backup and recovery solution that allows you to back up and restore IBM Db2 databases.
* [Veeam Plug-In Management](management.md) — Veeam Backup & Replication allows you to deploy Veeam Plug-Ins on database servers and launch backup policies directly from the Veeam backup console.
* [MongoDB Backup](mongo_backup.md) — a backup and recovery solution that allows you to back up and restore MongoDB replica sets.

|  |
| --- |
| Important |
| Veeam Plug-Ins store database and log backups in repositories added to the Veeam Backup & Replication infrastructure. Thus, to use Veeam Plug-Ins, you must have a Veeam Backup & Replication server deployed in your infrastructure. To learn how to deploy Veeam Backup & Replication, see [Deployment](deployment.md). |


