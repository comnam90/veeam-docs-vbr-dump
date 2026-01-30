---
title: "Getting Started"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_getting_started.html"
last_updated: "11/21/2024"
product_version: "13.0.1.1071"
---

# Getting Started


To protect MongoDB Backup databases with Veeam Backup & Replication, perform the following operations:

1. Create a protection group for MongoDB. For more information, see [Creating Protection Group for MongoDB](protection_group_create_mongo.md).
2. Create an application backup policy to define what data you want to back up and configure backup settings. For more information, see [Creating Application Backup Policy](mongo_policy_create.md).
3. Run the backup job to create a database backup and store it in the backup repository. To learn more, see [Starting and Stopping Application Backup Policy](mongo_policy_manage_start_stop.md#start).
4. In case of a disaster, you can restore data from a backup with Veeam Explorer for MongoDB. For more information, see [Restoring with Veeam Explorer for MongoDB](mongo_restore.md).


