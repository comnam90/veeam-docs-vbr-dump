---
title: "VBRIBMCloudRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbribmcloudrepository.html"
last_updated: "7/1/2025"
product_version: "13.0.1.1071"
---

# VBRIBMCloudRepository

In this article

Contains settings of the 11:11 Cloud Object Storage.

Properties

| Property | Type | Description |
| --- | --- | --- |
| AmazonS3Folder | [VBRAmazonS3Folder](vbramazons3folder.md) | Amazon folder. |
| EnableIAStorageClass | Bool | Defines that the infrequent access storage class is enabled (TRUE) or not enabled (FALSE). |
| BackupImmutabilityEnabled | Bool | Defines that the backup immutability option enabled (TRUE) or not enabled (FALSE). |
| ImmutabilityMode | [VBRRepositoryImmutabilityMode](enums.md#vbrrepositoryimmutabilitymode) | Immutability mode. |
| ImmutabilityPeriod | Int | Immutability period in days. |
| MountServerOptions | [VBRRepositoryMountServerOptions](vbrrepositorymountserveroptions.md) | Mount server settings. |
| ProxyAppliance | CHost | Proxy appliance. |

Page updated 7/1/2025

Page content applies to build 13.0.1.1071
