---
title: "Data Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_data_restore.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Data Restore


With the configured Veeam Plug-In for Oracle RMAN, you can restore Oracle databases from Veeam Plug-In backups that reside on Veeam backup repositories.

You can use the built-in Oracle functionality or Veeam Explorer for Oracle to restore databases. Restore operations are performed on the Oracle side.

|  |
| --- |
| Tip |
| For details on how to use Veeam Explorer for Oracle for restore operations, see the [Restoring Oracle RMAN Backups](https://helpcenter.veeam.com/docs/vbr/explorers/rman_backups.html?ver=13) section of the Veeam Explorers User Guide. |

Depending on the available type of Veeam Plug-In backups that will be the source for the restored databases, you can perform the following restore operations:

* Restoring from backup.

Restore Oracle databases from a Veeam Plug-In backup to the original server by using the built-in Oracle functionality. For details, see [Restore to Original Server](restore_rman.md).

You can also restore Oracle databases from a Veeam Plug-In backup to another server. For details, see [Restore to Another Server](restore_other_server_rman.md).

* Restoring from a backup copy.

Restore Oracle databases from backup copies created for Veeam Plug-In for Oracle RMAN backups. For details, see [Restore from Backup Copy](restore_from_copy.md).

Depending on the location of Veeam Plug-In backups that will be the source for the restored databases, you can also perform the following restore operations:

* Restoring a control file from autobackup.

Restore the Oracle database control file if you want to restore the database to a new location where the control file does not exist, or if the database control file is lost or corrupted. For details, see [Restore of Control File from Autobackup](controlfile_restore.md).

* Restoring from hardened repositories.

Restore Oracle databases from hardened repositories by creating new backup job metadata files (.VACM) with data from available backup metadata files (.VASM). For details, see [Restore from Hardened Repository](restore_from_immutable_rman.md).


