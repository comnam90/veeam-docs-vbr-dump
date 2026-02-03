---
title: "Backup Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup_retention.html"
last_updated: "1/8/2026"
product_version: "13.0.1.1071"
---

# Backup Retention


Veeam Backup & Replication retains the number of latest restore points defined in job scheduling settings as described in section [Creating Backup Jobs](pve_backup_job_create_destination.md). For backup chains created by jobs without scheduled active or synthetic full backups, Veeam Backup & Replication applies forever forward incremental backup retention policy. For backup chains created by jobs that regularly produce active or synthetic full backups, Veeam Backup & Replication applies forward incremental backup retention policy.

|  |
| --- |
| Note |
| For backup chains created by jobs that no longer exist, Veeam Backup & Replication applies a separate retention mechanism as described in section [Background Retention](background_retention_job.md). |

Forever Forward Incremental Backup Retention Policy

To track and remove redundant restore points from a forever forward incremental backup chain, Veeam Backup & Replication performs the following actions once a day:

1. Veeam Backup & Replication checks the configuration database to detect backup chains with restore points that are older than the specified time limit.
2. If a redundant restore point exists in a backup chain, Veeam Backup & Replication transforms the backup chain in the following way:

1. Rebuilds the full backup to include there data of the incremental backup that follows the full backup. To do that, Veeam Backup & Replication injects into the full backup data blocks from the earliest incremental backup in the chain. This way, the full backup ‘moves’ forward in the standard backup chain.

![Backup Retention](images/vplugins_backup_retention_injecting_blocks.webp)

1. Removes the earliest incremental backup from the chain as redundant — this data has already been injected into the full backup.

![Backup Retention](images/vplugins_backup_retention_removing_data.webp)

1. Veeam Backup & Replication repeats step 2 for all other redundant restore points found in the backup chain until all the restore points are removed. As data from multiple restore points is injected into the rebuilt full backup, Veeam Backup & Replication ensures that the backup chain is not broken and that you will be able to recover your data when needed.

![Backup Retention](images/vplugins_backup_retention_multiple_points.webp)

Forward Incremental Backup Retention Policy

To track and remove redundant restore points from a forward incremental backup chain, Veeam Backup & Replication performs the following actions once a day:

1. Veeam Backup & Replication checks the configuration database to detect forward incremental backup chains where a new full backup has been created (which starts a new backup chain fragment).
2. Veeam Backup & Replication checks the following whether the period to keep restore points in the new chain fragment has reached the allowed time limit.

1. If the new backup chain fragment has reached the limit of allowed restore points, Veeam Backup & Replication removes all restore points of the older backup chain fragment.

![Backup Retention](images/vplugins_retention_policy_forward.webp)


