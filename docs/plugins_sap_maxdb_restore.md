---
title: "Performing Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_maxdb_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Restore


With the configured Veeam Plug-In you can restore SAP MaxDB databases from the backups that reside in the Veeam backup repository. All restore operations are performed on the Veeam Plug-In side.

|  |
| --- |
| Note |
| To restore data from a backup, the version of Veeam Plug-In must be the same or later than the version that created the backup. Restore with an earlier version of Veeam Plug-In from a backup created with a later version is not supported and may cause the restore to fail. This limitation applies to build numbers, not only major versions: for example, you cannot use Veeam Plug-In build 13.0.1.1071 to restore data from a backup created with build 13.0.1.2067. |

For details about SAP MaxDB database restore, see [SAP MaxDB documentation](https://maxdb.sap.com/doc/7_7/d4/fba2eae7ba441c88771db88768d99e/frameset.htm).

In This Section

* [Restore to Original Server](plugins_sap_maxdb_restore_db.md)
* [Restore to Another Server](plugins_sap_maxdb_restore_to_another.md)
* [Restore from Hardened Repository](plugins_sap_maxdb_restore_from_hard.md)

|  |
| --- |
| Tip |
| * This guide provides examples for Database Manager CLI. Apart from Database Manager CLI, you can perform backup operations using MaxDB Studio. * You can restore SAP MaxDB databases from backup copies created for Veeam Plug-In for SAP MaxDB backups. The procedure of database restore from a backup copy is the same as database restore to another server. For more information, see [Restore to Another Server](plugins_sap_maxdb_restore_to_another.md). |

Page updated 2026-07-30

