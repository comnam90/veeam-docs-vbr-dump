---
title: "Scale-Out Repository with Extents in Metadata and Data Roles"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/unstructured_data_backup_sobr_extent_roles.html"
last_updated: "9/18/2025"
product_version: "13.0.1.1071"
---

# Scale-Out Repository with Extents in Metadata and Data Roles

In this article

When you use a standalone repository for storing unstructured data backups, it stores both data and metadata. But when you plan to use a scale-out repository, you can configure its performance extents to act as data extents or as metadata extents. Thus, you can store metadata separate from the backup data.

|  |
| --- |
| Note |
| We strongly recommend configuring a scale-out backup repository with the following architecture:   * Metadata extent: fast SSD-based extent for storing metadata. * Data extent: deduplicating storage appliance for storing backup data ([Dell Data Domain](dell_dd.md), [ExaGrid](deduplicating_appliance_exgrid.md), [HPE StoreOnce](deduplicating_appliance_storeonce.md), [Quantum DXi](deduplicating_appliance_quantum.md)).   It ensures that metadata operations benefit from SSD-level performance, while backup data benefits from the storage efficiency of deduplication. |

Most often, when performing restore, merge, transform operations, Veeam Backup & Replication interacts with metadata rather than with the backup data. Obviously, processing metadata stored on the SSD is faster and more efficient than accessing large data arrays stored on a slow storage.

|  |
| --- |
| Important |
| Consider the following when assigning roles to extents in a scale-out backup repository:   * An extent with the metadata role can be used for storing metadata for unstructured data backup jobs only. However, extents with the data role can be used by any job. * Make sure that you assign both roles to extents in a scale-out repository. If an extent with one of the roles is missing, Veeam Backup & Replication cannot store backups on this scale-out repository. |

|  |
| --- |
| Note |
| If the data role is assigned to an extent, Veeam Backup & Replication will also copy replica of metadata to this extent to provide the metadata redundancy. While the original metadata is available, Veeam Backup & Replication does not use the replica of metadata on data extents. If by some reason metadata stored on metadata extents is corrupted or lost, to restore it Veeam Backup & Replication will use the replica of metadata stored on data extents. |

To assign the metadata or data role to extents in a scale-out backup repository, use the Set-VBRRepositoryExtent cmdlet, as described in the [Veeam PowerShell Reference](https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrrepositoryextent.html?ver=13). If previously the role was not assigned to the extents for unstructured data backup or you changed the assigned role, during the next run of the file backup job or object storage backup job that writes backups to this scale-out repository, Veeam Backup & Replication will move metadata to the metadata extent, data — to the data extents.

For example, if you already have an existing backup and want to move its metadata to a specific extent that will operate as a metadata only extent, do the following:

1. Make sure that your license allows using a scale-out backup repository with object storage support. For more information, see [Viewing License Information](license_view.md) and [Veeam Backup & Replication Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf).
2. Create a scale-out backup repository with the following extents: one extent that currently stores the backup (its data and metadata), another extent that will store metadata of the backup. Usually, it is a fast storage, for example, SSD-based. Let us assume that these extents are named “Backup Repository 1” and "File Backup Repository on SSD".
3. Run the Set-VBRRepositoryExtent cmdlet to assign the data role to the “Backup Repository 1” extent and the metadata role to the "File Backup Repository on SSD" extent.

|  |
| --- |
| Set-VBRRepositoryExtent –Extent “File Backup Repository on SSD” -Metadata  Set-VBRRepositoryExtent –Extent “Backup Repository 1” –Data |

For more information, see the [Veeam PowerShell Reference](https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrrepositoryextent.html?ver=13).

1. Run the file backup job and make sure that the metadata of the backup was moved to the metadata extent: the backup job session displays a line notifying of that.

To view the roles of the extents in a scale-out backup repository, do either of the following:

* Check the role of each extent (the Role column) in the list of extents under the certain scale-out repository in the Backup Infrastructure view.
* Run the Get-VBRRepositoryExtent cmdlet, as described in the [Veeam PowerShell Reference](https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrrepositoryextent.html?ver=13).

Page updated 9/18/2025

Page content applies to build 13.0.1.1071
