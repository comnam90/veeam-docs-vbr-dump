---
title: "Required Job Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vemdb_job_settings.html"
last_updated: "11/3/2025"
product_version: "13.0.1.1071"
---

# Required Job Settings

In this article

You can create backups of MongoDB replica sets using application backup jobs in Veeam Backup & Replication.

To create a MongoDB application backup job, do the following:

1. Add the source MongoDB replica set to a protection group. For more information, see [Creating Protection Group for MongoDB](protection_group_create_mongo.md).
2. Create an application backup policy using the protection group. For more information, see [Creating Application Backup Policy](mongo_policy_create.md).

To be able to restore your MongoDB data to a point-in-time state, make sure to configure oplog backup. For more information, see [Processing Settings](mongo_policy_preferences_processing.md).

After the backup is successfully created, you can use Veeam Explorer for MongoDB to restore your MongoDB data.

Page updated 11/3/2025

Page content applies to build 13.0.1.1071
