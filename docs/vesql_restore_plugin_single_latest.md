---
title: "Restoring Latest State"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_plugin_single_latest.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Restoring Latest State

In this article

You can restore a database as of the latest state in your backup file.

The data will be restored in the following manner:

* Database files will be copied to the original location and then mounted to the original Microsoft SQL Server.
* If a database with the same name already exists on a target Microsoft SQL Server, it will be replaced with the database from a backup file.

To restore the latest available state of a Microsoft SQL Server database, do the following:

1. In the navigation pane, select a database.
2. On the Database tab, select Restore Database > Restore latest state to <original\_location>.

Alternatively, you can right-click a database and select Restore latest state to <original\_location>.

|  |
| --- |
| Note |
| Before the restore process begins, you will be prompted to enter the source machine credentials. |

[![Restoring Latest State](images/vesql_restore_plugin_single_latest.webp)](images/vesql_restore_plugin_single_latest.webp "Restoring Latest State")

Page updated 11/4/2025

Page content applies to build 13.0.1.1071
