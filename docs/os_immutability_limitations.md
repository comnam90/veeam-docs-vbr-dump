---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/os_immutability_limitations.html"
last_updated: "2/23/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


This section lists considerations and known limitations for object storage repositories.

General Considerations and Limitations

Consider the following immutability limitations:

* The minimum immutability period that you can set for an object storage repository is 1 day, and the maximum is 999 days.
* Immutable data is preserved as described in [Block Generation](object_storage_block_generation.md).

* We recommend that you do not set the immutability period longer than the retention policy of the backup job, otherwise it will result in extra charges.

* After you upgrade to Veeam Backup & Replication version 13.0.1.P1 (build 13.0.1.1071), Veeam Backup & Replication will set the default immutability mode to match the [entire retention period specified in the backup job policy](hiw_immutability_os.md#entireduration).

Amazon S3 Immutability Limitations

Consider the following immutability limitations for Amazon S3:

* After you have created an S3 bucket with Object Lock enabled, check that the default retention is disabled.

The default retention may result in an unpredictable system behavior and data loss. However, note that Veeam Backup & Replication will use Compliance object lock mode for each uploaded object. For more information on the retention modes, see [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock-overview.html). For more information on how to disable retention settings for S3 bucket, see [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock-console.html).

* After you have added the buckets to the backup infrastructure, you must NOT enable or disable Versioning and Object Lock as it may lead to unpredictable system behavior and data loss.
* If you plan to use the immutability feature with the existing S3 bucket containing backups created by 9.5 Update 4, keep in mind that both Versioning and Object Lock must be enabled on the bucket simultaneously and immediately before enabling the immutability feature. Any other approach will lead to backup offload failures and inability to correctly interact with backups in the bucket.

Azure Blob Storage Immutability Limitations

Consider the following immutability limitations for Azure Blob Storage:

* Make sure that the Azure Blob storage settings meet the following requirements: when you configure an Azure storage account and an Azure container:

* When you create a storage account, make sure you enable versioning for blobs.
* When you create a storage account, do NOT enable version-level immutability. By default, this option is enabled and you must disable it. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-policy-configure-version-scope?tabs=azure-portal#enable-version-level-immutability-support-on-a-storage-account).
* When you create a container, you must enable version-level immutability. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-policy-configure-version-scope?tabs=azure-portal#enable-version-level-immutability-for-a-new-container).
* The default retention is disabled. For more information on how to disable retention settings for Azure container, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-policy-configure-container-scope?tabs=azure-portal).

|  |
| --- |
| Tip |
| For instruction on how to configure your Azure storage account with the necessary settings, see [this Veeam KB article](https://www.veeam.com/kb4416). |

* The default immutability policies are not supported.
* Do NOT enable immutability for already existing containers in the Azure portal. Otherwise, Veeam Backup & Replication will not be able to process these containers properly and it may result in data loss.

* Version-level immutability support for Azure storage accounts is not supported.

Veeam Data Cloud Vault Limitations

Consider the following immutability limitations for Veeam Data Cloud Vault:

* Immutability is enabled by default for Veeam Data Cloud Vault and you cannot disable it.

* [For backup jobs managed by Veeam Agent] You cannot back up data to Veeam Data Cloud Vault added in the direct connection mode.

Google Cloud Storage Limitations

Consider the following immutability limitations for Google Cloud Storage:

* Verify that the bucket retention policy is disabled.

* After you have added the buckets to the backup infrastructure, you must NOT enable or disable Object versioning and object retention as it may lead to unpredictable system behavior and data loss.

Block Generation for GFS Backups

Consider the following immutability limitations for GFS backups:

* Monthly and yearly GFS backups do not have Block Generation unless you change the default values for Block Generation to exceed these backups.
* If you keep backups with multiple GFS flags assigned (weekly, monthly, and yearly) in the same object storage, Veeam Backup & Replication will not assign any Block Generation period for these backups.


