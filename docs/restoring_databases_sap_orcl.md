---
title: "Database Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restoring_databases_sap_orcl.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Database Recovery


With the configured Veeam Plug-In you can restore Oracle databases from the backups that reside on backup repositories. All restore operations are performed on the SAP BR\*Tools side.

Keep in mind that examples provided in this section are for demonstration purposes only. To see the full restore functionality of SAP BR\*Tools, see the [BR\*Tools for Oracle DBA Guide](https://help.sap.com/doc/saphelp_nw74/7.4.16/en-us/46/e42438f63966c6e10000000a1553f7/content.htm?loaded_from_frameset=true).

|  |
| --- |
| Note |
| To restore data from a backup, the version of Veeam Plug-In must be the same or later than the version that created the backup. Restore with an earlier version of Veeam Plug-In from a backup created with a later version is not supported and may cause the restore to fail. This limitation applies to build numbers, not only major versions: for example, you cannot use Veeam Plug-In build 13.0.1.1071 to restore data from a backup created with build 13.0.1.2067. |

To learn how to recover Oracle databases from backups created by Veeam Plug-In for SAP on Oracle, see the following subsections:

* [Restore Oracle Databases](restore_sap_orcl.md)
* [Restore Redo Logs](restore_sap_orcl_logs.md)
* [Restore from Hardened Repository](restore_from_immutable_sap_orcl.md)

Page updated 2026-07-30

