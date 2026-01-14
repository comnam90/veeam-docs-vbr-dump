---
title: "Seeding Backups to Azure Blob Storage"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/data_box_seeding.html"
last_updated: "8/7/2025"
product_version: "13.0.1.1071"
---

# Seeding Backups to Azure Blob Storage

In this article

Seeding backups is an operation which can help in case you want to keep backups in object storage repositories and need to transfer backups in bulk to object storage. In this case, you can utilize the capabilities of the Azure Data Box device that will help you to transfer data from the local backup repository to Azure Blob storage and synchronize with the storage. Azure Data Box is a physical storage device that emulates a cloud storage endpoint and serves as an intermediate between the local backup repository and Azure Blob storage. With the help of Azure Data Box you will not need to create a full backup file and transfer it through the network which may result in high load on the network. Instead, you will transport all necessary data using Azure Data Box.

To seed data to Azure Blob storage, you need to order Azure Data Box from Microsoft, connect to it, copy backups from the local repository and ship it back to Microsoft. After the backup data is uploaded to your Azure Blob storage, you can perform initial sync and store your backups in Azure Blob storage later on.

For more information on ordering Azure Data Box, see [Azure Storage Documentation](https://docs.microsoft.com/en-us/azure/databox/data-box-deploy-ordered?tabs=portal).

|  |
| --- |
| Important |
| Consider the following limitations:   * We do not recommend offloading immutable data to the Azure Data Box device. If you do so, it will become mutable on the Azure Data Box device and will remain mutable after seeding. * You cannot seed data from the Azure Data Box device to Veeam Data Cloud Vault. |

To seed backups to Azure Blob Storage do the following:

1. Review [considerations and limitations.](#setup)
2. [Set up Azure Data Box](#setup).
3. [Add Azure Data Box to the backup infrastructure and then offload the data](#offload).
4. [Prepare Azure Data Box for shipping](#shipping).
5. [Synchronize the seeded data](#sync).

Setting up Azure Data Box

Before you add Azure Data Box to Veeam Backup & Replication, you need to set up the storage:

1. Install Azure Data Box. For more information, see [Azure Storage Documentation](https://docs.microsoft.com/en-us/azure/databox/data-box-deploy-set-up).
2. Connect to Azure Data Box through REST APIs. For more information, see [Azure Storage Documentation](https://docs.microsoft.com/en-us/azure/databox/data-box-deploy-copy-data-via-rest).

After you perform the steps in the Azure Storage Documentation, you will have a storage account name, access key, and blob service endpoint that you can use to add Azure Data Box to the backup infrastructure.

Adding Azure Data Box and Transferring the Data

To transfer backups to Azure Data Box, do the following:

1. Add Azure Data Box as an [Azure Data Box storage](osr_adding_data_box.md).
2. Add Azure Data Box storage as a standalone [object storage repository](osr_adding_blob_storage.md), the [capacity tier](new_capacity_tier.md) or [performance tier](backup_repository_sobr_extents.md) in a scale-out backup repository.

|  |
| --- |
| Important |
| When you configure a scale-out backup repository with Azure Blob storage as the [capacity extent](new_capacity_tier.md), make sure to select the Copy backups to object storage as soon as they are created check box as described in section [Add Capacity Tier](new_capacity_tier.md). In this case, you will keep copy of the data on your local storage which will help you to reduce the risk of data loss if the device is damaged during shipping. It will also ensure that the backup data is available for restore operations while Azure Blob storage is in shipment.  If you use the other type of backup repository, make sure to keep a copy of your backup in your local storage. |

Preparing Azure Data Box for Shipping

After you have completed copying backup data to the Azure Data Box, you need to ship this device back to Microsoft so that this data can be synchronized with your Azure storage account.

Before shipping Azure Data Box back to Microsoft, do the following:

1. Put an object storage repository that is associated with Azure Data Box into the Maintenance mode, as described in section [Switching to Maintenance Mode](sobr_maintenance.md).

|  |
| --- |
| Note |
| In case you have added Azure Data Box as a standalone object storage repository, make sure that you stop all backup job activities to prevent backups from modification. |

1. Perform the steps described in [Microsoft Docs](https://docs.microsoft.com/en-us/azure/databox/data-box-deploy-picked-up?tabs=in-us-canada-europe).

After shipping the device, wait for Microsoft to receive it and copy your data into your Azure storage account. You will be notified of successful data upload to your Azure storage account.

Synchronizing the Seeded Data

To connect Veeam Backup & Replication to your Azure storage account, do the following:

1. Add an Azure Blob storage, as described in section [Adding Azure Blob Storage](osr_adding_blob_storage.md). At the [Specify Object Storage Settings](azure_storage_details.md) step, select the same container and folder that you have selected for your Azure Data Box device.
2. Depending on the way you have added Azure Data Box, do one of the following:

* If you have added Azure Data Box as an object storage repository, as this Azure Data Box as the Azure Blob storage, rescan and map the jobs to the newly synced backups.
* If you have added Azure Data Box as an extent of a scale-out backup repository, edit settings of this scale-out backup repository. Change your Azure Data Box object storage to the Azure Blob storage.

1. Enable importing backups from Azure Blob storage and wait for the synchronization to complete.
2. Remove Azure Data Box object storage from the backup infrastructure, as described in section [Removing Object Storage Repository](object_storage_remove.md).

|  |
| --- |
| Note |
| Keep in mind that if you delete individual VMs from your backup in the period between mailing Azure Data Box and adding Azure Blob Storage, you may need to run Active Full instead of Incremental job after the final Azure synchronization. To avoid this, do not delete any VMs manually and disable the Retention Policy for Deleted Items option in the job settings for that period. After successful synchronization, you can re-enable this option and work as usual. |

Related Topics

[Adding Azure Data Box Storage](osr_adding_data_box.md)

Page updated 8/7/2025

Page content applies to build 13.0.1.1071
