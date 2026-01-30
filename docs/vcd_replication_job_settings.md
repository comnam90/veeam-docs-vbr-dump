---
title: "Step 8. Specify Replication Job Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vcd_replication_job_settings.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Step 8. Specify Replication Job Settings


At the Job Settings step of the wizard, define VMware Cloud Director replication job settings.

1. From the Repository for replica metadata list, select a backup repository. Veeam Backup & Replication uses this backup repository to keep metadata for replicas. Metadata is required when you perform failback with the [Quick Rollback](failback_quick_rollback.md) option. For more information on metadata, see [Changed Block Tracking](changed_block_tracking.md).
2. In the Replica name suffix field, enter a suffix for the name of replicas. Veeam Backup & Replication will add this suffix to the name of the target vApps and will register replicas with this suffix.
3. In the Restore points to keep field, specify the number of restore points the replication job must maintain. If this number is exceeded, Veeam Backup & Replication removes the earliest restore point.

When you specify the retention policy settings for the replication job, consider available space on the target datastore. Due to VMware restrictions on the number of VM snapshots, the maximum number of restore points for replicas is limited to 28. An excessive amount of restore points may overfill the target datastore.

|  |
| --- |
| Important |
| Consider the following:   * You cannot store replica metadata on deduplicating storage appliances. During replication jobs, Veeam Backup & Replication frequently reads and writes small portions of metadata from/to the backup repository. Frequent access to metadata causes low performance of deduplicating storage appliances, which may result in low performance of replication jobs. * You cannot store replica metadata in a scale-out backup repository, object storage repository or NFS backup repository. * At least one successful run of a VMware Cloud Director replication job is required to apply a retention policy to a VMware Cloud Director replica and to delete previous restore points. |

![Step 8. Specify Replication Job Settings](images/vcd_replica_job_settings.webp)


