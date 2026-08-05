---
title: "Object Storage as Unstructured Data Source"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/permissions_obj_unstruct.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Object Storage as Unstructured Data Source


The following permissions are required for the account that you use to add Amazon S3 and S3 Compatible object storage as unstructured sources.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)1. Permissions for Working with Bucket Objects

|  |  |
| --- | --- |
| To be able to work with objects in buckets, the account for Amazon S3 and S3 Compatible object storage must have the following permissions:  |  | | --- | | HeadBucket  GetBucketLocation  ListBuckets  HeadObject  GetObject  GetObjectTagging  ListObjectsV1  ListObjectsV2  ListObjectVersions | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)2. Permissions for Restoring Objects and Perform Backup Objects Calls

|  |  |
| --- | --- |
| To be able to perform restore, recovery, and backup object calls, the account for Amazon S3 and S3 Compatible object storage must have the following permissions:  |  | | --- | | PutObject  PutObjectTagging  DeleteObject  DeleteObjects  CreateMultipartUpload  CreateBucket  UploadPart  CompleteMultipartUpload  AbortMultipartUpload | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)3. Permissions for Getting Backup Bucket Properties

|  |  |
| --- | --- |
| To be able to get backup bucket properties, the account for Amazon S3 and S3 Compatible object storage must have the following permissions:  |  | | --- | | GetBucketLifecycleConfiguration  GetBucketLogging  GetBucketMetricsConfiguration  ListBucketMetricsConfigurations  GetBucketNotificationConfiguration  GetBucketOwnershipControls  GetBucketPolicy  GetPublicAccessBlock  GetBucketReplication  GetBucketRequestPayment  GetBucketTagging  GetBucketVersioning  GetBucketWebsite  GetObjectLockConfiguration | |

Page updated 2026-07-21

