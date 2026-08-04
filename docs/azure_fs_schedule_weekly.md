---
title: "Specifying Weekly Schedule"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_fs_schedule_weekly.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Specifying Weekly Schedule


To create a weekly schedule for the backup policy, do the following at the Schedule step of the wizard:

1. Set the Weekly retention toggle to On and click Edit Weekly Settings.
2. In the Create weekly schedule window, select days of the week when the backup policy will create snapshots.

1. Use the Create restore points at drop-down list to schedule a specific time for the backup policy to run.

1. In the Weekly retention section, specify the number of restore points that you want to keep in a snapshot chain.

If the restore point limit is exceeded, the backup appliance removes the earliest restore point from the chain. For more information, see [File Share Snapshot Retention](azure_file_share_snapshot_retention.md).

Consider that Veeam Backup for Microsoft Azure prioritizes global retention settings over retention settings configured for backup policies. If snapshots produced by a backup policy are older than the global retention period, these snapshots will be removed anyway. For more information, see [Configuring Global Retention Settings](azure_configuring_global_retention.md).

1. To save changes made to the backup policy settings, click Apply.

|  |
| --- |
| Tip |
| The backup appliance will start applying the configured retention settings as soon as the backup policy produces restore points. Even if you disable the daily schedule after the restore points are created, the retention policy will still be applied to these restore points. As a workaround, you can modify the configured retention settings. |

[![Adding Backup Policy](images/azure_fs_weekly.webp)](images/azure_fs_weekly.webp "Adding Backup Policy")

Page updated 2026-07-01

