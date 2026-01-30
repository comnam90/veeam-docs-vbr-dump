---
title: "Migrating Backups within Scale-Out Backup Repository"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backups_migration.html"
last_updated: "3/28/2025"
product_version: "13.0.1.1071"
---

# Migrating Backups within Scale-Out Backup Repository


The migration option allows you to migrate data between performance or capacity extents of different object storage repositories. This option may be helpful if you want to switch from one object storage repository to another or to migrate from the object storage repository with different immutability settings.

|  |
| --- |
| Important |
| If you need to migrate your data from a mutable bucket or container to an immutable bucket or container, perform the steps described in the [Migrating Data Between Different Buckets or Containers](#different) scenario. Do NOT use 3rd party tools for this type of migration. |

Migrating Data Between Different Object Storage Repositories

You can follow this scenario in case you need to migrate data from one type of object storage to another. For example, to migrate data from the Amazon S3 object storage repository to the Azure Blob storage or any other object storage. These object storage repositories can have different or identical immutability settings. If Veeam Backup & Replication migrates data from the mutable object storage repository, it removes data from this repository. If Veeam Backup & Replication migrates data from the immutable object storage repository, this data remains intact after migration and will be removed according to the immutability period settings. Depending on the immutability settings, consider the necessary migration scenario.

|  |
| --- |
| Important |
| Before migrating data, configure the [connection through the gateway server](object_storage_repository.md#connectionMode) for both the source and target object storage repositories to ensure data flows entirely within the cloud environment. |

Identical Immutability Settings

To migrate data, do the following:

1. Put an extent from which you want to migrate data to the [Sealed](sobr_seal.md) mode.
2. Add a new object storage repository to the same (performance or capacity) tier of your existing scale-out backup repository.
3. Switch an extent from which you want to migrate data into the [Maintenance](sobr_maintenance.md) mode.
4. [Evacuate](sobr_evacuate.md) data from the source extent.
5. Remove the old object storage repository from the backup infrastructure.

Different Immutability Settings

To migrate data, do the following:

1. Switch the extent from which you want to migrate data to the [Sealed](sobr_seal.md) and [Maintenance](sobr_maintenance.md) mode.
2. Add a new object storage repository to the same (performance or capacity) tier of your existing scale-out backup repository.
3. [Evacuate](sobr_evacuate.md) data from the source extent.
4. [If the source repository is immutable] Disable the Maintenance mode for the source object storage repository.

|  |
| --- |
| Note |
| Do not turn off the Sealed mode for the source object storage repository. The backups will be removed from it according to its immutability period settings. |

Migrating Data Between Different Buckets or Containers

You can follow this scenario if you need to migrate data between different buckets or containers of the same object storage repository. These buckets or containers can have different or identical immutability settings. If Veeam Backup & Replication migrates data from the mutable bucket or container, it removes data from the source bucket or container. If Veeam Backup & Replication migrates data from the immutable bucket or container, this data remains intact after migration and will be removed according to the immutability period settings.

Depending on the immutability settings, consider the necessary migration scenario.

Identical Immutability Settings

To migrate data, do the following:

1. Switch the extent from which you want to migrate data to the [Maintenance Mode](sobr_maintenance.md).
2. Add a new object storage repository to the backup infrastructure and specify a new bucket or container. For more information, see the [Adding Object Storage Repositories](new_object_storage.md) section.
3. Set this new object storage repository as a performance or capacity extent of your existing scale-out backup repository. For more information, see the [Extending Scale-Out Repositories](sobr_add_extent.md) section.
4. [Evacuate](sobr_evacuate.md) data from the source extent.
5. Synchronize your data. For more information, see the [Synchronizing Capacity Tier Data](new_capacity_tier.md#sync_tier_data) section.

Different Immutability Settings

To migrate data, do the following:

1. Switch the extent from which you want to migrate data to the [Sealed](sobr_seal.md) and [Maintenance](sobr_maintenance.md) mode.
2. Add a new object storage repository to the backup infrastructure and specify a new bucket or container. For more information, see the [Adding Object Storage Repositories](new_object_storage.md) section.
3. Set this new object storage repository as a performance or capacity extent of your existing scale-out backup repository. For more information, see the [Extending Scale-Out Repositories](sobr_add_extent.md) section.
4. [Evacuate](sobr_evacuate.md) data from the source extent.
5. [If the source repository is immutable] Disable the Maintenance mode for the source object storage repository.

|  |
| --- |
| Note |
| Do not turn off the Sealed mode for the source object storage repository. The backups will be removed from it according to its immutability period settings. |

1. Synchronize your data. For more information, see the [Synchronizing Capacity Tier Data](new_capacity_tier.md#sync_tier_data) section.

Copying Data Between Different Buckets or Containers with 3rd Party Tool

You can follow this scenario in case you want to use a 3rd party tool to migrate data located in an object storage repository between different buckets or containers of the same same object storage repository, do the following:

1. Use any available 3rd party tool to copy ALL data from an old bucket or container to a new bucket or container.
2. Add a new object storage repository to the backup infrastructure. For more information, see the [Adding Object Storage Repositories](new_object_storage.md) section.
3. Set a new object storage repository as a capacity extent of the scale-out backup repository which you use.

1. Synchronize your data. For more information, see the [Synchronizing Capacity Tier Data](new_capacity_tier.md#sync_tier_data) section.

Migrating Data Within One Capacity Tier

You can migrate your data between different extents of the same tier.

To do this, perform the following steps:

1. Switch the necessary extent into the [Maintenance](sobr_maintenance.md) mode.
2. Evacuate backups from the extent.


