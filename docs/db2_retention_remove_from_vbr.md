---
title: "Deleting Backups Using Veeam Backup & Replication Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_retention_remove_from_vbr.html"
last_updated: "4/2/2024"
product_version: "13.0.1.1071"
---

# Deleting Backups Using Veeam Backup & Replication Console


You can manually delete backups from Veeam backup repositories using the Veeam Backup & Replication console. You can use the console to delete backups in the following ways:

* [Remove backup from the configuration](#remove)
* [Delete backup](#delete)

Removing Backup from Configuration

If you want to remove records about backups from the Veeam Backup & Replication console and configuration database, you can use the Remove from configuration operation. When you remove a backup from configuration, backup files (.VAB, .VASM, .VACM) remain in the backup repository. You can import the backup later and restore data from it.

To remove a backup from configuration:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, select the necessary backup.
4. Press and hold the [Ctrl] key, right-click the backup and select Remove from > Configuration.

[![Remove from Configuration](images/plugins_db2_backup_remove.webp)](images/plugins_db2_backup_remove.webp "Remove from Configuration")

Deleting Backup

You can use the Veeam Backup & Replication console to delete backups created with Veeam Plug-In from a Veeam backup repository.

To delete a backup, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, right-click the name of the backed-up object and select Delete from > Disk.

[![Delete from Disk](images/plugins_db2_backup_delete.webp)](images/plugins_db2_backup_delete.webp "Delete from Disk")


