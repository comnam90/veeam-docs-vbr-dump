---
title: "Removing Missing Restore Points"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/remove_missing_point_hv.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---

# Removing Missing Restore Points

In this article

In some cases, one or more restore points in the backup chain may be inaccessible. It can happen, for example, if the backup repository is put into Maintenance mode (for scale-out backup repositories), the backup repository is unavailable, or some backup file is missing in the backup chain. Backup chains that contain missing restore points get corrupted — you cannot perform backup or restore VM data from the missing restore point and restore points that depend on the missing restore point.

You can perform two operations with missing restore points:

* [Forget](#forget) — you can remove records about missing restore points from the configuration database. Veeam Backup & Replication will “forget” about missing restore points and will not display them in the console. The actual backup files will remain on disk (if backup files are still available).
* [Remove](#delete) — you can remove records about missing restore points from the configuration database and delete backup files from disk (if backup files are still available).

|  |
| --- |
| Note |
| Consider the following:   * The Forget and Remove from disk options are available only for the restore points missing from the backup chain or points that depend on missing ones. If the restore point is available in the backup chain and does not depend on a missing restore point, you will not be able to use the Forget and Remove from disk options for it.  * You can manually update information about missing restore points. For this, disable a backup job and rescan the backup repository that is the target for the job. For more information, see [Disabling and Deleting Jobs](disabling_jobs_hv.md) and [Rescanning Backup Repositories](rescanning_backup_repositories.md).   Manual update can be required because Veeam Backup & Replication requires some time to update information in the configuration database for restore points that were removed from a backup chain or became inaccessible. That is why such restore points may not be displayed in the console as missing restore points.   * Veeam Backup & Replication does not track missing restore points in backups that reside in the cloud repository. * If you apply the Forget or Remove from disk options to a missing restore point in a scale-out backup repository, the backup file associated with the missing restore point will be deleted from the capacity tier and archive tier on the next offload and archiving job run. |

To remove records about missing restore points from the configuration database:

1. Open the Home view.
2. In the [inventory pane](vbr_ui.md), select Disk under Backups.
3. In the working area, select the backup and click Properties on the ribbon or right-click the backup and select Properties.
4. In the Backup Properties window, right-click the missing restore point and select Forget.

+ To remove only the selected restore point and restore points that depend on it (that is, a part of the backup chain starting from this restore point), select This and dependent backups.
+ To remove all missing restore points, select All unavailable backups.

To remove missing restore points from the configuration database and disk:

1. Open the Home view.
2. In the [inventory pane](vbr_ui.md), click Disk under Backups.
3. In the working area, select the backup and click Properties on the ribbon or right-click the backup and select Properties.
4. In the Backup Properties window, right-click the missing restore point and select Remove from disk.

+ To remove only the selected restore point and restore points that depend on it (that is, a part of the backup chain starting from this restore point), select This and dependent backups.
+ To remove all missing restore points, select All unavailable backups.

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
