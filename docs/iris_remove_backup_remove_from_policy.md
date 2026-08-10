---
title: "Removing Backup from Backup Policy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_remove_backup_remove_from_policy.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Backup from Backup Policy


If you want to detach records about application backups of InterSystems IRIS instances from the application backup policy, you can use the Remove from job operation. This makes the backup orphaned. The backup remains visible in the Veeam Backup & Replication console and configuration database, under Backups > Disk (Orphaned), and the actual backup files remain on the backup repository. To fully remove the backup from the console and database, use [Removing Backup from Configuration](iris_remove_backup_remove_from_configuration.md).

|  |
| --- |
| NOTE |
| You can use the Veeam Backup & Replication console to remove backups created by application backup policies in the Veeam backup repository. Backups created on a local drive of a protected computer or in a network shared folder are not displayed in the Veeam backup console. |

To remove an application backup from configuration:

1. Open the Home view.
2. In the inventory pane, click Backups.
3. To remove the backup of an application backup policy, select the policy, press and hold the [Ctrl] key, right-click the backup and select Remove from > Job.

[![Remove Backup from Backup Job](images/iris_remove_from_job.webp)](images/iris_remove_from_job.webp "Remove Backup from Backup Job")

Page updated 2026-08-05

