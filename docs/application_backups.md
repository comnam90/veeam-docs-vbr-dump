---
title: "Managing Application Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/application_backups.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Managing Application Backups


You can perform administration tasks with backups created on a Veeam backup repository by application backup policies configured in Veeam Backup & Replication. For such backups, Veeam Backup & Replication allows you to perform the same set of operations as for backups created with application policies configured directly on a protected computer. You can perform the following tasks:

* [Restore a database item from an application backup using Veeam Explorer](application_backups_restore_with_explorer.md).

* [Create a recovery token for a computer](application_backups_recovery_token.md).
* [Delete an application backup from configuration](application_backups_remove_from_configuration.md).
* [Delete an application backup from disk](application_backups_delete.md).
* [Create a backup copy](application_backups_copy.md).

|  |
| --- |
| Note |
| Backups created by Veeam Plug-Ins cannot be used as a source for file to tape jobs. For information about backup to tape support, see [Backup to Tape](plugins_rman_backup_to_tape.md). |

Page updated 2026-07-10

