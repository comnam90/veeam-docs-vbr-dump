---
title: "Restoring from SQL Plug-in Backups"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_plugin.html"
last_updated: "11/3/2025"
product_version: "13.0.1.1071"
---

# Restoring from SQL Plug-in Backups


This section explains how to restore data from backups created with Veeam Plug-In for Microsoft SQL Server. For more information, see [Veeam Plug-In for Microsoft SQL Server](mssql_plugin.md).

Before you restore data from SQL plug-in backups, make sure that your infrastructure is set up properly. In particular, note that when you restore from a SQL plug-in backup to another server and Veeam Plug-In for Microsoft SQL Server on the target server does not have access to the source backup, you must configure the plug-in authentication settings. For more information, see [Considerations and Limitations](vesql_considerations.md).

In This Section

* [Restoring Single Database](vesql_restore_plugin_single.md)

* [Restoring Multiple Databases](vesql_restore_plugin_multiple.md)
* [Canceling Restore](vesql_restore_plugin_cancel.md)


