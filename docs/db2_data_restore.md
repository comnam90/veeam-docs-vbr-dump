---
title: "Data Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_data_restore.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Data Restore


With the configured Veeam Plug-In for IBM Db2, you can restore IBM Db2 databases from Veeam Plug-In backups that reside on Veeam backup repositories. Restore operations are performed on the Veeam Plug-In side.

Depending on the available type of Veeam Plug-In backups that will be the source for the restored databases, you can perform the following restore operations:

* Restoring from backup.

Restore IBM Db2 databases from a Veeam Plug-In backup to the original server by using the db2 restore command. For details, see [Restore to Original Server](db2_restore_to_original.md).

You can also restore IBM Db2 databases from a Veeam Plug-In backup to another server. For details, see [Restore to Another Server](db2_restore_to_another.md).

* Restoring from a backup copy.

Restore IBM Db2 databases from backup copies created for Veeam Plug-In backups. For details, see [Restore from Backup Copy](db2_restore_from_backup_copy.md).

Depending on the location of Veeam Plug-In backups that will be the source for the restored databases, you can also perform the following restore operations:

* Restoring from simple repositories.

Restore IBM Db2 databases from Veeam Plug-In backups stored on supported types of repositories. For details, see [Veeam Backup Repositories](db2_backup_repos.md).

* Restoring from hardened repositories.

Restore IBM Db2 databases from hardened repositories by creating new backup job metadata files (.VACM) with data from available backup metadata files (.VASM). For details, see [Restore from Hardened Repository](db2_restore_from_hardened.md).


