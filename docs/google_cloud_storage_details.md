---
title: "Step 4. Specify Object Storage Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/google_cloud_storage_details.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Step 4. Specify Object Storage Settings

In this article

At the Bucket step of the wizard, specify the bucket and folder that will be used to store data:

1. From the Data center region drop-down list, select a region.
2. In the Bucket field, enter a name of the bucket or click Browse to get the necessary bucket.

Note that you must create the bucket where you want to store your backup data beforehand.

1. In the Folder field, enter a cloud folder name to which you want to map your object storage repository. Alternatively, click Browse and either select an existing folder or click New Folder.

1. Select the Limit object storage consumption to check box to define a soft limit for your object storage consumption. If this limit is exceeded during a job run, Veeam Backup & Replication will complete the job. However, a new job will not be able to start unless you remove the extra data that exceeds the limit or change the soft limit settings. Provide the value in TB or PB.

Specifying Immutability Settings

To prohibit deletion of blocks of data from object storage, select the Make recent backups immutable (recommended) check box. In the Immutability Settings window, specify how the immutability period is counted and set the immutability period in days:

* Select For the entire duration of their retention policy if you want the immutability period depend on the retention policy of a backup job.

|  |
| --- |
| Important |
| Consider the following:   * If the job retention exceeds the immutability period, the actual retention is counted as job retention policy + Block Generation period. * If the immutability period exceeds the job retention period, the actual retention is counted as immutability period + Block Generation period.   For more information, see [How Immutability Works](hiw_immutability_os.md), |

* Select For the minimum immutability period only if you want to specify the immutability period explicitly. The backup job retention will be skipped.
* Next to the Minimum immutability duration option, provide the necessary value.

![Step 4. Specify Object Storage Settings](images/google_cloud_bucket_immutability.webp)

Specifying Storage Class Settings

To specify the storage class that you want assign to data blocks that you keep in Google Cloud object storage, click the Standard link to the right of the Storage class field. In the Storage Class Settings window, select one of the following:.

* Select the Standard option to assign the Standard storage class to data blocks. Use this option if you plan to access your data frequently and store it for a short period of time.
* Select the Nearline option to assign the Nearline storage class to data blocks. Use this option if you want to access data rarely (for example, once in a month or less) and plan to store data at least for 30 days.
* Select the Coldline option to assign the Coldline storage class to data blocks. Use this option if you plan to access data rarely (for example, once a quarter) and plan to store data minimum 90 days.

For more information on Google Cloud object storage classes, see [Google Documentation](https://cloud.google.com/storage/docs/storage-classes).

![Step 4. Specify Object Storage Settings](images/google_cloud_storage_class.webp)

Page updated 1/15/2026

Page content applies to build 13.0.1.1071
