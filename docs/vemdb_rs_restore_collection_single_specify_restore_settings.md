---
title: "Step 2. Specify Restore Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vemdb_rs_restore_collection_single_specify_restore_settings.html"
last_updated: "8/29/2024"
product_version: "13.0.1.1071"
---

# Step 2. Specify Restore Settings


At this step of the wizard, you can choose whether to restore your MongoDB data to the original or to another replica set.

* The Restore to the original location option allows you to restore your MongoDB data to the original replica set.
* The Restore to a different location option allows you to restore your MongoDB data to another replica set.

* In the Target instance field, enter the DNS name or IP address of a node of the target replica set and the port used to connect to the target MongoDB instance.
* In the Target database field, specify the target database to which the collection will be restored.

|  |
| --- |
| Note |
| You cannot restore system collections from the admin, config and local databases to the original location or the equivalent databases on another MongoDB replica set. To restore system collections, specify a different target database or create a new one. |

[![Specifying Restore Settings](images/vemdb_rs_restore_collection_single_specify_restore_settings.webp)](images/vemdb_rs_restore_collection_single_specify_restore_settings.webp "Specifying Restore Settings")


