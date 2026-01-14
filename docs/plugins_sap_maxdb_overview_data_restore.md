---
title: "Data Restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_overview_data_restore.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Data Restore

In this article

With the configured Veeam Plug-In for SAP MaxDB, you can restore SAP MaxDB databases from Veeam Plug-In backups that reside on Veeam backup repositories. Restore operations are performed on the Veeam Plug-In side.

Depending on the available type of Veeam Plug-In backups that will be the source for the restored databases, you can perform the following restore operations:

* Restoring from backup.

Restore SAP MaxDB databases from a Veeam Plug-In backup to the original server by using the recover\_start command. For details, see [Restore to Original Server](plugins_sap_maxdb_restore_db.md).

You can also restore SAP MaxDB databases from a Veeam Plug-In backup to another server. For details, see [Restore to Original Server](plugins_sap_maxdb_restore_db.md).

* Restoring from a backup copy.

Restore SAP MaxDB databases from backup copies created for Veeam Plug-In for SAP MaxDB backups. The procedure of database restore from a backup copy is the same as database restore to another server. For details, see [Restore to Another Server](plugins_sap_maxdb_restore_to_another.md).

Depending on the location of Veeam Plug-In backups that will be the source for the restored databases, you can also perform the following restore operations:

* Restoring from simple repositories.

Restore SAP MaxDB databases from Veeam Plug-In backups stored on supported types of repositories. For the list of supported repositories, see [Veeam Backup Repositories](plugins_sap_maxdb_overview_data_backup_repos.md).

* Restoring from hardened repositories.

Restore SAP MaxDB databases from hardened repositories by creating new backup job metadata files (.VACM) with data from available backup metadata files (.VASM). For details, see [Restore from Hardened Repository](plugins_sap_maxdb_restore_from_hard.md).

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
