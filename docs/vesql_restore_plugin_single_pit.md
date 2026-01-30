---
title: "Restoring Point-in-Time State"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_plugin_single_pit.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Restoring Point-in-Time State


You can restore a database backed up with Veeam Plug-In for Microsoft SQL Server as of a point-in-time state in your backup file.

The data will be restored in the following manner:

* Database files will be copied to the original location and then mounted to the original Microsoft SQL Server.
* If a database with the same name already exists on a target Microsoft SQL Server, it will be replaced with the database from a backup file.

To restore SQL Server databases as of a point-in-time state, use the Restore wizard.

1. [Launch the Restore wizard](vesql_restore_plugin_single_pit_wizard.md).
2. [Specify a restore point](vesql_restore_plugin_single_pit_specify_restore_point.md).
3. [Specify a point-in-time state](vesql_restore_plugin_single_pit_specify_pit.md).


