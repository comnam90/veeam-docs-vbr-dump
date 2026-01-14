---
title: "Adding Azure Data Box Storage"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/osr_adding_data_box.html"
last_updated: "1/16/2025"
product_version: "13.0.1.1071"
---

# Adding Azure Data Box Storage

In this article

[Azure Data Box](https://docs.microsoft.com/en-us/azure/databox/data-box-overview) is a physical device which you can request for a short period of time from Microsoft. You can temporarily attach it to the backup infrastructure and use it as an object storage. For more information about ordering Azure Data Box and preparing to use it, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/databox/data-box-deploy-ordered).

This device may become useful when you need to offload a significant number of backup files occupying storage space on your extents, as offloading data to the Azure Data Box device is much faster than transferring the same amount of data directly to Azure object storage. Once you have offloaded backups to Azure Data Box, you need to ship the device back to Microsoft for further data synchronization with your Azure storage account, as described in section [Seeding Backups to Azure Blob Storage](data_box_seeding.md).

General Considerations and Limitations

Consider the following:

* Veeam Backup & Replication supports only those Azure Data Box devices that are capable of reading and writing data using REST API.
* The Azure Data Box disk type is not supported.
* Direct data copy to the archive tier from Azure Data Box is not supported. When you place your order, do not enable Copy to archive option on the Data destination step.
* When you configure a scale-out backup repository with Azure Data Box as the [capacity extent](new_capacity_tier.md), it is recommended to only use the copy policy. This way you keep copy of the data on your local storage which helps you reduce the risk of data loss if the device is damaged during shipping. It will also ensure that the backup data is available for restore operations while Azure Data Box is in shipment.
* We do not recommend offloading immutable data to the Azure Data Box device. If you do so, it will become mutable on the Azure Data Box device and will remain mutable after [seeding](data_box_seeding.md).
* You cannot [seed](data_box_seeding.md) data from the Azure Data Box device to Veeam Data Cloud Vault.
* You can add only one Azure Data Box device to a scale-out backup repository.

* Veeam Cloud Connect service providers can use Azure Data Box only as a capacity extent of a scale-out backup repository.
* You cannot back up data using Veeam Agent backup job or policy to Azure Data Box devices.

For information about other limitations for Microsoft Azure Data Box storage, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/databox/data-box-limits).

To add Microsoft Azure Blob storage, use the New Object Storage Repository wizard.

1. [Check prerequisites](before_you_begin_data_box.md).
2. [Launch the New Object Storage Repository wizard](azure_db_repository_launch.md).
3. [Specify object storage name](azure_db_repository_name.md).
4. [Specify object storage account](azure_db_repository_account.md).
5. [Specify object storage settings](azure_db_storage_details.md).
6. [Finish working with the wizard](azure_db_finishing_wizard.md).

Page updated 1/16/2025

Page content applies to build 13.0.1.1071
