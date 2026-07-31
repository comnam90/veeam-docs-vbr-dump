---
title: "Deleting Backup from Disk"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_remove_snapshot_delete.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Deleting Backup from Disk


If you want to permanently delete InterSystems IRIS instance storage snapshots from the storage system, you can use the Remove from Disk operation. Veeam Backup & Replication deletes the snapshots from the storage system through the Universal Storage API. This operation cannot be undone.

To delete a snapshot from disk:

1. Open the Home view.
2. In the inventory pane, click Backups.
3. In the working area, select the necessary snapshot and click Remove from > Disk on the ribbon, or right-click the snapshot and select Remove from > Disk.

[![Remove Snapshot Backup from Disk](images/iris_snapshot_remove_from_disk.webp)](images/iris_snapshot_remove_from_disk.webp "Remove Snapshot Backup from Disk")

Page updated 2026-07-10

