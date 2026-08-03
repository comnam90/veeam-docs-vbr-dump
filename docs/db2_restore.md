---
title: "Performing Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/db2_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Restore


With the configured Veeam Plug-In you can restore IBM Db2 databases from the backups that reside in the Veeam backup repository. All restore operations are performed on the Veeam Plug-In side.

|  |
| --- |
| Note |
| To restore data from a backup, the version of Veeam Plug-In must be the same or later than the version that created the backup. Restore with an earlier version of Veeam Plug-In from a backup created with a later version is not supported and may cause the restore to fail. This limitation applies to build numbers, not only major versions: for example, you cannot use Veeam Plug-In build 13.0.1.1071 to restore data from a backup created with build 13.0.1.2067. |

In This Section

* [Get Backup Time Stamp](db2_restore_get_time_stamp.md)
* [Restore to Original Server](db2_restore_to_original.md)
* [Restore to Another Server](db2_restore_to_another.md)
* [Restore from Backup Copy](db2_restore_from_backup_copy.md)
* [Restore from Hardened Repository](db2_restore_from_hardened.md)

Page updated 2026-07-30

