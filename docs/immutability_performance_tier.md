---
title: "Immutability for Performance Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/immutability_performance_tier.html"
last_updated: "9/1/2025"
product_version: "13.0.1.1071"
---

# Immutability for Performance Tier


Veeam Backup & Replication allows you to prohibit deletion of data from the repositories added as a performance extent by making that data temporarily immutable. It is done for increased security: immutability protects your data from loss as a result of attacks, malware activity or any other injurious actions.

You can enable immutability for the following types of repositories:

* Amazon, S3-compatible, Azure, and Google Cloud object storage repositories. For more information, see [Immutability for Object Storage Repositories](immutability_object_storage_repositories.md).
* Hardened Repository. For more information, see [Hardened Repository](hardened_repository.md#sobr).

* HPE StoreOnce. For more information, see [Immutability for HPE StoreOnce](storeonce_supported_features.md#immutability).
* Dell Data Domain. For more information, see [Immutability for Dell Data Domain](dell_dd.md#immutability).

After you configure a performance extent with an immutable repository, you will not be able to perform the following operations with the immutable data:

* [Remove data manually](deleting_backups_from_sobr.md)
* Remove data using any cloud service provider tools.
* Remove data by the cloud service provider technical support department.
* Remove data by the Remove deleted items data after option. For more information, see the Maintenance Settings section for [VMware vSphere backup jobs](backup_job_advanced_maintenance_vm.md) and [Microsoft Hyper-V backup jobs](backup_job_advanced_maintenance_hv.md).

Immutability Period for Direct Backup Object Storage Repositories Added as Performance Extents

The immutability period for the performance tier almost always depends on the configuration of your object storage repository: you either specify the immutability period to depend on the retention of the backup job, or set the minimum immutability period. For more information, see [How Immutability Works](hiw_immutability_os.md#retention).

However, for a specific configuration of the scale-out backups repository, Veeam Backup & Replication applies a different algorithm to identify the actual retention of the backups in the performance tier.

Scenario 1. Immutable Performance Tier and Capacity Tier with Move Policy

The actual immutability period depends on the backup job retention, [move policy](capacity_tier_move.md), periodic full settings, and settings of GFS backup files. The immutability period is reduced to the value of the move policy. This is done to guarantee that an outdated backup chain will become inactive and will be moved to the capacity tier according to the schedule. Veeam Backup & Replication defines the nearest date when the data can be moved to the capacity tier. Since data is moved only when the backup chain becomes inactive (that is, it will have a new full backup file). Veeam Backup & Replication checks the periodic full backup schedule that will produce a new full backup. After that, the previous backup chain will become unavailable, and data will be moved to the capacity tier.

For example:

* Backup job retention = 28 days
* Move policy  = 7 days
* Periodic full backup = 1 time in 7 days

In this case, Veeam Backup & Replication will add 7 days to the move policy and 3 days to make backups immutable during the offload job. Thus, the immutability period will be set to 17 days.

Scenario 2. Immutable Performance Tier and Archive Tier

In this scenario, the immutability period depends on the type of a backup file:

* For GFS backup files, the immutability period does not exceed the period of the operational restore window that you specify when configure [archive tier](new_archive_tier.md#operational_window).

Note that to run an archiving job, Veeam Backup & Replication adds 3 days to the immutability period.

* For all other backup files, the immutability period depends on the backup job retention and periodic full settings.

Related Topics

[Block Generation](performance_tier_block_generation.md)


