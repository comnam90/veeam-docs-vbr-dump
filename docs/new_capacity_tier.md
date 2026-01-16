---
title: "Step 5. Add Capacity Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/new_capacity_tier.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Step 5. Add Capacity Tier

In this article

Before you add a capacity tier, [check the prerequisites](capacity_tier_limitations.md).

At the Capacity Tier step of the wizard, select object storage repositories that you want to add as capacity extents. Then specify when to move and copy data.

|  |
| --- |
| Tip |
| If you already have a scale-out backup repository in your backup infrastructure and you want to add a capacity tier, select the scale-out backup repository, click Edit Scale-out Repository on the ribbon or right-click the scale-out backup repository and select Properties. In the Edit Scale-out Backup Repository wizard go to the Capacity Tier step and proceed with the following steps. |

To configure capacity tier, do the following:

1. Select the Extend scale-out backup repository capacity with object storage check box.
2. To select the object storage repositories to which you want to offload your data, click Choose.
3. In the Capacity Tier Extents window select the check box in front of the necessary object storage repositories. Make sure that these repositories are added to the backup infrastructure in advance. In case object storage repositories are not added, click Add and follow the steps of the [Adding Object Storage Repository](new_object_storage.md) wizard.
4. Click Offload window and specify when it is allowed or prohibited to move or copy data to object storage.
5. Select the Copy backups to object storage as soon as they are created check box to copy new backups as soon as they are created, as described in section [Copying Backups to Capacity Tier](capacity_tier_copy.md).

When selecting this option, you will be asked whether to copy all backup files that you may already have on any of the performance extents, or only those that have been created recently.

If you select Latest, only backup files that belong to the last active backup chain will be copied from each of the performance extents. If you select All, Veeam Backup & Replication will copy all backup files that belong to all backup chains located on any of the [specified](sobr_add_extents.md) extents.

1. Select the Move backups to object storage as they age out of the operational restore window check box to move inactive backup chains to the capacity extent, as described in section [Moving Backups to Capacity Tier](capacity_tier_move.md).

In the Move backup files older than X days field, specify the operational restore window to define a period after which inactive backup chains on your performance extents will be considered outdated and, therefore, should be moved to the capacity extent. Consider that "0" is an acceptable value, which you can specify to offload inactive backup chains on the same day they are created.

To override behavior of moving old backups, click Override, select the Move oldest backup files sooner if scale-out backup repository is reaching capacity check box and define a threshold in percent to force data transfer if a scale-out backup repository has reached the specified threshold.

1. To offload data encrypted, select Encrypt data uploaded to object storage and provide a strong password. With this option selected, the entire collection of blocks along with the metadata will be encrypted while being offloaded.If you have not created the password beforehand, click Add or use the Manage passwords link to specify a new password.

|  |
| --- |
| Note |
| You must enable capacity tier encryption if you want to use Veeam Data Cloud Vault as a capacity extent. |

1. If you want to specify a schedule for a health check, click the Monthly link and define the schedule settings. For more information, see [Health Check for Capacity Tier](hc_capacity_tier.md).

|  |
| --- |
| Tip |
| You can combine both the Copy backups to object storage as soon as they are created option and the Move backups to object storage as they age out of the operational restores window option, as described in section [Copying Backups to Capacity Tier](capacity_tier_copy.md). |

![Step 5. Add Capacity Tier](images/capacity_tier_step.webp)

Synchronizing Capacity Tier Data

When you add as a capacity extent an object storage repository that contains offloaded backup data, you will be prompted to synchronize this data with the performance extents in the scale-out backup repository.

Consider the following:

* An object storage repository can only be added as a capacity extent after existing data (if any) is synchronized.
* During synchronization, Veeam Backup & Replication downloads backup files with metadata located in object storage to the performance extents that are part of the scale-out backup repository that is being added.

These files are created as described in section [Moving Backups to Capacity Tier](capacity_tier_move.md#dt).

* Extents to which backup data is going to be downloaded (synchronized), will be selected automatically, depending on the available resources.
* The actual data blocks will not be downloaded and will continue to remain in object storage.
* When synchronizing encrypted storage, make sure to provide the same exact password with which the data was encrypted.

After the synchronization is complete, the associated backup files located in object storage will become available as Imported and will be displayed in the Home view, under the Object Storage (Imported) node in the [inventory pane](vbr_ui.md).

[![Synchronizing Capacity Tier Data](images/sync_storage.webp)](images/sync_storage.webp "Synchronizing Capacity Tier Data")

Related Topics

* [Capacity Tier](capacity_tier.md)
* [Capacity Extent Structure](object_storage_repository_structure.md)
* [Data Transfer](capacity_tier_data_transfer.md)
* [Health Check for Capacity Tier](hc_capacity_tier.md)

Page updated 1/15/2026

Page content applies to build 13.0.1.1071
