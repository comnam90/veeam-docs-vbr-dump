---
title: "Restoring with Veeam Explorer for MongoDB"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_restore.html"
last_updated: "12/10/2025"
product_version: "13.0.1.1071"
---

# Restoring with Veeam Explorer for MongoDB


You can restore MongoDB data from backups created with the MongoDB Backup feature of Veeam Backup & Replication. Veeam Backup & Replication supports restore of entire instances or certain collections to the original or to another location. Veeam Backup & Replication restores MongoDB data to the time when the restore point was created.

|  |
| --- |
| Important |
| It is recommended to create a full backup immediately after you restore a database. All subsequent log or differential backups of the restored database will be based on this full backup. This action helps prevent potential data loss. |

To restore MongoDB data, Veeam Backup & Replication uses Veeam Explorer for MongoDB for restore operations. Before you perform database restore, review considerations and limitations for Veeam Explorer for MongoDB listed in [Considerations and Limitations](vemdb_considerations.md).

To learn more about restore operations, see the following sections:

* [Restoring Single Collection](vemdb_rs_restore_collection_single.md)

* [Restoring Multiple Collectionl](vemdb_rs_restore_collection_multiple.md)

* [Restoring Instance](vemdb_rs_restore_instance.md)


