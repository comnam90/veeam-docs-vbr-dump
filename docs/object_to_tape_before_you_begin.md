---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/object_to_tape_before_you_begin.html"
last_updated: "2/4/2026"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you create an object to tape job, consider the following:

* The object storage backup to tape functionality consumes Veeam instance licenses. However, if you upgrade to Veeam Backup & Replication 12 from the previous versions, you will have a grace period of 3 months during which your object to tape jobs will not consume license instances. For more information, see [Instance Consumption for Object Storage Backup, File Backup and File to Tape Jobs](nas_licensing.md).

* You must configure the object storage permissions for the user account which Veeam Backup & Replication will use to authenticate and get access to the object storage. For more information on user permissions, see [Object Storage Permissions](#permissions).
* You must configure one or more regular media pools with the necessary media set and retention settings.
* You must load tapes to the tape device and configure the target media pool so that it has access to them. If the media pool has no available tape, the tape job will retry for 72 hours and then terminate.

|  |
| --- |
| Note |
| Consider the following:   * Object to tape jobs can back up only object storage data and cannot protect other workloads. You need to create other backup to tape jobs to be able to process other types of data. For more information, see [File Backup to Tape](file_to_tape_jobs.md) and [Backup to Tape](backup_to_tape.md). * Backups produced by [Veeam Backup for Microsoft 365](https://helpcenter.veeam.com/docs/vbo365/guide/vbo_introduction.html) and stored in object storage repositories cannot be a source for object to tape jobs and are skipped from processing. For more information, see the [Object Storage](object_to_tape_objects.md) step of the New Object to Tape Job wizard. |

Object Storage Permissions

The following permissions for the object storage are required for an object to tape job:

|  |
| --- |
| GetBucketAccelerateConfigurationGetBucketAcl |


