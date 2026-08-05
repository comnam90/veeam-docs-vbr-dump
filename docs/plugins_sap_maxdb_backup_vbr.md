---
title: "Backup in Veeam Backup & Replication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_backup_vbr.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup in Veeam Backup & Replication


After a backup job session completes successfully, Veeam Backup & Replication creates a backup in the backup repository. You can use the Veeam Backup & Replication console to create recovery token, delete the backup, and view the backup properties.

Creating Recovery Token

If you want to recover database data from a specific backup, you can use the Create recovery token operation.

You can generate the recovery token on the Veeam Backup & Replication side. Then, on the computer side, with this recovery token get access to the backup and recover data that are stored in the backup. To learn more about operations on the computer side, see [Restore to Another Server Using Recovery Token](plugins_sap_maxdb_restore_to_another.md#token).

Before creating a recovery token, consider the following prerequisites and limitations:

* Recovery tokens stay valid for 24 hours.
* You can recover data only from the backup for which the recovery token is generated.
* During recovery, Veeam Backup & Replication does not stop backup operations.
* You cannot create a recovery token for a whole backup copy job, but you can create a recovery token for individual objects included in a backup copy job.

To create a recovery token on the Veeam Backup & Replication side:

1. Open the Home view.
2. In the inventory pane, click Backups.
3. In the working area, right-click the backup and select Create Recovery Token.

You can create a recovery token for several backups. To do this, press and hold [Ctrl], select multiple backups, right-click one of the selected backups and select Create Recovery Token.

1. In the Create Recovery Token window, click Create.

You can also create and modify the existing recovery token using the PowerShell console. To learn more, see the [Working with Tokens](https://helpcenter.veeam.com/docs/vbr/powershell/tokens.html?ver=13) section in the Veeam PowerShell Reference.

|  |
| --- |
| Tip |
| Alternatively, you can get access to the backup using user credentials. |

[![Create Recovery Token](images/plugins_create_re_token_maxdb.webp)](images/plugins_create_re_token_maxdb.webp "Create Recovery Token")

Deleting Backups Manually

Apart from configuring the [retention policy](plugins_sap_maxdb_retention_garbage_collector.md), you can delete backups manually from backup repositories using the Veeam Backup & Replication console.

|  |
| --- |
| Note |
| If you remove backups from a backup repository manually, the backup catalog will not be updated. |

To remove a backup from a backup repository, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. In the Inventory pane, select Backups.
3. In the working area, right-click the backup job object name and select Delete from disk.

[![Delete from Disk](images/plugins_maxdb_remove_disk.webp)](images/plugins_maxdb_remove_disk.webp "Delete from Disk")

Removing Backups from Configuration

If you want to remove records about backups from the Veeam Backup & Replication console and configuration database, you can use the Remove from configuration operation.

When you remove a backup from the configuration, backup files (.VAB, .VASM) remain on the backup repository. You can import backup files later and restore from them.

To remove a backup from configuration:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, select the necessary backup.
4. Press and hold the [Ctrl] key, right-click the backup and select Remove from configuration.

[![Remove from Configuration](images/plugins_remove_from_config_maxdb.webp)](images/plugins_remove_from_config_maxdb.webp "Remove from Configuration")

Viewing Backup Properties

To review what data Veeam Plug-In has backed up, check the backup properties in the Veeam Backup & Replication console.

To view backup properties:

1. Open the Home view.
2. In the inventory pane, expand the Backups node and select Disk. To view properties of backups stored on tape, select Tape.
3. In the working area, right-click the backup and select Properties.

The backup properties window displays the following information about the content of a backup file:

* Objects — databases backed up by Veeam Plug-In.
* Files — backup files of a selected database that are stored in the backup repository.

To find a specific item in a list, use the search field. To copy the path to a backup file, use the Copy path button.

[![Backup in Veeam Backup & Replication](images/plugins_view_properties_maxdb.webp)](images/plugins_view_properties_maxdb.webp)

Page updated 2026-07-29

