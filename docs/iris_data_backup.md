---
title: "Data Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_data_backup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Data Backup


Epic EHR System Protection protection is an integrated solution that uses Veeam Backup & Replication mechanisms to create storage snapshot backups of InterSystems IRIS instance data. With a configured application backup policy, you can operate in backup mode to create full and incremental backups in a Veeam backup repository, or in snapshot-only mode to retain storage snapshots on the storage system. For details, see [Backup Types](iris_backup_types.md).

For each backup operation in backup mode, Veeam Backup & Replication automatically creates and stores backup files in the target backup repository. For the backup chain, Veeam Backup & Replication also creates a separate metadata file. The metadata file helps Veeam Backup & Replication store and manage backup data while ensuring that the data is protected, accessible and can be quickly restored when needed. All backup files created for a backup policy reside in a dedicated folder in the backup repository. For details, see [Backup Files](iris_backup_files.md).

Veeam Backup & Replication connects to each InterSystems IRIS instance through the Veeam Transport Service running on the ODB server. To perform application aware processing, including freezing and thawing the instance, Veeam Backup & Replication switches to the database user with OS user privileges that owns the InterSystems IRIS instance. You specify this user name in the policy processing settings. For details, see [Authentication](iris_auth_methods.md).

To store backups, you can add and configure backup repositories in your Veeam Backup & Replication infrastructure. All primary backup repositories available in Veeam Backup & Replication are supported as backup targets for InterSystems IRIS application backup policies. For details, see [Veeam Backup Repositories](iris_backup_repos.md).

Page updated 2026-07-24

