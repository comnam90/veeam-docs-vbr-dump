---
title: "Limitations for Performance Tier"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/performance_tier_limitations.html"
last_updated: "1/2/2026"
product_version: "13.0.1.1071"
---

# Limitations for Performance Tier

In this article

Consider the following limitations for the performance tier:

* The same limitations that are specific for certain types of backup repositories apply to the performance extents. For example, if you add Dell Data Domain as a performance extent to the scale-out backup repository, you will not be able to create a backup chain longer than 120 points in this scale-out backup repository.
* The performance extents of the scale-out backup repository should be located in the same site. Technically, you can add to the scale-out backup repository the performance extents that reside in different sites. However, in this case Veeam Backup & Replication will have to access VM backup files on storage devices in different locations, and the backup performance will degrade.
* If you plan to use an HA cluster, make sure that your performance tier does not consist of local repositories.

* Within a scale-out backup repository, the mount server of a performance extent will act as a gateway server of the capacity extent if all of the following is true:

1. You use SMB share/NFS share/deduplicating storage appliances as performance extents of your scale-out backup repository.
2. You have chosen Automatic selection for the gateway server at the [Specify Shared Folder Settings](repository_server.md) step of the New backup repository wizard.
3. For the object storage that you use as the capacity extent, you have not selected to connect to object storage using a gateway server at the Account step of the New Object Repository wizard.

* If you want to add object storage repositories of another provider as performance extents, you must switch the object storage of the former extent [to the sealed mode](sobr_seal.md). For example, if you used Amazon S3 object storage as performance extents and you want to add Microsoft Azure Blob as a new extent, you must first seal the Amazon S3 object storage.

* If you want to use S3-compatible repositories by different providers as performance extents, one of this repository must be in the sealed mode. For example, if you want to use both Wasabi Cloud object storage and IBM Cloud object storage within the same performance tier, Wasabi Cloud object storage must be in [sealed mode](sobr_seal.md).

* You cannot have a mixed configuration and use different types of repositories within one performance tier. For example, a performance tier cannot consist of a Windows-based backup repository and the object storage repository added as performance extents.

* Data located in object storage repositories is organized into a separate backup chain for every machine in a job.

* If you use immutability and have several extents in your performance tier, you must enable it for all active extents within this tier. If your performance tier consists of object storage repositories and you want to use a mixed immutability configuration (with some extents immutable and some mutable), you must switch either all mutable or all immutable extents to the sealed mode.

|  |
| --- |
| Note |
| You can apply the mixed immutability configuration for performance tier only if it consists of object storage repositions. For other types of backup repositories mixed immutability configuration is not supported. |

* You cannot add as performance extents one Wasabi bucket as an [S3 Compatible Object Storage](adding_s3c_object_storage.md) and another Wasabi bucket as a [Wasabi Cloud Object Storage](adding_wasabi_object_storage.md) to the same type of tier (either performance tier or capacity tier) of a scale-out backup repository.
* You cannot use the same object storage repository as a performance extent and as a capacity extent.

* Veeam Cloud Connect service providers can not use Azure Data Box and AWS Snowball Edge storage as a performance extent of a scale-out backup repository.

* You cannot use direct backup object storage repositories as performance extents to keep backups created with [Veeam Plug-Ins for Enterprise Applications](protect_applications.md).
* [For VeeamZIP] You cannot move VeeamZIP backups to direct object storage repositories or when they are added as a performance tier of a scale-out backup repository. However, you can still move VeeamZIP backups to an object storage repository used as capacity tier.

Page updated 1/2/2026

Page content applies to build 13.0.1.1071
