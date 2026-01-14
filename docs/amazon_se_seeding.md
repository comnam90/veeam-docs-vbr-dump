---
title: "Seeding Backups to Amazon S3 Storage"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/amazon_se_seeding.html"
last_updated: "8/1/2024"
product_version: "13.0.1.1071"
---

# Seeding Backups to Amazon S3 Storage

In this article

Seeding backups is an operation which can be helpful in case you want to start using object storage repositories and need to transfer a bulk amount of data to object storage. In this case, you can utilize the capabilities of the AWS Snowball Edge device that will help you to transfer data from the local backup repository to Amazon S3 storage and synchronize with the storage. AWS Snowball Edge is a physical storage device that emulates a cloud storage endpoint and serves as an intermediate between the local backup repository and Amazon S3 storage. With the help of AWS Snowball Edge you will not need to create a full backup file and transfer it through the internet which can result in high load on the network. Instead you will transport all necessary data using AWS Snowball Edge.

To seed data to Amazon S3 storage, you need to order AWS Snowball Edge from AWS, connect to it, copy backups from the local repository and ship it back to AWS. After the backup data is uploaded to your Amazon S3 storage, you can perform initial sync and store your backups in Amazon S3 storage later on.

For more information on AWS Snowball Edge, see [AWS Documentation](https://docs.aws.amazon.com/snowball/latest/developer-guide/whatisedge.html).

|  |
| --- |
| Note |
| Before you seed backups to AWS Snowball Edge, make sure to review [considerations and limitations](byb_snow.md). |

To seed backups to AWS Snowball Edge do the following:

1. [Set up AWS Snowball Edge](#setup).
2. [Add AWS Snowball Edge to the backup infrastructure and then offload the data](#offload).
3. [Prepare AWS Snowball Edge for shipping](#shipping).
4. [Synchronize the seeded data](#sync).

Setting up AWS Snowball Edge Device

Before you add AWS Snowball Edge to Veeam Backup & Replication, you need to order the device, connect it to your local network, download and install the Snowball edge client and configure the device. For detailed instructions on these steps, see [AWS Documentation](https://docs.aws.amazon.com/snowball/latest/developer-guide/getting-started.html).

After that, you will have a service point address, access key and a secret key that you can use to add AWS Snowball Edge to the backup infrastructure.

Adding AWS Snowball Edge and Transferring the Data

To transfer backups to AWS Snowball Edge, do the following:

1. Add AWS Snowball Edge as [AWS Snowball Edge Storage](osr_amazon_se_adding.md).
2. Add AWS Snowball Edge as a standalone [object storage repository](osr_adding_blob_storage.md), the [capacity tier](new_capacity_tier.md) or [performance tier](backup_repository_sobr_extents.md) in a scale-out backup repository.

|  |
| --- |
| Important |
| When you configure a scale-out backup repository with AWS Snowball Edge as the [capacity extent](new_capacity_tier.md), make sure to select the Copy backups to object storage as soon as they are created check box as described in section [Add Capacity Tier](new_capacity_tier.md). In this case, you will keep copy of the data on your local storage which will help you to reduce the risk of data loss if the device is damaged during shipping. It will also ensure that the backup data is available for restore operations while AWS Snowball Edge is in shipment.  If you use the other type of backup repository, make sure to keep a copy of your backup in your local storage. |

Preparing AWS Snowball Edge for Shipping

After you have completed copying backup data to the AWS Snowball Edge device, you need to ship this device back to Amazon so that this data can be synchronized with your Amazon S3 storage.

Before shipping AWS Snowball Edge back to AWS, do the following:

1. Put an object storage repository that is associated with AWS Snowball Edge into the Maintenance mode, as described in section [Switching to Maintenance Mode](sobr_maintenance.md).

|  |
| --- |
| Note |
| In case you have added AWS Snowball Edge as a standalone object storage repository, make sure that you stop all backup job activities to prevent backups from modification. |

1. Power off AWS Snowball Edge. For more information, see [AWS Documentation](https://docs.aws.amazon.com/snowball/latest/developer-guide/turnitoff.html).
2. Ship AWS Snowball Edge back to AWS. For more information, see [AWS Documentation](https://docs.aws.amazon.com/snowball/latest/developer-guide/return-device.html).

After mailing the device, wait until it is accepted by AWS and notification of successful data upload to your storage account is received (if you subscribed for such notification).

Synchronizing the Seeded Data

To connect Veeam Backup & Replication to your Amazon S3 storage account, do the following:

1. Add an Amazon S3 storage, as described in section [Adding Amazon S3 Storage](osr_amazon_adding.md). At the [Specify Object Storage Settings](amazon_storage_details.md) step, select the same bucket and folder that you have selected for your AWS Snowball Edge device.
2. Depending on the way you have added AWS Snowball Edge, do one of the following:

* If you have added AWS Snowball Edge as an object storage repository, as this AWS Snowball Edge as the Amazon S3 storage, rescan and map the jobs to the newly synced backups.
* If you have added AWS Snowball Edge as an extent of a scale-out backup repository, edit settings of this scale-out backup repository. Change your AWS Snowball Edge object storage to the Amazon S3 storage.

1. Enable importing backups from Amazon S3 storage and wait for the synchronization to complete.
2. Remove the AWS Snowball Edge object storage from the backup infrastructure, as described in section [Removing Object Storage Repository](object_storage_remove.md).

Related Topics

[Adding AWS Snowball Edge Storage](osr_amazon_se_adding.md)

Page updated 8/1/2024

Page content applies to build 13.0.1.1071
