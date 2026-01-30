---
title: "Oplog Backup"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_oplog_backup.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# Oplog Backup


You can use MongoDB Backup to create transactionally consistent backups of MongoDB replica sets.

To ensure transactional consistency, these backups must include the operations log (oplog). The oplog is a special collection in the MongoDB database that stores all operations that modify database data. The oplog backup helps to maintain data consistency across nodes. It also enables you to restore a MongoDB database items to a specific state between scheduled backups. For more details on MongoDB oplog backups, see the [MongoDB documentation](https://www.mongodb.com/docs/manual/core/replica-set-oplog/).

To back up the oplog, Veeam Backup & Replication uses a MongoDB log backup job. This log backup job runs alongside the application backup policy and stores the oplog collection along with the database backup. You can configure the MongoDB log backup job as a setting of the application backup policy. For details, see [Processing Settings](mongo_policy_preferences_processing.md).

How MongoDB Log Backup Job Works

If you configured an application backup job to create log backups, Veeam Backup & Replication performs log backup in the following way:

1. After the application backup policy with the enabled log backup is created, Veeam Backup & Replication creates a separate MongoDB log backup job for each replica set in a backup scope.
2. The MongoDB log backup job waits for Veeam Backup & Replication to create a full backup. For details, see [Application Backup Policies](mongo_backup_job.md).
3. After a full backup is created, Veeam Backup & Replication initiates the oplog backup in the interval set in the application backup policy settings. By default, the oplog backup job runs every 15 minutes. In the specified interval, Veeam components on the machine with the MongoDB database work in the following way:

1. Veeam Mongo Backup Plug-In detects the oplog collection and the oplog operations to back up. To select which operations from the oplog collection to back up, plug-in uses Timestamp collected during the full backup creation. For details on timestamps, see [MongoDB documentation](https://www.mongodb.com/docs/manual/reference/bson-types/#timestamps).
2. Veeam Mongo Agent transfers the selected oplog operations to the target repository and stores them in dedicated log backup files. For details, see [Backup Files](mongo_backup_files.md).

1. Once the log backup files are created, Veeam Backup & Replication applies a retention policy specific for log backup files. For details, see [Processing Settings](mongo_policy_preferences_processing.md).

1. After the backup run is completed, Veeam Backup & Replication waits for the next run according to the specified interval.

Related Task

[Specifying MongoDB Processing Settings](mongo_policy_preferences_processing.md)


