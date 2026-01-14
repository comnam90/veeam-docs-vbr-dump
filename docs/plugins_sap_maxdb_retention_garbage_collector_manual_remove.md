---
title: "Deleting Backups Manually"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_retention_garbage_collector_manual_remove.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Deleting Backups Manually

In this article

Apart from configuring the [retention policy](plugins_sap_maxdb_retention_garbage_collector.md), you can delete backups manually from backup repositories using the Veeam Backup & Replication console.

|  |
| --- |
| Note |
| If you remove backups from a backup repository manually, the backup catalog will not be updated. |

To remove a backup from a backup repository, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. In the Inventory pane, select Backups.
3. In the working area, right-click the backup job object name and select Delete from disk.

[![Delete from Disk](images/maxdb_remove_disk.webp)](images/maxdb_remove_disk.webp "Delete from Disk")

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
