---
title: "File Share Snapshot Retention"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_file_share_snapshot_retention.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# File Share Snapshot Retention


For cloud-native snapshots, the backup appliance retains the number of latest restore points defined in backup scheduling settings as described in section [Creating Azure Files Backup Policies](azure_fs_backup_policy_schedule.md).

During every successful backup session, the backup appliance creates a new restore point. If the backup appliance detects that the number of restore points in the snapshot chain exceeds the retention limit, it removes the earliest restore point from the chain. For more information on the snapshot deletion process, see [Microsoft Docs](https://docs.azure.cn/en-us/storage/files/storage-files-prevent-file-share-deletion?tabs=azure-portal).

[![File Share Snapshot Retention](images/azure_snapshot_retention.webp)](images/azure_snapshot_retention.webp)

|  |
| --- |
| Note |
| Consider that Veeam Backup for Microsoft Azure does not apply retention policy settings to cloud-native snapshots created manually. To learn how to remove these snapshots, see [Managing Azure Files Data](azure_removing_fs_manual_snaphots.md). |

Page updated 2026-07-01

