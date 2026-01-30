---
title: "Deleting Unstructured Data Backups from Disk"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/unstructured_data_backup_delete_from_disk.html"
last_updated: "6/24/2025"
product_version: "13.0.1.1071"
---

# Deleting Unstructured Data Backups from Disk


If you want to permanently remove unstructured data backup files from the backup repository and Veeam Backup & Replication console, you can use the Delete from disk operation.

Consider the following:

* Do not delete unstructured data backup files from the backup repository manually. Use the Delete from disk instead. If you delete unstructured data backup files manually, Veeam Backup & Replication database will not reflect these changes, causing subsequent backup job sessions to fail.
* When you delete unstructured data backup files from a disk, Veeam Backup & Replication deletes the whole chain from the backup repository. Thus, on the next backup job run, Veeam Backup & Replication will create a full backup for objects on the data source.
* Delete from disk operation does not remove unstructured data from processing with subsequent backup job sessions. If you do not want to back up this data anymore, remove or exclude it from processing in the backup job's settings.

To delete backups from disk:

1. Open the Home view.

1. In the [inventory pane](vbr_ui.md), select the Backups node.

1. In the working area, select the backup and click Delete from > Disk on the ribbon. You can also right-click the backup and select Delete from disk.


