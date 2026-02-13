---
title: "Step 2. Specify Restore Point"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_plugin_single_tas_specify_restore_point.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Step 2. Specify Restore Point


At this step of the wizard, select a restore point from which you want to restore your database.

To quickly find the necessary restore point, you can sort the restore points according to the backup time, backup type, the backup set to which they belong and the description.

|  |
| --- |
| Note |
| When you restore the master database, only full backups are available. Differential backups rely on transaction log backups, which are not supported for the master database. |

![Step 2. Specify Restore Point](images/vesql_restore_plugin_single_specify_restore_point.webp "Specifying Restore Point")


