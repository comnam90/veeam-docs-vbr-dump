---
title: "Data Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_data_backup.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# Data Backup


Veeam Plug-In for Oracle RMAN transfers backup data to the Veeam backup repository and stores the data in the Veeam proprietary format for backups.

You can use the built-in Oracle functionality to initiate and manage backup operations. Veeam Backup & Replication creates a backup job for all backup operations started in Oracle RMAN. Use this job to view the statistics on the backup process, generate backup job reports or disable the backup job. For details on how to perform backup operations, see [Database Protection](rman_protection.md).

For each backup operation, Veeam Plug-In automatically creates and stores database backup files. For each of the created backup files, Veeam Plug-In also creates separate metadata files. The backup and metadata files help Veeam Plug-Ins to store and manage backup data while ensuring that the data is protected, accessible, and can be quickly restored when needed. All backup files created for backup jobs reside in a dedicated job folder in the backup repository. For details on backup files, see [Veeam Plug-In Backup Files](rman_bfiles.md).

Veeam Plug-In allows you to authenticate against Oracle database with the credentials of operation system or database user. For details, see [Authentication Against Database](rman_auth_methods.md)

To store backup files, you can add backup repositories to your Veeam Backup & Replication infrastructure. For details on all supported backup repositories, see [Veeam Backup Repositories](repos_rman.md).


