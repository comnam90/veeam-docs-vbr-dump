---
title: "Enabling Immutability"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/immutability_os_enable.html"
last_updated: "11/21/2025"
product_version: "13.0.1.1071"
---

# Enabling Immutability


To enable immutability, you must configure the necessary settings for your object storage repository.

Configuring Immutability Settings S3 Buckets

To be able to use immutability with S3 object storage repositories, you must configure a new S3 bucket with the following settings:

1. Enable the Object Lock feature on your S3 bucket. For more information, see these Amazon articles [Creating a bucket](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/create-bucket.html), [Using S3 Object Lock](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html).

|  |
| --- |
| Important |
| Note that most vendors allow enabling Object Lock only at the moment of creating the bucket. |

1. Verify that the default retention is disabled.
2. Enable the Versioning on your S3 bucket. For more information, see [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/enable-versioning.html).
3. Enable the immutability option when you add an object storage repository to the backup infrastructure at the Bucket step of the new [Object Storage Repository](new_object_storage.md) wizard.

Configuring Immutability Setting for Azure Containers

To be able to use immutability with Azure object storage repositories, you must configure a new Azure storage account and Azure container with the following settings:

1. Setting for a new Azure container:

* Enable support for version-level WORM on the container. For more information on enabling version-level WORM for a container, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-policy-configure-version-scope?tabs=azure-portal#enable-version-level-immutability-for-a-new-container).

* Enable version-level immutability. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-policy-configure-version-scope?tabs=azure-portal#enable-version-level-immutability-for-a-new-container).
* Verify that the default retention is disabled. For more information on how to disable retention settings for Azure container, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-policy-configure-container-scope?tabs=azure-portal).

1. Azure storage account settings:

* Enable blob versioning for your storage account. For more information on blob versioning for a storage account, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal#data-protection-tab).
* Do NOT enable version-level immutability. By default, this option is enabled and you must disable it. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-policy-configure-version-scope?tabs=azure-portal#enable-version-level-immutability-support-on-a-storage-account).

|  |
| --- |
| Tip |
| For instruction on how to configure your Azure storage account with the necessary settings, see [this Veeam KB article](https://www.veeam.com/kb4416). |

1. Enable the immutability option when you add an object storage repository to the backup infrastructure at the Container step of the new [Object Storage Repository](new_object_storage.md) wizard.

Configuring Immutability Setting for Google Cloud Storage Buckets

To be able to use immutability with Google Cloud object storage repositories, you must create a new Cloud Storage buckets with the following settings:

1. Enable object versioning.

|  |
| --- |
| Note |
| Veeam Backup & Replication does not create any versions of objects. If you specify several versions of an object, this setting will not take effect. |

1. Enable object retention.

1. Enable the immutability option when you add an object storage repository to the backup infrastructure at the Bucket step of the new [Object Storage Repository](new_object_storage.md) wizard.


