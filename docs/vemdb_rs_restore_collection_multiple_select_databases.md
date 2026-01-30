---
title: "Step 5. Select Databases"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vemdb_rs_restore_collection_multiple_select_databases.html"
last_updated: "11/4/2025"
product_version: "13.0.1.1071"
---

# Step 5. Select Databases


At this step of the wizard, select the databases that you want to recover.

To quickly find the necessary databases, use the search field or sort the databases by name.

In the New Name column, you can specify a new name for the selected database on the target server. If the renamed database does not exist on the target server, it will be created.

|  |
| --- |
| Note |
| Consider the following:   * When restoring the admin database to another replica set, both the source and target replica sets must have the same user. * To restore collections from the config and local databases, make sure to launch the restore wizard from the necessary database, instead of the replica set. * You cannot restore system collections from the admin, config and local databases to the original location or the equivalent databases on another server. To restore collections from these databases, specify another target database or create a new one. |

[![Selecting Databases](images/vemdb_rs_restore_collection_multiple_select_databases.webp)](images/vemdb_rs_restore_collection_multiple_select_databases.webp "Selecting Databases")


