---
title: "Removing Backup from Configuration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/delete_backups_config_mssql.html"
last_updated: "1/19/2026"
product_version: "13.0.1.1071"
---

# Removing Backup from Configuration


If you want to remove records about backups from the Veeam Backup & Replication console and configuration database, you can use the remove from configuration operation.

When you remove a backup from configuration, backup files (.VAB, .VASM, .VACM) remain in the backup repository. You can import the backup later and restore data from it.

To remove a backup from configuration:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, select the necessary backup.
4. Press and hold the [Ctrl] key, right-click the backup and select Remove from > Configuration.

[![Remove from Configuration](images/plugins_remove_from_config_mssql.webp)](images/plugins_remove_from_config_mssql.webp "Remove from Configuration")


