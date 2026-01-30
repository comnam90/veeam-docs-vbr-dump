---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/restore_entire_bucket_byb.html"
last_updated: "3/18/2025"
product_version: "13.0.1.1071"
---

# Before You Begin


Before you restore the entire bucket or container, consider the following:

* You can restore the bucket or container from a backup that has at least one successfully created restore point.
* The object storage where you plan to save the restored bucket or container must be added to the backup infrastructure.
* Veeam Backup & Replication does not support restore of tags if you restore data from Microsoft Azure Blob storage to Amazon S3 object storage and S3 compatible object storage.
* Veeam Backup & Replication does not support Instant recovery of data previously backed up with object storage backup jobs.
* [For Microsoft Azure Blob storage] Veeam Backup & Replication does not support the following restore scenarios if you change the Azure Storage access tier of blocks to the archive access tier:

* Restore data [to the original location or to another location with the overwrite option](restore_entire_bucket_restore_options.md#overwrite).
* Restore individual objects or versions with the overwrite option.

* The target location where you want to restore the bucket or container has the following limitations:

* You can restore backups of Amazon S3 and s3 compatible only to a new bucket located either in Amazon S3 or S3 compatible object storage.
* You can restore backups of Microsoft Azure Blob Storage only to a new container in Microsoft Azure Blob Storage.

|  |
| --- |
| Tip |
| If you want to restore these objects, you must change the access tier to hot, cool or cold access tiers. If you do not want to restore these objects, you need to remove them from your Azure container. |


