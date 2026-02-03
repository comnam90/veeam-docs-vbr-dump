---
title: "Backup Methods"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_backup_methods.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Backup Methods


Veeam Backup & Replication provides the following methods for creating backup chains:

* Forever forward incremental

When the forever forward incremental backup method is used, Veeam Backup & Replicationcreates a backup chain that consists of the first full backup file (VBK) and a set of forward incremental backup files (VIBs) following it. For more information, see [Forever Forward Incremental Backup](ovirt_forever_forward_backup.md).

This backup method helps you save space on the backup storage because Veeam Backup & Replication stores only one full backup file and removes incremental backup files [once the retention period is exceeded](ovirt_backup_retention.md#ffi).

* Forward incremental

When the forward incremental backup method is used, Veeam Backup & Replication creates a backup chain that consists of multiple full backup files (VBKs) and sets of forward incremental backup files (VIBs) following each full backup file. Full backups created using the synthetic full or active full method split the backup chain into shorter series. This lowers the chances of losing the backup chain completely and makes this backup method the most reliable. For more information, see [Forward Incremental Backup](ovirt_forward_backup.md).

This backup method requires more storage space than other methods because the backup chains contains multiple full backup files and sometimes Veeam Backup & Replication stores more restore points than specified in the retention policy settings due to the specifics of the [forward incremental retention policy](ovirt_backup_retention.md#fi).

Related Topics

* [Active Full Backup](ovirt_active_full_backup.md)
* [Synthetic Full Backup](ovirt_synthetic_full_backup.md)


