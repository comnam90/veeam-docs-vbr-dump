---
title: "Specifying Monthly Schedule"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_fs_schedule_monthly.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Specifying Monthly Schedule


To create a monthly schedule for the backup policy, do the following at the Schedule step of the wizard:

1. Set the Monthly retention toggle to On and click Edit Monthly Settings.
2. In the Create monthly schedule window, select months when the backup policy will create snapshots.
3. Use the Create restore points at and Run on drop-down lists to schedule a specific time and day for the backup policy to run.
4. In the Monthly retention section, specify the number of restore points that you want to keep in a snapshot chain.

If the restore point limit is exceeded, the backup appliance removes the earliest restore point from the chain. For more information, see [File Share Snapshot Retention](azure_file_share_snapshot_retention.md).

Consider that Veeam Backup for Microsoft Azure prioritizes global retention settings over retention settings configured for backup policies. If snapshots produced by a backup policy are older than the global retention period, these snapshots will be removed anyway. For more information, see [Configuring Global Retention Settings](azure_configuring_global_retention.md).

1. To save changes made to the backup policy settings, click Apply.

|  |
| --- |
| Tip |
| The backup appliance will start applying the configured retention settings as soon as the backup policy produces restore points. Even if you disable the daily schedule after the restore points are created, the retention policy will still be applied to these restore points. As a workaround, you can modify the configured retention settings. |

[![Adding Backup Policy](images/azure_fs_monthly.webp)](images/azure_fs_monthly.webp "Adding Backup Policy")

Page updated 2026-07-01

