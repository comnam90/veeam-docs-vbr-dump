---
title: "Data Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_data_backup.html"
last_updated: "6/26/2024"
product_version: "13.0.1.1071"
---

# Data Backup


Veeam Plug-In for IBM Db2 integrates and uses native IBM Db2 mechanisms to back up data to the Veeam backup repository. With the configured Veeam Plug-In, you can create full, incremental or log backups. For details, see [Backup Types](db2_backup_types.md).

For each backup operation, Veeam Plug-In automatically creates and stores database backup files. For each of the created backup files, Veeam Plug-In also creates separate metadata files. The metadata files help Veeam Plug-In to store and manage backup data while ensuring that the data is protected, accessible, and can be quickly restored when needed. All backup files created for backup jobs reside in a dedicated job folder in the backup repository. For details, see [Backup Files](db2_backup_files.md).

To store backups, you can add and configure backup repositories to your Veeam Backup & Replication infrastructure. For details on supported backup repositories, see [Veeam Backup Repositories](db2_backup_repos.md).


