---
title: "Step 4. Specify Object Storage Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veeam_data_cloud_vault_details_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Specify Object Storage Settings


At the Folder step of the wizard, do the following:

1. [Specify general folder settings](#general).
2. [Specify immutability settings](#immutability).

Specifying General Folder Settings

To specify the folder that will be used to store data and the storage consumption, do the following:

1. To the right of the Folder field, click Browse
2. In the Select a folder window, either select an existing folder or click New Folder.
3. Select the Limit object storage consumption to check box to define a soft limit for your object storage consumption. If this limit is exceeded during a job run, Veeam Backup & Replication will complete the job. However, a new job will not be able to start unless you remove the extra data that exceeds the limit or change the soft limit settings. Provide the value in TB or PB.

![Step 4. Specify Object Storage Settings](images/veeam_vault_archive_settings.webp)

Specifying Immutability Settings

1. To prohibit deletion of blocks of data from object storage, select the Make recent backups immutable (recommended) check box. In the Immutability Settings window, specify how the immutability period is counted and set the immutability period in days:

* Select For the entire duration of their retention policy if you want the immutability period depend on the retention policy of a backup job.

|  |
| --- |
| Important |
| Consider the following:   * If the GFS retention period is shorter than the minimum immutability period configured for the repository, the minimum immutability period applies. * If the GFS retention period is longer, the backup is kept for the entire GFS period.   For more information, see [Immutability for Archive Tier](immutability_archive_tier.md). |

* Select the For the minimum immutability period only option if you want to specify the immutability period explicitly. The backup job retention will be skipped.

* Next to the Minimum immutability duration option, provide the necessary value.

|  |
| --- |
| Note |
| Consider the following:   * By default, immutability is enabled for Veeam Data Cloud Vault. You cannot disable this option and cannot remove data during this period.  * The default immutability period is 180 days. You can set the immutability period to different values. The maximum immutability period is 999 days. |

![Step 4. Specify Object Storage Settings](images/veeam_vault_archive_settings_immutability.webp)

Page updated 2026-07-29

