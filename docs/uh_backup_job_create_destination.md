---
title: "Step 4. Configure Backup Destination Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/uh_backup_job_create_destination.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Configure Backup Destination Settings


At the Backup Destination step of the wizard, do the following:

1. In the Backup repository drop-down list, select a backup repository where you want to store backups. For a backup repository to be displayed in the list of available repositories, it must be [added to the backup infrastructure](uh_configure_repository.md).

When restoring data of backed-up VMs, Veeam Backup & Replication will offer you to choose a restore point from the list of all restore points available in the default backup repository. To allow Veeam Backup & Replication to detect restore points created for these VMs by other backup jobs or stored in other backup repositories, you can map these restore points to this backup job — this way, Veeam Backup & Replication will be able to continue existing backup chains and will transfer less data over network, reducing unwanted overhead for the production environment. To do that, click Map backup and choose the necessary backup.

1. In the Retention policy section, choose how long Veeam Backup & Replication will keep restore points in a backup chain. If a restore point is older than the specified limit, Veeam Backup & Replication will remove it from the chain. For more information on how Veeam Backup & Replication tracks and removes redundant restore points, see [Retention Policies](uh_retention_policy.md).

Keep in mind that since every backup chain must contain at least 3 restore points, Veeam Backup & Replication may ignore the configured retention policy settings and retain restore points for longer periods of time. For more information, see [Backup Retention](uh_backup_retention.md).

|  |
| --- |
| Important |
| If you use [hardened repositories](hardened_repository.md) to store Veeam Backup & Replication VM backups, you must consider the following requirements:   * Active full backups must be scheduled in the backup job settings. * The backup job retention period must be longer than the backup repository immutability period.   For example, if the backup repository immutability period is set to 25 days, you can configure a one-month retention period: specify 4 as the number of restore points, [schedule one backup per week](uh_backup_job_create_schedule.md) and schedule active full backup to run on the last day of the month. |

To help you implement a comprehensive backup strategy, Veeam Backup & Replication allows you to [enable long-term retention policy for backups](uh_backup_job_create_gfs.md) and to [configure advanced job settings](uh_backup_job_create_advanced.md) (such as notification settings, health check, active and synthetic full backups).

[![Backup Destination](images/uh_backup_job_create_destination.webp)](images/uh_backup_job_create_destination.webp "Backup Destination")

Page updated 2026-07-24

