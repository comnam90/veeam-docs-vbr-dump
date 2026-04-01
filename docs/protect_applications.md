---
title: "Databases and Enterprise Applications"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protect_applications.html"
last_updated: "3/31/2026"
product_version: "13.0.1.2067"
---

# Databases and Enterprise Applications


Veeam Backup & Replication allows you to protect data from various applications and databases, such as Microsoft Active Directory, Microsoft SQL Server, MongoDB and others. Depending on the application you want to back up and the level on which you want to create a backup, we suggest the following options:

Databases and Enterprise Applications

| Database or Application | Image-Level Backup with Application-Aware Processing | Database-Level Backup with Veeam Plug-Ins or MongoDB Backup |
| IBM Db2 | - | [Veeam Plug-In for IBM Db2](db2_plugin.md) |
| Microsoft Active Directory | [Veeam Backup & Replication](application_aware_processing.md) | - |
| Microsoft Exchange | [Veeam Backup & Replication](application_aware_processing.md) | - |
| Microsoft SharePoint | [Veeam Backup & Replication](application_aware_processing.md) | - |
| Microsoft SQL Server | [Veeam Backup & Replication](application_aware_processing.md) | [Veeam Plug-In for Microsoft SQL Server](mssql_plugin.md) |
| MongoDB | - | [MongoDB Backup](mongo_backup.md) |
| MySQL | [Veeam Agent for Linux](agents_backup_linux_dbs_processing.md) | - |
| Oracle | [Veeam Backup & Replication](application_aware_processing.md), | [Veeam Plug-In for Oracle RMAN](rman_plugin.md), |
| PostgreSQL | [Veeam Backup & Replication](application_aware_processing.md),  [Veeam Agent for Linux](agents_backup_linux_dbs_processing.md) | - |
| SAP HANA | - | [Veeam Plug-In for SAP HANA](sap_hana_plugin.md) |
| SAP MaxDB | - | [Veeam Plug-In for SAP MaxDB](plugins_sap_maxdb.md) |

In This Section

* [Image-Level Backup](protect_applications_image.md)
* [Database-Level Backup](protect_applications_db.md)


