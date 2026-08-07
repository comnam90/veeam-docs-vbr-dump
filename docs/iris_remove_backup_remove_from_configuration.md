---
title: "Removing Backup from Configuration"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_remove_backup_remove_from_configuration.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Backup from Configuration


If you want to remove records about the application backup created by an InterSystems IRIS backup policy from the Veeam Backup & Replication console and configuration database without deleting the backup files from the backup repository, you can use the Remove from Configuration operation. The backup files remain on the backup repository and can be imported to Veeam Backup & Replication at any time. This operation is intended for experienced Veeam Backup & Replication users.

To remove an application backup from configuration:

1. Open the Home view.
2. In the inventory pane, click Backups.
3. In the working area, expand the parent backup, select the backup created by the application backup policy, press and hold the [Ctrl] key, right-click it and select Remove from > Configuration.

[![Remove Backup from Configuration](images/iris_remove_from_configuration.webp)](images/iris_remove_from_configuration.webp "Remove Backup from Configuration")

Page updated 2026-08-05

