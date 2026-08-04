---
title: "Viewing Backup Properties"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_application_backups_properties.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Viewing Backup Properties


To review what data was backed up by an application backup policy, check the backup properties in the Veeam Backup & Replication console.

To view backup properties:

1. Open the Home view.
2. In the inventory pane, expand the Backups node and select Disk. To view properties of backups stored on tape, select Tape.
3. In the working area, right-click the backup and select Properties.

The backup properties window displays the following information:

* Databases — items backed up by the application backup policy.
* Backup catalog — items created in the catalog for the backed-up databases. For Microsoft SQL Server backups, restore points stored in the Veeam Backup & Replication configuration database are displayed instead.
* Files — backup files stored in the backup repository.

To find a specific item in a list, use the search field. To copy the path to a backup file, use the Copy path command.

Page updated 2026-07-24

