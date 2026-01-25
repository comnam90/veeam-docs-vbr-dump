---
title: "Backup Immutability"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/plugins_sap_orcl_object_storage_immutable.html"
last_updated: "1/23/2026"
product_version: "13.0.1.1071"
---

# Backup Immutability


If you store your backup files in an object storage repository, Veeam Backup & Replication allows you to protect backup data from deletion or modification by making that data temporarily immutable. It is done for increased security: immutability protects data in your recent backups from loss as a result of attacks, malware activity or any other injurious actions.

|  |
| --- |
| Important |
| Backup immutability uses native capabilities of object storage. Enabling this feature may result in additional API and storage charges from the storage provider. |

Supported Object Storage Types

Veeam Backup & Replication supports database backup immutability for all supported object storage types:

* Amazon S3
* S3 compatible
* Google Cloud Storage
* Microsoft Azure Blob Storage
* IBM Cloud Object Storage
* Wasabi Cloud Storage
* Veeam Data Cloud Vault
* 11:11 Cloud Object Storage

Before You Begin

Before you configure immutability for database backups, you must prepare the target storage account. Depending on the selected object storage type, perform the following actions:

* [S3 Compatible and Amazon S3 storage] When you create an S3 bucket, you must enable the S3 Versioning and S3 Object Lock features for the bucket. For more information, see [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/managing-storage.html).

* [S3 Compatible and Amazon S3 storage] After you create an S3 bucket with Object Lock enabled, make sure that the default retention is disabled to avoid unpredictable system behavior and data loss. To disable the default retention, edit the Object Lock retention settings as described in [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock-console.html).

* [Microsoft Azure Blob storage] You must enable blob versioning and version-level immutability support for the Azure container. For more information, see [Microsoft documentation](https://learn.microsoft.com/en-us/azure/storage/blobs/data-protection-overview).
* [Google Cloud Storage] When you create a bucket, you must enable the Object Versioning and Object Retention Lock features for the bucket. For more information on Object Versioning, see [Google Cloud documentation](https://cloud.google.com/storage/docs/object-versioning). For more information on Object Retention Lock, see [Google Cloud documentation](https://cloud.google.com/storage/docs/object-lock).

Consider the following about backup immutability:

* [S3 Compatible and Amazon S3 storage] Veeam Plug-In will use the compliance retention mode for each uploaded object. For more information on retention modes of S3 Object Lock, see [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html).
* [Microsoft Azure Blob storage] Do not enable immutability for already existing containers in the Microsoft Azure Portal. Otherwise, Veeam Backup & Replication will not be able to process these containers properly and it may result in data loss.
* After you specify a minimum immutability period for a backup and run the backup job for the first time, Veeam Backup & Replication will append the block generation period to the specified immutability period. To learn more, see [Block Generation Period](#gen).

* Increasing the minimum immutability duration in the object storage repository settings updates immutability locks for all objects in this repository to match the block generation period of the current generation. As a result, this change may cause additional costs as it results in requests generated for each object in the object storage repository.

Backup Immutability and Retention Policy

Veeam Backup & Replication removes obsolete restore points based on the defined backup retention policy, but only if such restore points are no longer immutable. If data associated with an obsolete restore point is still immutable, such restore point will remain in the backup chain and in the repository until its immutability period is over. After that, such restore point is automatically removed from the backup chain and storage.

Block Generation Period

When you specify an immutability period in the object storage repository settings, Veeam Backup & Replication will automatically calculate an effective immutability period as a sum of the following periods:

* minimum immutability period

You can specify the minimum immutability period in the object storage repository settings. To learn more, see [Adding Object Storage Repositories](new_object_storage.md).

* block generation period

The block generation period serves to reduce the number of requests to the object storage repository, which results in lower traffic and reduced storage costs. During this block generation period, all of the transferred data objects will have the same immutability.

The block generation period is predetermined depending on the object storage that you use:

* 30 days — for repositories in Amazon S3 and Google Cloud Storage IBM Cloud and 11:11 Cloud Object Storage.
* 10 days — for repositories in S3 compatible storage, Microsoft Azure Blob Storage and Veeam Data Cloud Vault.

|  |
| --- |
| Note |
| * You may configure a backup repository in IBM Cloud and 11:11 Cloud Object Storage using the S3 Compatible wizard. In this case, Veeam Backup & Replication will append the block generation period of 10 days. * You can change the predetermined block generation period with the registry key. For more information, submit a support case on the [Veeam Customer Support Portal](https://www.veeam.com/support.html). |

Example

You create a backup on IBM Cloud Object Storage on July 1st with immutability set for 7 days.

The effective immutability period for the first block generation will be July 1st + 7 days (minimum immutability period) + 10 days (block generation period for IBM Cloud Object Storage). As a result, database backups created during the first block generation period from July 1st to July 10th will be immutable till July 18th.

The second block generation will start 10 days later on July 11th. The effective immutability period for the second block generation will be July 11th + 7 days (minimum immutability period)  + 10 days (block generation period for IBM Cloud Object Storage). As a result, database backups created during the second block generation period from July 11th to July 21st will be immutable till July 28th.


