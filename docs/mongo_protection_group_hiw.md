---
title: "Protection Group for MongoDB"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_protection_group_hiw.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# Protection Group for MongoDB


In Veeam Backup & Replication, computers that you want to protect with Veeam Plug-Ins or Veeam Agents are organized into protection groups. A protection group is a container in the Veeam Backup & Replication inventory aimed to combine protected computers of a specific type.

To start managing computers with MongoDB using Veeam Backup & Replication, you need to create a protection group for MongoDB in the inventory and specify computers that you want to protect in the protection group settings. You can create one or more protection groups depending on the size and complexity of your infrastructure. Protection groups appear under the Physical Infrastructure node in the Inventory view of the Veeam Backup & Replication console.

Keep in mind the following:

* The protection group for MongoDB is designed to back up MongoDB replica sets. Other protection groups cannot create a volume-level backup of MongoDB data.
* You must add nodes of the same MongoDB replica set to the same protection group.

Veeam Backup & Replication connects to discovered computers using an administrative account or a certificate specified in the protection group settings. To learn more, see [Creating Protection Group for MongoDB](protection_group_create_mongo.md).

After you create a protection group, Veeam Backup & Replication starts the rescan job to connect to computers added to the protection group and perform the required operations on these computers. To learn more, see [Rescan Job](mongo_rescan_job.md).


