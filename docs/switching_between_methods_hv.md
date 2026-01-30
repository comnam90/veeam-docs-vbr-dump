---
title: "Switching Between Backup Methods"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/switching_between_methods_hv.html"
last_updated: "8/13/2025"
product_version: "13.0.1.1071"
---

# Switching Between Backup Methods


You can easily switch between backup methods. Veeam Backup & Replication does not transform the previously created chain. Instead, it creates a new backup chain next to the existing one in the following manner:

* If you switch from the reverse incremental method (deprecated) to the forever forward incremental or forward incremental method, Veeam Backup & Replication creates a set of incremental backup files next to the reverse incremental chain. The full backup file in the reverse incremental chain is used as a starting point for incremental backup files.
* If you switch from the forever forward incremental or forward incremental method to the reverse incremental method (deprecated), Veeam Backup & Replication first creates a full backup file next to incremental backup files. During every new job session, Veeam Backup & Replication transforms this full backup file and adds reverse incremental backup files to the backup chain.
* If you switch from the forever forward incremental method to the forward incremental method, Veeam Backup & Replication creates synthetic full backups according to the specified schedule. The old backup chain is deleted when the number of restore points in the new chain reaches the retention limit.
* If you switch from the forward incremental method to the forever forward incremental method, synthetic full backups are no longer created. When the number of restore points created since the last full backup reaches the retention limit, the old backup chain is deleted. Thereafter, with each restore point creation the earliest increment file will merge with the full backup file.

For more information on which settings are required for each method, see the following sections: [Forever Forward Incremental Backup](incremental_forever_backup_hv.md), [Forward Incremental Backup](forward_incremental_backup_hv.md) and [Reverse Incremental Backup (Deprecated)](reversed_incremental_backup_hv.md).


