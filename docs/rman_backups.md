---
title: "Restoring from RMAN Plug-in Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/rman_backups.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Restoring from RMAN Plug-in Backups


This section explains how to restore Oracle data from backups created with Veeam Plug-In for Oracle RMAN. You can also export recovery scripts for later restore operations.

For more information about configuring the plug-in and creating backups, see [Veeam Plug-In for Oracle RMAN](rman_plugin.md).

Before you restore data from RMAN plug-in backups, make sure that your infrastructure is set up properly. In particular, note that when you restore from an RMAN plug-in backup to another server and Veeam Plug-In for Oracle RMAN on the target server does not have access to the source backup, you must configure the plug-in authentication settings. For more information, see [Considerations and Limitations](veor_considerations.md#restore-rman).

In This Section

* [Database Restore](rman_backups_restore.md)
* [Recovery Script Export](rman_recovery_scripts_export.md)

Page updated 2026-07-17

