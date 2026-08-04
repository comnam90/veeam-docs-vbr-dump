---
title: "Database Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/oracle_db_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Database Recovery


With the configured Veeam Plug-In for Oracle RMAN, you can perform all kinds of database restore operations available in Oracle RMAN. You can also restore from database backups in the Veeam Backup & Replication console.

|  |
| --- |
| Note |
| To restore data from a backup, the version of Veeam Plug-In must be the same or later than the version that created the backup. Restore with an earlier version of Veeam Plug-In from a backup created with a later version is not supported and may cause the restore to fail. This limitation applies to build numbers, not only major versions: for example, you cannot use Veeam Plug-In build 13.0.1.1071 to restore data from a backup created with build 13.0.1.2067. |

In This Section

* [Restore to Original Server](restore_rman.md)
* [Restore to Another Server](restore_other_server_rman.md)
* [Restore from Backup Copy](restore_from_copy.md)
* [Restore with Veeam Explorer for Oracle](restore_veor.md)
* [Restore of Control File from Autobackup](controlfile_restore.md)
* [Restore from Hardened Repository](restore_from_immutable_rman.md)

Page updated 2026-07-30

