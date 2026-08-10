---
title: "Removing File Share Snapshots"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_removing_fs_snapshots.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing File Share Snapshots


The backup appliance applies the [configured retention policy settings](azure_fs_backup_policy_schedule.md) to automatically remove cloud-native snapshots created by backup policies. If necessary, you can also remove the backed-up data manually.

|  |
| --- |
| Note |
| In the backup appliance Web UI, you can remove only snapshots created by the Veeam backup service. To delete External snapshots, use Microsoft Azure portal as described in [Microsoft Docs](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-quick-create-use-windows#delete-a-share-snapshot). |

To remove backed-up data manually, do the following:

1. Navigate to Protected Data > Azure Files.
2. Select Azure file shares whose data you want to remove.
3. Click Remove and select either of the following options:

* All — to remove all cloud-native snapshots created for the selected Azure file shares both by backup policies and manually.
* Policy Snapshots — to remove all cloud-native snapshots created for the selected Azure file shares by backup policies.
* Manual Snapshots — to remove all cloud-native snapshots created for the selected Azure file shares manually.

[![Removing Snapshots](images/azure_remove_backups_fs.webp)](images/azure_remove_backups_fs.webp "Removing Snapshots")

Page updated 2026-07-01

