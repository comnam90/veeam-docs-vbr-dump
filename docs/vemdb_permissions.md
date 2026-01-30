---
title: "Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vemdb_permissions.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Permissions


The following table lists the required permissions for user accounts to restore MongoDB data.

| Operation | Required Roles and Permissions |
| --- | --- |
| Veeam Explorer for MongoDB launch | The account used to run Veeam Explorer for MongoDB must meet the following requirements:   * The account must be a member of the local Administrators or Users group on the machine where Veeam Explorer for MongoDB is running.  * The account must have one of the following roles on the backup server:  * The Veeam Backup Administrator or Veeam Restore Operator default roles. * A custom role with at least the Manage restores permission and the Veeam Explorer for MongoDB restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles). |
| Restore, Publish | When restoring collections and publishing instances make sure to configure user accounts as follows:   * The account used to authenticate to the target MongoDB replica set must have the root MongoDB role. For more information, see the [MongoDB Manual](https://www.mongodb.com/docs/manual/reference/built-in-roles/#mongodb-authrole-root). * The account used to authenticate to the primary node of the MongoDB replica set must be a Linux user with root privileges on the target machine.   When restoring an entire instance, the account used to authenticate to the target Linux machine with MongoDB must be a Linux user with root privileges on the target machine. |


