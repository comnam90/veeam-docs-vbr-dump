---
title: "Database-Level Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protect_applications_db.html"
last_updated: "3/27/2026"
product_version: "13.0.1.2067"
---

# Database-Level Backup


Backup solutions for enterprise applications (Veeam Plug-Ins and MongoDB Backup) allow you to create transactionally-consistent database-level backups of SAP HANA, Oracle, Microsoft SQL Server, IBM Db2 databases and MongoDB replica sets. These solutions extend the functionality of Veeam Backup & Replication and are distributed as part of the Veeam Backup & Replication installation image.

Backup solutions for enterprise applications use native database instruments to create backups. Created backups contain data only for databases (including application logs) without server data. For database-level backups created with Veeam Plug-Ins, Veeam Backup & Replication provides recovery of entire databases. You can recover data using native database tools or Veeam Explorers. For details on which database-level backup solutions support data recovery with Veeam Explorers, see [Launching Veeam Explorer from Plug-in or MongoDB Backup](launching_veeam_explorers_plugin.md).

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


