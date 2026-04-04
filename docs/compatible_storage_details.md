---
title: "Step 4. Specify Object Storage Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/compatible_storage_details.html"
last_updated: "4/1/2026"
product_version: "13.0.1.2067"
---

# Step 4. Specify Object Storage Settings


At the Bucket step of the wizard, do the following:

1. [Specify general settings for a bucket](#general).
2. [Specify immutability settings](#immutability).

Specifying General Settings for Bucket

1. In the Bucket field, enter a name of the bucket or click Browse to get the necessary bucket.

Note that you must create the bucket where you want to store your backup data beforehand.

1. To create [multiple child buckets](object_storage_repository.md#childbuckets) automatically, do the following:

1. Click the Automatic bucket creation disabled link.
2. To specify a number of per-machine backups chains that you want to keep in a single child bucket, check the Create new buckets automatically check box. Veeam Backup & Replication will create child buckets according to this amount of backup chains.

1. To the right of the Folder field, click Browse and either select an existing folder or click New Folder.

1. Select the Limit object storage consumption to check box to define a soft limit for your object storage consumption. If this limit is exceeded during a job run, Veeam Backup & Replication will complete the job. However, a new job will not be able to start unless you remove the extra data that exceeds the limit or change the soft limit settings. Provide the value in TB or PB.

![Step 4. Specify Object Storage Settings](images/s3_compatible_add_bucket.webp)

Specifying Immutability Settings

Immutability prohibits deletion of blocks of data from your object storage repository.

To enable immutability:

1. Select the Make backups immutable (recommended) check box.
2. In the Immutability Settings window, specify how the immutability period is counted and set the immutability period in days:

* Select the For the entire duration of their retention policy option if you want the immutability period depend on the retention policy of a backup job.

|  |
| --- |
| Important |
| Consider the following:   * If the job retention exceeds the immutability period, the actual retention is counted as job retention policy + Block Generation period. * If the immutability period exceeds the job retention period, the actual retention is counted as immutability period + Block Generation period. * The default immutability period is 30 days. You can set the immutability period to different values in the Veeam Backup & Replication UI. The minimum immutability period is 1 day, and the maximum is 999 days.   For more information, see [How Immutability Works](hiw_immutability_os.md). |

* Select the For the minimum immutability period only option if you want to specify the immutability period explicitly. The backup job retention will be skipped.
* Next to the Minimum immutability duration option, provide the necessary value.

![Step 4. Specify Object Storage Settings](images/s3_compatible_immutability.webp)


