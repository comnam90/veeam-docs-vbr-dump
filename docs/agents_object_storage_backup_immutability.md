---
title: "Backup Immutability"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_object_storage_backup_immutability.html"
last_updated: "5/23/2025"
product_version: "13.0.1.1071"
---

# Backup Immutability

In this article

If you store your backup files in an object storage repository, Veeam Agent allows you to protect backup data from deletion or modification by making that data temporarily immutable. It is done for increased security: immutability protects data in your recent backups from loss as a result of attacks, malware activity or any other injurious actions.

|  |
| --- |
| Important |
| Backup immutability uses native capabilities of object storage. Enabling this feature may result in additional API and storage charges from the storage provider. |

Supported Object Storage Types

Veeam Agent supports backup immutability for the following object storage types:

* Veeam Data Cloud Vault
* Amazon S3
* S3 compatible storage that supports S3 Object Lock
* Microsoft Azure Blob Storage
* Google Cloud Storage

* Wasabi Cloud Storage
* IBM Cloud
* 11:11 Cloud Object Storage

Before You Begin

Before you configure immutability for Veeam Agent backups, you must prepare the target storage account. Depending on the selected object storage type, perform the following actions:

* [S3 Compatible and Amazon S3 storage] When you create an S3 bucket, you must enable the S3 Versioning and S3 Object Lock features for the bucket. For more information, see [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/managing-storage.html).

* [S3 Compatible and Amazon S3 storage] After you create an S3 bucket with Object Lock enabled, make sure that the default retention is disabled to avoid unpredictable system behavior and data loss. To disable the default retention, edit the Object Lock retention settings as described in [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock-console.html).

* [Microsoft Azure Blob storage] You must enable blob versioning and version-level immutability support for the Azure container. For more information, see [Microsoft documentation](https://learn.microsoft.com/en-us/azure/storage/blobs/data-protection-overview).
* [Google Cloud Storage] When you create a bucket, you must enable the Object Versioning and Object Retention Lock features for the bucket. For more information on Object Versioning, see [Google Cloud documentation](https://cloud.google.com/storage/docs/object-versioning). For more information on Object Retention Lock, see [Google Cloud documentation](https://cloud.google.com/storage/docs/object-lock).

Consider the following about backup immutability:

* The effective immutability period consists of the user-defined immutability period and the block generation period automatically appended by Veeam Agent. For more information, see [How Backup Immutability Works](agents_backup_immutability_hiw.md) and [Block Generation](agents_immutability_block_generation.md).
* [S3 Compatible and Amazon S3 storage] Veeam Agent will use the compliance retention mode for each uploaded object. For more information on retention modes of S3 Object Lock, see [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html).
* [Microsoft Azure Blob storage] Do not enable immutability for already existing containers in the Microsoft Azure Portal. Otherwise, Veeam Agent will not be able to process these containers properly and it may result in data loss.

Configuring Backup Immutability

When you create the backup job that is targeted at an object storage, the minimum immutability period must be specified in the settings of the object storage repository. For more information, see [Adding Object Storage Repositories](new_object_storage.md).

Backup Immutability and Retention Policy

Veeam Agent removes obsolete restore points based on the defined backup retention policy, but only if such restore points are no longer immutable. If data associated with an obsolete restore point is still immutable, such restore point will remain in the backup chain and in the repository until its immutability period is over. After that, such restore point is automatically removed from the backup chain and storage.

Page updated 5/23/2025

Page content applies to build 13.0.1.1071
