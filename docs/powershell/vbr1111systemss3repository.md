---
title: "VBR1111SystemsS3Repository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbr1111systemss3repository.html"
last_updated: "11/22/2024"
product_version: "13.0.1.1071"
---

# VBR1111SystemsS3Repository

In this article

Contains settings of the 11:11 Cloud Object Storage.

Properties

| Property | Type | Description |
| --- | --- | --- |
| AmazonS3Folder | [VBRAmazonS3Folder](vbramazons3folder.md) | Amazon folder. |
| EnableIAStorageClass | Bool | Defines that the infrequent access storage class is enabled (TRUE) or not enabled (FALSE). |
| BackupImmutabilityEnabled | Bool | Defines that the backup immutability option enabled (TRUE) or not enabled (FALSE). |
| ImmutabilityPeriod | Int | Immutability period in days. |
| MountServerOptions | [VBRRepositoryMountServerOptions](vbrrepositorymountserveroptions.md) | Mount server settings. |
| ProxyAppliance | CHost | Proxy appliance. |

Page updated 11/22/2024

Page content applies to build 13.0.1.1071
