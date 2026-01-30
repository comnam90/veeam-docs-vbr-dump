---
title: "Full Backup Methods"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/full_backup_methods_hv.html"
last_updated: "2/11/2025"
product_version: "13.0.1.1071"
---

# Full Backup Methods


Veeam Backup & Replication provides the following methods for creation of full backup files:

* [Active Full Backup](active_full_backup_hv.md)

When you perform an active full backup, Veeam Backup & Replication retrieves VM data from the source volume where the VM resides, compresses and deduplicates it and writes it to the VBK file in the backup repository.

* [Synthetic Full Backup](synthetic_full_backup_hv.md)

When you perform a synthetic full backup, Veeam Backup & Replication does not retrieve VM data from the source volume. Instead, it synthesizes a full backup from data you already have in the backup repository. Veeam Backup & Replication accesses the previous full backup file and a chain of subsequent incremental backup files on the backup repository, consolidates VM data from these files and writes consolidated data into a new full backup file. As a result, the created synthetic full backup file contains the same data you will have if you create an active full backup.

|  |
| --- |
| Tip |
| You can perform both active and synthetic full backups. For more information on how to do that, see [Backup Settings](backup_job_advanced_backup_hv.md). |


