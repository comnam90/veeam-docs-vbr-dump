---
title: "Creating Active Full Backups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_copy_active_full_create.html"
last_updated: "5/30/2023"
product_version: "13.0.1.1071"
---

# Creating Active Full Backups

In this article

You can manually create an ad-hoc full backup — active full backup, and add it to the backup chain in the target backup repository. Active full backup can be helpful if you want to change backup copy job settings, for example, enable or disable encryption. Veeam Backup & Replication will apply new settings starting from this full backup.

To create an active full backup manually:

1. Open the Home view.
2. In the inventory pane, select the Backup Copy node under Jobs.
3. In the working area, select the backup copy job and click Active full on the ribbon or right-click the backup copy job and select Active full. Veeam Backup & Replication will start a new backup copy session, copy data from the source backup repository and save it in a full backup file in the target backup repository.

[![Click to zoom in](images/backup_copy_active_full_manual.webp)](images/backup_copy_active_full_manual.webp "Click to zoom in")

Related Topics

[Active Full Backup Copies](backup_copy_active_full.md)

Page updated 5/30/2023

Page content applies to build 13.0.1.1071
