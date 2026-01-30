---
title: "Capacity Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/capacity_tier.html"
last_updated: "11/21/2025"
product_version: "13.0.1.1071"
---

# Capacity Tier


Capacity tier is an additional tier of storage that can be attached to a scale-out backup repository. Data from the scale-out backup repository performance extents can be transported to the capacity tier for long-term storage. You can use the capacity tier with almost all types of jobs and tasks that Veeam Backup & Replication runs. For a list of unsupported scenarios, see [Limitations for Capacity Tier](capacity_tier_limitations.md).

This feature is most useful in the following cases:

* You are running out of storage space.
* Your organization policies allow you to store only a certain amount of data on your extents, while the outdated data should be stored elsewhere.
* You seek to store data on several sites to ensure its safety in case of a disaster.

With capacity tier, you can perform the following operations:

* Move inactive backup chains to capacity extents, as described in section [Moving Backups to Capacity Tier](capacity_tier_move.md) and [Manually Moving Backups to Capacity Tier](moving_to_capacity_tier.md).
* Copy new backup files as soon as these files are created, as described in section [Copying Backups to Capacity Tier](capacity_tier_copy.md).
* Download data that was moved from capacity extents back to the performance extents, as described in section [How Downloading from Capacity Tier Works](capacity_tier_download.md).
* Restore your data. For more information, see [Restore from Capacity Tier](restore_capacity_tier.md). In particular, you can promptly restore data from the capacity tier in case of disaster without creating a scale-out backup repository anew. For more information about this feature, see [Importing Object Storage Backups](osr_import_backups.md).

Supported Types of Object Storage Repositories

The capacity tier consists of multiple capacity extents. The capacity extent can be either a cloud-based object storage repository or on-premises object storage repository, such as:

* [Veeam Data Cloud Vault](osr_adding_veeam_data_cloud_vault.md)
* [S3 Compatible Object Storage](s3_compatible_adding.md)
* [Amazon S3 Storage](osr_amazon_adding.md)
* [AWS Snowball Edge Storage](osr_amazon_se_adding.md)
* [Azure Blob Storage](osr_adding_blob_storage.md)
* [Azure Data Box Storage](osr_adding_data_box.md)
* [IBM Cloud Object Storage](adding_ibm_object_storage.md)
* [Google Cloud Object Storage](adding_google_cloud_object_storage.md)
* [Wasabi Cloud Object Storage](adding_wasabi_object_storage.md)
* [11:11 Cloud Object Storage](adding_1111.md)

Before an object storage repository can be configured as the capacity extent, it must be added to Veeam Backup & Replication. For more information, see [Adding Object Storage Repositories](new_object_storage.md).

The capacity extents are displayed in the scale-out backup repository wizard, on the [Capacity Tier](new_capacity_tier.md) step.

For information on configuring capacity tier and synchronizing capacity tier data, see [Add Capacity Tier](new_capacity_tier.md).

In This Section

* [Limitations for Capacity Tier](capacity_tier_limitations.md)
* [Capacity Extent Structure](object_storage_repository_structure.md)
* [Backup File Placement for Capacity Tier](data_placement_capacity.md)
* [Immutability for Capacity Tier](immutability_capacity_tier.md)
* [Encryption for Capacity Tier](encryption_for_capacity_tier.md)
* [Health Check for Capacity Tier](hc_capacity_tier.md)
* [Managing Capacity Tier](managing_capacity_tier_data.md)
* [Restore from Capacity Tier](restore_capacity_tier.md)


