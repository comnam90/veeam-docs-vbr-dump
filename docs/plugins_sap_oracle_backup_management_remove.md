---
title: "Removing Backup From Configuration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_oracle_backup_management_remove.html"
last_updated: "2/15/2026"
product_version: "13.0.2.29"
---

# Removing Backup From Configuration


If you want to remove records about backups from the Veeam Backup & Replication console and configuration database, you can use the remove from configuration operation.

When you remove a backup from the configuration, backup files (.VAB, .VASM) remain on the backup repository. You can import backup files later and restore from them.

To remove a backup from configuration:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, select the necessary backup.
4. Press and hold the [Ctrl] key, right-click the backup and select Remove from > Configuration.

[![Remove from Configuration](images/plugins_remove_from_config_sap_orcl.webp)](images/plugins_remove_from_config_sap_orcl.webp "Remove from Configuration")


