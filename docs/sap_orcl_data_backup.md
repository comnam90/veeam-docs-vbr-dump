---
title: "Data Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_orcl_data_backup.html"
last_updated: "4/4/2025"
product_version: "13.0.1.1071"
---

# Data Backup


Veeam Plug-In for SAP on Oracle transfers backup data to the Veeam backup repository and stores the data in the Veeam proprietary format for backups.

With Veeam Plug-In for SAP on Oracle, you can create a consistent backup of Oracle databases and automatically transfer the backup files to the Veeam backup repository. Veeam Backup & Replication creates a backup job for all backup processes started on the SAP on Oracle side. Use this job to view the statistics on the backup process, generate backup job reports or disable the Oracle backup jobs. All backup processes are performed on the SAP on Oracle side and are managed by the SAP BR\*Tools. For details on how to back up Oracle databases with Veeam Plug-In for SAP on Oracle, see [Database Protection](backup_sap_orcl.md).

For each backup operation, Veeam Plug-In automatically creates and stores database backup files. For each of the created backup files, Veeam Plug-In also creates separate metadata files. The backup and metadata files help Veeam Plug-Ins to store and manage backup data while ensuring that the data is protected, accessible, and can be quickly restored when needed. All backup files created for backup jobs reside in a dedicated job folder in the backup repository. For details on backup files, see [Veeam Plug-In Backup Files](saporcl_bfiles.md).

To store backup files, you can add backup repositories to your Veeam Backup & Replication infrastructure. For details on all supported backup repositories, see [Veeam Backup Repositories](sap_orcl_repos.md).


