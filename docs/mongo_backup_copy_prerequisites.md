---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/mongo_backup_copy_prerequisites.html"
last_updated: "12/4/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you create a backup copy job, check the prerequisites and limitations:

* Backup infrastructure components that will take part in the backup copy process must be added to the backup infrastructure and properly configured. These include source and target backup repositories between which backups must be copied.
* The target backup repository must have enough free space to store copied backups. To receive alerts about low space on the backup repository, configure global notification settings. For more information, see [Specifying Global Notification Settings](global_notifications.md).

* If you plan to create backup copy job for a backup created with MongoDB Backup and target this backup copy job at the scale-out backup repository, note that Veeam Backup & Replication can store files of such backup copy job in the performance tier and capacity tier. The archive tier are not supported as a target for backup copies containing MongoDB backups.
* Veeam Cloud Connect repositories are not supported as a target for backup copies containing MongoDB backups.

Page updated 12/4/2025

Page content applies to build 13.0.1.1071
