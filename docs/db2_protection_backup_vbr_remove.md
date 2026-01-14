---
title: "Removing Backup from Configuration"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_protection_backup_vbr_remove.html"
last_updated: "9/1/2025"
product_version: "13.0.1.1071"
---

# Removing Backup from Configuration

In this article

If you want to remove records about backups from the Veeam Backup & Replication console and configuration database, you can use the Remove from configuration operation. When you remove a backup from configuration, backup files (.VAB, .VASM, .VACM) remain in the backup repository. You can import the backup later and restore data from it.

To remove a backup from configuration:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, select the necessary backup.
4. Press and hold the [Ctrl] key, right-click the backup and select Remove from > Configuration.

[![Remove from Configuration](images/db2_backup_remove.webp)](images/db2_backup_remove.webp "Remove from Configuration")

Page updated 9/1/2025

Page content applies to build 13.0.1.1071
