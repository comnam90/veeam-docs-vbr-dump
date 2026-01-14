---
title: "Removing Backups from Configuration"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_retention_garbage_collector_remove_from_config.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Removing Backups from Configuration

In this article

If you want to remove records about backups from the Veeam Backup & Replication console and configuration database, you can use the Remove from configuration operation.

When you remove a backup from the configuration, backup files (.VAB, .VASM) remain on the backup repository. You can import backup files later and restore from them.

To remove a backup from configuration:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, select the necessary backup.
4. Press and hold the [Ctrl] key, right-click the backup and select Remove from configuration.

[![Remove from Configuration](images/remove_from_config_maxdb.webp)](images/remove_from_config_maxdb.webp "Remove from Configuration")

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
