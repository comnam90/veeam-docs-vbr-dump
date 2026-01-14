---
title: "Removing Backup from Configuration"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/delete_backups_config_mssql.html"
last_updated: "8/29/2025"
product_version: "13.0.1.1071"
---

# Removing Backup from Configuration

In this article

If you want to remove records about backups from the Veeam Backup & Replication console and configuration database, you can use the remove from configuration operation.

When you remove a backup from configuration, backup files (.VAB, .VASM, .VACM) remain in the backup repository. You can import the backup later and restore data from it.

To remove a backup from configuration:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, select the necessary backup.
4. Press and hold the [Ctrl] key, right-click the backup and select Remove from > Configuration.

[![Remove from Configuration](images/remove_from_config_mssql.webp)](images/remove_from_config_mssql.webp "Remove from Configuration")

Page updated 8/29/2025

Page content applies to build 13.0.1.1071
