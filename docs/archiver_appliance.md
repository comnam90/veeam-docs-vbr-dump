---
title: "Archiver Appliances"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/archiver_appliance.html"
last_updated: "9/19/2025"
product_version: "13.0.1.1071"
---

# Archiver Appliances

In this article

Archiver appliance is a temporary virtual machine that is located in the Public Cloud (AWS or Microsoft Azure). Veeam Backup & Replication uses it for the following operations:

* To transfer data from the capacity tier to the archive tier.
* To transfer data from performance tier that consist of object storage repositories to the archive tier.
* To perform health check operations of data blocks located in the performance tier.

To be able to use the archiver appliance, you must configure it at the Archiver Appliance step of the [Adding Amazon S3 Glacier](glacier_archiver_appliance.md) or [Adding Azure Archive Storage](azure_archive_tier_archiver_appliance.md) wizard. You can either create the archiver appliance with the default settings, or specify the archiver appliance settings manually: set up the size of the virtual machine and cloud resources where the archiver appliance will be created.

|  |
| --- |
| Note |
| Veeam Backup & Replication must be able to connect to the machine that you will use as an archiver appliance. Therefore, if your backup server is not located within the Public Cloud (AWS or Microsoft Azure), you must configure public IP addresses for the Amazon subnet or Azure virtual network in which the appliance resides. For more information on configuring the subnet for Amazon VPC, see [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/modify-subnets.html#subnet-public-ip). For more information on configuring the Azure virtual network, see [Microsoft Docs](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview). |

After the archiving job is finished, all the archiver appliances are automatically deleted. If the job ends prematurely, the archiver appliances will be deleted as well. Also, any archiver appliance can be deleted if there are no more tasks for it.

Limitations and Considerations

Consider the following:

* The archiver appliance is not used in case you do not configure it at the Archiver Appliance step of the [Adding Amazon S3 Glacier](glacier_archiver_appliance.md) or [Adding Azure Archive Storage](azure_archive_tier_archiver_appliance.md) wizard.

* The archiver appliance is used in case extents of your scale-out backup repository consists of the same object storage providers. For example, performance or capacity extents consist of [Microsoft Azure Blob storage](osr_adding_blob_storage.md) and the archive extent consist of [Azure Archive Storage](azure_archive_tier_archiver_appliance.md). If your scale-out backup repository has a mixed configuration, for example performance or capacity extents consist of an [Adding S3 Compatible Object Storage](adding_s3c_object_storage.md) and the archive extent consist of Azure Archive Storage, Veeam Backup & Replication will use the other component for the data transfer operation that might result in additional costs.

* The archiever appliance is not used for the direct data transfer from the performance tier to the archive tier if your scale-out backup repository has the following configuration:

* The archive tier consists of S3 compatible object storage with data archiving.
* The performance tier consist of a direct attached storage or network attached storage and the archive tier consist of Amazon S3 object storage or Microsoft Azure Blob storage.

In these cases, the component that transfers data depends on the connection type of the object storage repository:

* If you use the direct connection type, the data mover that runs on performance extents transfers data to the archive tier.
* If you use the connection through gateway servers, the specified gateway servers transfer data to the archive tier.

Page updated 9/19/2025

Page content applies to build 13.0.1.1071
