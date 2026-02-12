---
title: "Deleting Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_backups_delete.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Deleting Backups


By default, Veeam Plug-in for Scale Computing HyperCore maintains backups stored in backup repositories according to retention policy settings saved in the backup metadata. If Veeam Plug-in for Scale Computing HyperCore detects that the number of restore points in the backup chain exceeds the allowed number, it automatically removes obsolete backups. You can also delete backup files from backup repositories manually if you no longer need them.

To delete backup files created for a Scale Computing HyperCore VM, do the following:

1. Open the Home view.
2. In the inventory pane of the Home view, select Backups.
3. In the working area, expand the job that created the backup, right-click the VM name and select Remove from > Disk.

|  |
| --- |
| Note |
| If [4-eyes authorization](four_eyes_authorization.md) is enabled in Veeam Backup & Replication, deleting backup files will require additional approval from another user with the Veeam Backup Administrator role. |

[![Deleting Backups](images/sch_backups_delete.webp)](images/sch_backups_delete.webp "Deleting Backups")


