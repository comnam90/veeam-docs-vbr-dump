---
title: "Overview"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_about.html"
last_updated: "12/10/2025"
product_version: "13.0.1.1071"
---

# Overview

In this article

MongoDB Backup uses the backup functionality of Veeam Backup & Replication and Veeam Agent for Linux and stores backups in Veeam backup repositories. For details, see [Solution Architecture](mongo_hiw.md).

With the configured application backup policy, you can perform full and incremental backups of MongoDB data. Use MongoDB Backup to back up databases in the following cases:

* If you want to store MongoDB backups in hardened and object storage repositories.
* If you want to perform centralized management of MongoDB backups.
* If you want to restore individual instances and collections.

You must use the Veeam Backup & Replication console for the following tasks:

* Discover computers with MongoDB data and deploy Veeam components on them. For details, see [Computer Discovery and Veeam Components Deployment](mongo_discovery_and_deployment.md).
* Configure an application backup policy that contains instructions for Veeam components on how to create MongoDB backups. For details, see [Application Backup Policies](mongo_backup_job.md).
* Perform and manage the MongoDB backup operations. For details, see [Data Backup](mongo_data_backup.md) and [Oplog Backup](mongo_oplog_backup.md).
* In case of malware activity or unplanned actions, restore MongoDB items from the backups stored in Veeam backup repositories. You can restore entire instances or certain collections from a MongoDB backup. Veeam Backup & Replication supports restoring instances and collections to the original or another location. For details, see [Data Restore](mongo_data_restore.md). Alternatively, you can get access to the data by publishing the entire MongoDB instance. For details, see [Data Publishing](mongo_data_publishing.md).

|  |
| --- |
| Tip |
| If you want to protect the whole server where your databases are located, you can use the image-level backup functionality of [Veeam Backup & Replication](backup.md) or [Veeam Agent for Linux](https://helpcenter.veeam.com/docs/agentforlinux/userguide/overview.html?ver=60). In case of image-level backup, application-aware processing of MongoDB data is not available. |

Page updated 12/10/2025

Page content applies to build 13.0.1.1071
