---
title: "Data Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_overview_backup.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Data Backup

In this article

Veeam Plug-In for SAP MaxDB transfers backed-up data to the Veeam backup repository and stores the data in the Veeam proprietary format for backups.

With Veeam Plug-In for SAP MaxDB, you can create a consistent backup of SAP MaxDB databases and automatically transfer the backup files to the Veeam backup repository. Veeam Backup & Replication creates a backup job for all backup processes started on the SAP MaxDB side. Use this job to view the statistics on the backup process, generate backup job reports or disable the backup jobs. All backup processes are performed on the SAP MaxDB side and are managed by SAP MaxDB Database Manager. For details on how to back up SAP MaxDB databases with Veeam Plug-In, see [Performing Backup](plugins_sap_maxdb_backup.md).

For each backup operation, Veeam Plug-In automatically creates and stores database backup files. For each of the created backup files, Veeam Plug-In also creates separate metadata files. The backup and metadata files help Veeam Plug-Ins to store and manage backup data while ensuring that the data is protected, accessible, and can be quickly restored when needed. All backup files created for backup jobs reside in a dedicated job folder in the backup repository. For details on backup files, see [Veeam Plug-In Backup Files](plugins_sap_maxdb_overview_backup_files.md).

To store backup files, you can add backup repositories to your Veeam Backup & Replication infrastructure. For details on all supported backup repositories, see [Veeam Backup Repositories](plugins_sap_maxdb_overview_data_backup_repos.md).

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
