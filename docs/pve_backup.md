---
title: "Backup Chain"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup.html"
last_updated: "1/26/2026"
product_version: "13.0.1.1071"
---

# Backup Chain


Veeam Backup & Replication creates a new backup file in a backup repository during every backup session. A sequence of backup files created during a set of backup sessions makes up a backup chain. Each backup chain contains data for one VM only. If a backup job includes several VMs, Veeam Backup & Replicationcreates one backup chain for each VM processed by the job.

The backup chain includes backup files of the following types:

* VBK — a full backup file stores a copy of the full VM image.
* VIB — incremental backup files store incremental changes of the VM image.
* VBM — backup metadata files store information about the backup job, VMs processed by the backup job, number and structure of backup files, restore points, and so on. Metadata files facilitate import of backups, backup mapping and other operations.

Full and incremental backup files act as restore points for backed-up VMs that let you roll back VM data to the necessary state. To recover a VM to a specific point in time, the chain of backup files created for the VM must contain a full backup file and a set of incremental backup files dependent on the full backup file.

If some file in the backup chain is missing, you will not be able to roll back to the necessary state. For this reason, you must not delete individual backup files from the backup repository manually. Instead, you must specify retention policy settings that will let you maintain the necessary number of backup files in the backup repository.  For more information, see [Backup Retention](pve_backup_retention.md).

Related Topics

* [Forever Forward Incremental Backup](pve_forever_forward_backup.md)
* [Forward Incremental Backup](pve_forward_backup.md)


