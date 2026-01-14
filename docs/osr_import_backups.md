---
title: "Importing Object Storage Backups"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/osr_import_backups.html"
last_updated: "5/27/2024"
product_version: "13.0.1.1071"
---

# Importing Object Storage Backups

In this article

In case a disaster strikes and your Veeam Backup & Replication with a scale-out backup repository becomes unavailable, you can import into another Veeam Backup & Replication infrastructure backups located in object storage repositories added as performance, capacity or archive extents of the scale-out backup repository. Once you add the necessary object storage repositories in Veeam Backup & Replication infrastructure, you can import backups and they will become available for data recovery operations.

|  |
| --- |
| Note |
| If you want to import backups located in standalone object storage repositories or that are added as performance extents of a scale-out backup repository, use the [Rescan Backup Repositories](rescanning_backup_repositories.md) option. |

Consider the following:

* The Import Backups option is available only if the object storage is not a part of the scale-out backup repository.
* Before you start importing backups, make sure to [add the object storage repository](new_object_storage.md) that stores data you want to import.
* If you have imported backups from the object storage repository, you will not be able to use it as a standalone repository when you configure a job or as an extent of a scale-out backups repository. To be able to do it, you will need to [detach](osr_detach_backups.md) this object storage.
* The Import Backups option is applicable only to the [Capacity Tier backups](capacity_tier.md) and [Archive Tier backups](archive_tier.md). It does not support the [unstructured data backups](unstructured_data_backup.md).

To import backups, do the following:

1. [Launch the Import Backups wizard](osr_new_import_wizard.md).
2. [Specify password](osr_import_password.md).
3. [Wait for import](osr_wait_import.md).
4. [Finish working with the wizard](osr_finish.md).

Page updated 5/27/2024

Page content applies to build 13.0.1.1071
