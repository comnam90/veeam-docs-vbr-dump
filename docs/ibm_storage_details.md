---
title: "Step 4. Specify Object Storage Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ibm_storage_details.html"
last_updated: "8/12/2025"
product_version: "13.0.1.1071"
---

# Step 4. Specify Object Storage Settings

In this article

At the Bucket step of the wizard, specify the bucket and folder that will be used to store data:

1. In the Bucket field, enter a name of the bucket or click Browse to get the necessary bucket.

Note that you must create the bucket where you want to store your backup data beforehand.

1. In the Folder field, enter a cloud folder name to which you want to map your object storage repository. Alternatively, click Browse and either select an existing folder or click New Folder.

1. Select the Limit object storage consumption to check box to define a soft limit for your object storage consumption. If this limit is exceeded during a job run, Veeam Backup & Replication will complete the job. However, a new job will not be able to start unless you remove the extra data that exceeds the limit or change the soft limit settings. Provide the value in TB or PB.
2. Select the Make recent backups immutable for check box to prohibit deletion of blocks of data from object storage. Specify the immutability period. For more information, see [Immutability for Object Storage Repositories](immutability_object_storage_repositories.md).

![Step 4. Specify Object Storage Settings](images/new_ibm_storage_bucket.webp)

Specifying Immutability Settings

To prohibit deletion of blocks of data from object storage, select the Make recent backups immutable (recommended) check box. In the Immutability Settings window, specify how the immutability period is counted and set the immutability period in days:

* Select For the entire duration of their retention policy if you want the immutability period depend on the retention policy of a backup job.

|  |
| --- |
| Important |
| Consider the following:   * If the job retention exceeds the immutability period, the actual retention is counted as job retention policy + Block Generation period. * If the immutability period exceeds the job retention period, the actual retention is counted as immutability period + Block Generation period.   For more information, see [How Immutability Works](hiw_immutability_os.md), |

* Select For the minimum immutability period only if you want to specify the immutability period explicitly. The backup job retention will be skipped.
* Next to the Minimum immutability duration option, provide the necessary value.

![Step 4. Specify Object Storage Settings](images/new_ibm_storage_bucket_immutability.webp)

Page updated 8/12/2025

Page content applies to build 13.0.1.1071
