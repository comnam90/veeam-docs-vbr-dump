---
title: "Data Retrieval"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/archive_tier_retrieval.html"
last_updated: "10/13/2025"
product_version: "13.0.1.1071"
---

# Data Retrieval


Data retrieval is the process of receiving temporary access to archived data, so that it can be restored.

The process of retrieving data from the archive tier takes course in a separate retrieval job session. It is completed when a restore point is available for reading and restore. For information on how to launch the retrieval job, see [Retrieving Backup Files](retrieval_job_launch.md).

When the retrieval job is complete, the retrieved data will be available for a limited period of time, during which you can restore it. However, you can [extend the availability period](extending_expiration_time.md).

|  |
| --- |
| Note |
| If you launch restore job when retrieval job is not over yet, the restore job will be pending until the retrieval job is complete. |

Retrieval cost varies depending on the desired speed of the process and on the targeted period of the data accessibility. The set of options is different for different vendors.

Retrieval Options for Amazon S3 Glacier and S3 Compatible Object Storage with Data Archiving

Amazon and S3 compatible object storage with Data Archiving provide the following options for data retrieval. The indicated time is approximate. For more information on Amazon, see [AWS Documentation](https://docs.aws.amazon.com/amazonglacier/latest/dev/downloading-an-archive-two-steps.html#api-downloading-an-archive-two-steps-retrieval-options ).

|  |
| --- |
| Note |
| Before you start data retrieval from S3 compatible object storage with Data Archiving, verify that the necessary method is supported by your S3 compatible vendor. To get this information, contact your vendor. |

* Expedited: the most expensive method. Retrieval takes 1-5 minutes.

|  |
| --- |
| Note |
| This option is not available if you assign the [Amazon S3 Glacier Deep Archive](glacier_storage_details.md#storageclass) storage class to data blocks. |

* Standard accelerated: retrieval time is faster than the standard option and allows you to retrieve a group of object. Note that it will result in additional costs.

|  |
| --- |
| Note |
| To perform the standard accelerate restore, you must set the necessary permissions. For more information, see [S3 Batch Retrieval Permissions for Amazon S3 Glacier](required_permissions.md#batch). |

* Standard: retrieval time 3-5 hours for Amazon S3 Glacier and within 12 hours for Amazon S3 Glacier Deep Archive.
* Bulk: the least expensive method. Retrieval time within 5-12 hours for Amazon S3 Glacier and within 48 hours for Amazon S3 Glacier Deep Archive.

Expiration of the Retrieved Data for Amazon S3 Glacier

Estimated time of data expiration is calculated from the moment of the data retrieval launch. Required number of days is added to that moment.

However, during the retrieval job Veeam Backup & Replication constantly requests the S3 API to move the expiration time forward, until the job is completed and all the data blocks are ready.

For more information on calculating the estimated expiration time, see [AWS Documentation](https://docs.aws.amazon.com/AmazonS3/latest/dev/restoring-objects.html).

For information on how to extend the expiration time, see [Extending Data Availability](extending_expiration_time.md).

Retrieval Options for Azure Archive Storage

Azure provides the following options for data retrieval. The indicated time is approximate. For more information, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-rehydration?tabs=azure-portal).

* High Priority: most expensive method. Retrieval may take less than one hour.
* Standard Priority: least expensive method. Retrieval takes up to 15 hours.

Expiration of the Retrieved Data for Azure Archive Storage

Unlike Amazon S3 Glacier, Azure API does not temporarily change the storage class of a backup file from Archive Tier to Hot. Instead, a temporary copy of a backup file is created in Hot storage class. Since the deletion of this temporary copy is managed by Veeam Backup & Replication, the expiration time is quite accurate (within ten minutes, which is the frequency of the deletion process).

For information on how to extend the expiration time, see [Extending Data Availability](extending_expiration_time.md).

Related Topics

* [Retrieving Backup Files](retrieval_job_launch.md)
* [Extending Data Availability](extending_expiration_time.md)


