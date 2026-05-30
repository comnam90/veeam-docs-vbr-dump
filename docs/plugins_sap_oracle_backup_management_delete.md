---
title: "Deleting Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_oracle_backup_management_delete.html"
last_updated: "2/15/2026"
product_version: "13.0.2.29"
---

# Deleting Backup


Apart from configuring the [retention policy](garbage_collector_sap_orcl.md), you can delete backups manually from backup repositories using the Veeam Backup & Replication console.

|  |
| --- |
| Note |
| If you remove backups from a backup repository manually, the backup catalog will not be updated. |

To remove a backup from a backup repository, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. In the Inventory pane, select Backups.
3. In the working area, right-click the backup job object name and select Delete from disk.

[![Delete from Disk](images/plugins_sap_orcl_remove_disk.webp)](images/plugins_sap_orcl_remove_disk.webp "Delete from Disk")


