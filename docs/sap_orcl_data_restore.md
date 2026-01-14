---
title: "Data Restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_orcl_data_restore.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Data Restore

In this article

With the configured Veeam Plug-In for SAP on Oracle, you can restore Oracle databases from Veeam Plug-In backups that reside on Veeam backup repositories.

You can use the SAP BR\*Tools to restore databases. All restore operations are performed on the SAP BR\*Tools side. For details on how to use specific restore tools, see [Database Recovery](restoring_databases_sap_orcl.md).

Depending on the available type of Veeam Plug-In backups that will be the source for the restored databases, you can perform the following restore operations:

* Restoring from backup.

Restore Oracle databases from a Veeam Plug-In backup using the BRRESTORE tool functionality. For more information, see [Restore Oracle Databases](restore_sap_orcl.md).

You can also restore Oracle databases from a Veeam Plug-In backup to another server. For details, see [Restore to Another Server (System Copy)](restore_sap_orcl_other_server.md).

* Restoring from a backup copy.

Restore Oracle databases from backup copies created for Veeam Plug-In for SAP on Oracle backups. The procedure of database restore from a backup copy is the same as database restore to another server. For more information, see [Restore from Backup Copy](restore_from_copy_sap_orcl.md).

Depending on the available Veeam Plug-In backup files, you can also perform the following restore operations:

* Restoring redo logs.

Restore redo log files that were backed up with BRARCHIVE by using the BRRESTORE tool. For details, see [Restore Redo Logs](restore_sap_orcl_logs.md).

* Restoring from hardened repositories.

Restore Oracle databases from hardened repositories by creating new backup job metadata files (.VACM) with data from available backup metadata files (.VASM). For details, see [Restore from Hardened Repository](restore_from_immutable_sap_orcl.md).

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
