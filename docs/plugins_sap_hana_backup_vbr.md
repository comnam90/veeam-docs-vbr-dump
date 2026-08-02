---
title: "Backup in Veeam Backup & Replication"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_hana_backup_vbr.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Backup in Veeam Backup & Replication


|  |
| --- |
| Tip |
| If you want to manage backups created by Veeam Plug-In operating in the managed mode, see [Managing Application Backups](application_backups.md). |

After a backup job session completes successfully, Veeam Backup & Replication creates a backup in the backup repository. You can use the Veeam Backup & Replication console to restore using Veeam Explorer for SAP HANA, create recovery token, delete the backup, and view the backup properties.

Restoring with Veeam Explorer for SAP HANA

You can restore SAP HANA databases from Veeam Plug-In backups in the Veeam Backup & Replication console. To restore SAP HANA databases Veeam Backup & Replication uses Veeam Explorer for SAP HANA. For details, see the [SAP HANA Data Restore](https://helpcenter.veeam.com/docs/vbr/explorers/vehana_restore.html?ver=13) section of the Veeam Explorers User Guide.

|  |
| --- |
| Tip |
| To perform restore from SAP HANA databases, you can also use Veeam Explorer cmdlets. For details, see the [Veeam Explorer for SAP HANA](https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veeam_explorer_for_sap_hana.html?ver=13) section of the Veeam Explorers PowerShell Reference. |

[![Restore From SAP HANA Backup](images/plugins_restore_saphana.webp)](images/plugins_restore_saphana.webp "Restore From SAP HANA Backup")

Creating Recovery Token

If you want to recover a database from a specific backup, you can use the Create recovery token operation.

You can generate a recovery token on the Veeam Backup & Replication side. Then, on the SAP HANA server side, use this token to get access to the backup and recover the database stored in it. To learn more about operations on the SAP HANA server side, see [Restore to Another Server](restore_saphana_other_server.md#token).

Before creating a recovery token, consider the following prerequisites and limitations:

* Recovery tokens stay valid for 24 hours.
* You can recover data only from the backup for which the recovery token is generated.
* During recovery, Veeam Backup & Replication does not stop backup operations.
* You cannot create a recovery token for a whole backup copy job, but you can create a recovery token for individual objects included in a backup copy job.

To create a recovery token on the Veeam Backup & Replication side:

1. Open the Home view.
2. In the inventory pane, click Backups.
3. In the working area, right-click the backup and select Create recovery token.

You can create a recovery token for several backups. To do this, press and hold [Ctrl], select multiple backups, right-click one of the selected backups and select Create recovery token.

1. In the Create Recovery Token window, click Create.

|  |
| --- |
| Tip |
| Alternatively, you can create and modify the existing recovery token using the PowerShell console. To learn more, see the [Working with Tokens](https://helpcenter.veeam.com/docs/vbr/powershell/tokens.html?ver=13) section in the Veeam PowerShell Reference. |

[![Backup in Veeam Backup & Replication](images/plugins_create_re_token_hana.webp)](images/plugins_create_re_token_hana.webp)

Deleting Backups Manually

In the main scenario, when using Veeam Plug-In for SAP HANA, you must configure the retention policy using native SAP HANA tools. For details on the SAP HANA housekeeping options, see [Deleting Backups Using SAP HANA Tools](retention_sap_tools.md#studio).

If you have lost the backup catalog, you can delete the backups manually from Veeam backup repositories using the Veeam Backup & Replication console.

|  |
| --- |
| Note |
| If you remove backups from a backup repository manually, the backup catalog will not be updated. |

To remove a backup from a backup repository, do the following:

1. In the Veeam Backup & Replication console, open the Home view.
2. In the Inventory pane, select Backups.
3. In the working area, right-click the backup job object name and select Remove from > Disk.

[![Delete from Disk](images/plugins_sap_hana_backups_delete.webp)](images/plugins_sap_hana_backups_delete.webp "Delete from Disk")

Removing Backups from Configuration

If you want to remove records about backups from the Veeam Backup & Replication console and configuration database, you can use the Remove from configuration operation.

When you remove a backup from the configuration, backup files (.VAB, .VASM) remain on the backup repository. You can import backup files later and restore data from them.

To remove a backup from configuration:

1. Open the Home view.
2. In the inventory pane, select Backups.
3. In the working area, select the necessary backup.
4. Press and hold the [Ctrl] key, right-click the backup and select Remove from > Configuration.

[![Delete from Configuration](images/plugins_remove_from_config_hana.webp)](images/plugins_remove_from_config_hana.webp "Delete from Configuration")

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

[![Backup in Veeam Backup & Replication](images/plugins_properties_hana.webp)](images/plugins_properties_hana.webp)

Page updated 2026-07-29

