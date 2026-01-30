---
title: "Step 4. Specify Object Storage Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/1111_storage_details.html"
last_updated: "8/8/2025"
product_version: "13.0.1.1071"
---

# Step 4. Specify Object Storage Settings


At the Bucket step of the wizard, specify the bucket and folder that will be used to store data:

1. In the Bucket field, enter a name of the bucket or click Browse to get the necessary bucket.

Note that you must create the bucket where you want to store your backup data beforehand.

1. In the Folder field, enter a cloud folder name to which you want to map your object storage repository. Alternatively, click Browse and either select an existing folder or click New Folder.

1. Select the Limit object storage consumption to check box to define a soft limit for your object storage consumption. If this limit is exceeded during a job run, Veeam Backup & Replication will complete the job. However, a new job will not be able to start unless you remove the extra data that exceeds the limit or change the soft limit settings. Provide the value in TB or PB.
2. If you plan to access your backup data in an infrequent manner, select the Use infrequent access storage class check box to mark each block as S3 Standard-IA (S3 Standard Infrequent Access). If you so not check this box, the blocks will be marked as S3 Standard.

![Step 4. Specify Object Storage Settings](images/1111_add_bucket.webp)

Specifying Immutability Settings

To prohibit deletion of blocks of data from object storage, select the Make recent backups immutable (recommended) check box. In the Immutability Settings window, specify how the immutability period is counted and set the immutability period in days:

* Select For the entire duration of their retention policy if you want the immutability period depend on the retention policy of a backup job.

|  |
| --- |
| Important |
| Consider the following:   * If the job retention exceeds the immutability period, the actual retention is counted as job retention policy + Block Generation period. * If the immutability period exceeds the job retention period, the actual retention is counted as immutability period + Block Generation period.   For more information, see [How Immutability Works](hiw_immutability_os.md), |

* Select For the minimum immutability period only if you want to specify the immutability period explicitly. The backup job retention will be skipped.
* Next to the Minimum immutability duration option, provide the necessary value.

![Step 4. Specify Object Storage Settings](images/1111_add_bucket_immutability.webp)

Specifying Storage Classes

To specify the storage class that you want to enable for your bucket, click the Infrequent Access link to the right of the Storage class field. In the Storage Class Settings window, select one of the following:

* Standard (recommended) — Use this option if you plan to access your data frequently. (Provides, Low latency and high throughput performance,  high durability, availability, and performance object storage
* Infrequent Access — Use this option if you plan to access your data infrequently and require fast access in case when data is needed.

![Step 4. Specify Object Storage Settings](images/1111_add_storage_class.webp)


