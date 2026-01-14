---
title: "Data Backup"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_data_backup.html"
last_updated: "8/22/2025"
product_version: "13.0.1.1071"
---

# Data Backup

In this article

MongoDB Backup is an integrated solution that uses Veeam Backup & Replication mechanisms to back up data to the Veeam backup repository. With the configured application backup policy, you can create full and incremental backups. For details, see [Backup Types](mongo_backup_types.md).

For each backup operation, Veeam Backup & Replication automatically creates and stores database backup files. For the backup chain, Veeam Backup & Replication also creates a separate metadata file. The metadata file helps Veeam Backup & Replication to store and manage backup data while ensuring that the data is protected, accessible, and can be quickly restored when needed. All backup files created for backup policies reside in a dedicated folder in the backup repository. For details, see [Backup Files](mongo_backup_files.md).

Veeam Backup & Replication provides several methods to authenticate against the MongoDB replica set. These methods require different prerequisites and provide different levels of security. For details, see [Authentication Against Database](mongo_auth_methods.md).

To store backups, you can add and configure backup repositories to your Veeam Backup & Replication infrastructure. For details on supported backup repositories, see [Veeam Backup Repositories](mongo_backup_repos.md).

Page updated 8/22/2025

Page content applies to build 13.0.1.1071
