---
title: "Backup Cache"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_backup_cache.html"
last_updated: "12/8/2025"
product_version: "13.0.1.1071"
---

# Backup Cache


Veeam Agent for Microsoft Windows managed by Veeam Backup & Replication supports creating restore points in the backup cache — a temporary local storage where Veeam Agent creates backup files in case a remote backup location is unavailable at the time of backup. This may be helpful in the scenario where you create Veeam Agent backups using the backup policy: if some computers in the backup policy cannot access the remote location during scheduled backup, Veeam Agent creates backup files in the backup cache on these computers. When the target location becomes available, Veeam Agent uploads backup files from the backup cache to the remote storage so that the backup chain contains a sequence of restore points that precisely complies with the backup schedule.

In the Veeam Agent management scenario, the backup cache works in the similar way as in Veeam Agent operating in the standalone mode. To learn more, see the [Backup Cache](https://helpcenter.veeam.com/docs/agentforwindows/userguide/backup_cache.html?ver=13) section in the Veeam Agent for Microsoft Windows User Guide.

In addition to backup cache features and limitations listed in the Veeam Agent for Microsoft Windows User Guide, the following applies to Veeam Agent operating in the managed mode:

* The backup cache is supported only for backup policies (backup jobs managed by Veeam Agent).

* You can specify backup cache settings in the properties of backup policies targeted at the following types of backup location:

* Veeam backup repository
* Cloud repository

* To facilitate backup cache configuration on multiple Veeam Agent computers added to the backup policy, you can instruct Veeam Agent to automatically select location for the backup cache on each computer. To learn more, see [How Automatic Backup Cache Placement Works](#auto).

How Automatic Backup Cache Placement Works

You can instruct Veeam Agent to automatically select location for the backup cache on each computer added to the backup policy. To do this, select the Automatic selection option at the Backup Cache step of the New Agent Backup Job wizard.To learn more, see [Specify Backup Cache Settings](agent_policy_win_cache.md).

With the Automatic selection option enabled in the backup cache settings, Veeam Agent for Microsoft Windows creates the backup cache according to the following rules:

1. By default, Veeam Agent attempts to select for the backup cache a non-system volume that has enough free space for the specified backup cache quota (that is, maximum backup cache size) and has the largest amount of free space.
2. On the selected volume, Veeam Agent creates the backup cache in the Veeam Backup Cache folder.

Consider the following:

* If the volume with the largest amount of free space is a system volume, Veeam Agent selects the volume that has enough space for the backup cache quota and has the second largest amount of free space.
* If the system volume is the only volume that has enough space for the backup cache quota, Veeam Agent creates the backup cache on the system volume.
* If no volumes have enough space for the backup cache quota, Veeam Agent selects the volume that has the largest amount of free space.
* Once Veeam Agent creates the Veeam Backup Cache folder on a protected computer, Veeam Agent does not change the location of this folder.

For example, the system volume is the only volume that has enough space for the backup cache quota at the time when you create the backup policy. In this case, Veeam Agent creates the Veeam Backup Cache folder on the system volume. After disk configuration changes on the computer, a non-system volume becomes able to fit the backup cache quota. However, Veeam Agent will not move the Veeam Backup Cache folder to the non-system volume.

* Veeam Agent does not create the backup cache on external, removable or virtual disks.

Tasks with Backup Cache

For Veeam Agent operating in the managed mode, you can perform the same operations with the backup cache as for the standalone version of the product: you can monitor backup cache activity, pause backup cache synchronization and delete restore points from the backup cache. To do this, you must use the Veeam Agent control panel directly on the protected computer. To learn more, see the [Managing Backup Cache](https://helpcenter.veeam.com/docs/agentforwindows/userguide/backup_cache_manage.html?ver=13) section in the Veeam Agent for Microsoft Windows User Guide.

Keep in mind that Veeam Backup & Replication automatically deletes restore points from the backup cache on all computers added to the backup policy after you perform one of the following operations:

* Change the target location for backup files in the backup policy settings.

* Change the backup mode for the backup policy to the File-level backup.

* Enable or disable data encryption settings for the backup policy.
* Change backup cache location for the backup policy (in case it was specified manually).
* Disable the backup cache for the backup policy.
* Delete the backup policy.

You can also delete restore points from the backup cache manually in the Veeam backup console. To learn more, see [Clearing Backup Cache](agent_policy_cache.md).


