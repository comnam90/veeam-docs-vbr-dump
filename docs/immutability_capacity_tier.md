---
title: "Immutability for Capacity Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/immutability_capacity_tier.html"
last_updated: "12/23/2025"
product_version: "13.0.1.1071"
---

# Immutability for Capacity Tier


Veeam Backup & Replication allows you to prohibit deletion of data from capacity extents by making that data temporarily immutable. It is done for increased security: immutability protects your data from loss as a result of attacks, malware activity or any other injurious actions.

You can enable immutability for data stored in Amazon, S3-compatible, Google Cloud and Azure object storage repositories used as capacity extents of the scale-out backup repository. After you enable immutability, Veeam Backup & Replication will prohibit data deletion from capacity tier until the immutability expiration date comes.

|  |
| --- |
| Note |
| The immutability period for backups with GFS flags depends on multiple settings of a scale-out backup repository. For more information, see the [GFS Backups Immutability Period](gfs_immutability_sobr.md) section. |

Backups are immutable only during the immutability period set in the object storage repository settings even if their retention policy allows for longer storage. Immutability retention policy ignores retention policies set for the following types of backups:

* Backups with GFS flags

* Backups created by VeeamZIP jobs

* Exported backup files

The immutable data within the capacity extents cannot be subject to the following operations:

* Manual removal of data, as described in section [Removing Backups from Capacity or Archive Tier](object_storage_removing_data.md).
* Removal of data by the retention policy, as described in section [Retention Policy](capacity_tier_retention.md).
* Removal of data using any cloud service provider tools.
* Removal of data by the cloud service provider technical support department.

* Removal of data by the Remove deleted items data after option. For more information, see the Maintenance Settings section for [VMware vSphere backup jobs](backup_job_advanced_maintenance_vm.md) and [Microsoft Hyper-V backup jobs](backup_job_advanced_maintenance_hv.md).

Enabling Immutability

To enable immutability, you must do the following:

1. Configure the necessary settings when you create an S3 bucket or an Azure container.

For more information, see [Enabling Immutability](immutability_os_enable.md).

1. Enable the immutability option when you add an object storage repository to the backup infrastructure at the Container step (for Azure object storage repository) or Bucket step (for Amazon S3 or S3 compatible object storage repositories) of the new Object Storage Repository wizard.

Related Topics

[Block Generation](block_gen.md)


