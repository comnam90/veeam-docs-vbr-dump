---
title: "Step 4. Specify Target Repository and Retention Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_target_web.html"
last_updated: "8/11/2025"
product_version: "13.0.1.1071"
---

# Step 4. Specify Target Repository and Retention Settings

In this article

At the Target step of the wizard, define a target backup repository and configure retention policy:

1. From the Backup repository list, select a backup repository where copied backups must be stored.
2. In the Retention Policy field, configure the short-term retention policy for restore points.

When the specified number is exceeded, the earliest restore point will be removed from the backup chain or will be merged with the next closest restore point. For more information on how Veeam Backup & Replication retains the desired number of restore points, see [Short-Term Retention Policy](backup_copy_simple_retention.md).

|  |
| --- |
| Note |
| If you enable the [GFS retention](backup_copy_gfs.md), the short-term retention policy will not be able to delete and merge the GFS backup files. Thus, the backup copy chain will have more restore points than specified in the short-term retention policy. |

1. If you want to create weekly, monthly and yearly full backups, you can configure long-term retention policy (GFS retention policy). GFS full backups will not be deleted or modified until the specified retention period expires. For more information on the GFS retention policy and its limitations, see [Long-Term Retention Policy (GFS)](backup_copy_gfs.md).

To configure GFS retention policy, do the following:

1. Select the Keep certain full backups longer for archival purposes check box.
2. Click Configure.
3. In the Configure GFS window, select the necessary GFS backup options. You can configure Veeam Backup & Replication to create weekly, monthly and yearly restore points. For details on settings of the GFS retention, see [Backup Copy GFS Cycles](backup_copy_gfs_periods.md).

![Step 4. Specify Target Repository and Retention Settings](images/backup_copy_target_gfsschedule_web.webp)

|  |
| --- |
| Note |
| Before you implement the GFS retention policy, see [Limitations and Considerations](backup_copy_considerations.md). |

1. You can define a way to create weekly, monthly and yearly full backups:

* [Synthetic Full Method](backup_copy_gfs_modes.md#synth): With this method, during the GFS backup copy creation, Veeam Backup & Replication does not copy data from the source backup repository but synthesizes full backups from backup files that are already stored in the target backup repository. This approach helps to reduce load on the network and production environment.

The synthetic full method is used by default. To use this method, leave the Read the entire restore point from source instead of synthesizing it from increments option unselected.

* [Active Full Method](backup_copy_gfs_modes.md#active): With this method, Veeam Backup & Replication copies data for archive full backups from the source backup repository. This method decreases load on the target repository but increases load on the network and production environment.

To use this method, select the Read the entire restore point from source instead of synthesizing it from increments option.

![Step 4. Specify Target Repository and Retention Settings](images/backup_copy_target_web.webp)

Page updated 8/11/2025

Page content applies to build 13.0.1.1071
