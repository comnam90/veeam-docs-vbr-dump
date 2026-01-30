---
title: "Restore Point Selection"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_select_point.html"
last_updated: "3/17/2025"
product_version: "13.0.1.1071"
---

# Restore Point Selection


Veeam Backup & Replication always copies the most recent restore points, even if a backup copy job runs for the first time and source backup repositories already contain chains of restore points.

In the immediate copy mode, backup copy job copies the recent complete restore point created by a source backup job on the first run. On the next runs, Veeam Backup & Replication copies the oldest source restore points that were created after the point initially copied until there are no restore points left.

In the periodic copy mode, backup copy job starts according to schedule. Backup copy job copies the recent complete restore point created by a source backup job on the first run. On the next runs backup copy job continues to copy the recent complete restore points.

If there are no restore points considered as recent, Veeam Backup & Replication does not copy data from source backup repositories. Instead, it waits for new restore points to appear. Only after that, Veeam Backup & Replication copies the most recent data blocks to the target repository.

In the periodic copy mode, you can also specify the search scope for restore points. For more information, see [Select Machines to Process](backup_copy_vms.md).

Limitations for Restore Points Selection

The following limitations apply when Veeam Backup & Replication selects restore points that must be copied to the target repository:

* Veeam Backup & Replication does not copy restore points from the target backup repository.
* Veeam Backup & Replication does not copy restore points from imported backups.
* Veeam Backup & Replication does not copy restore points that have already been copied by the same backup copy job to the target backup repository.
* Veeam Backup & Replication does not copy incomplete restore points.
* Veeam Backup & Replication does not copy restore points that are locked by the backup transformation process (merge, transform).

* A backup copy job does not copy a restore point if its data block size differs from the data block size of restore points that the job has already copied to the target backup repository. To copy restore points with the changed block size, you need to create active full backups. For details, see [Change Storage Optimization Settings for Backup Copy Job](compression_deduplication.md#bc_change_compression).

For example, if you have changed the block size for restore points in the source backup job settings, Veeam Backup & Replication will not copy newly created restore points and will display the Restore point is located in backup file with different block size message.


