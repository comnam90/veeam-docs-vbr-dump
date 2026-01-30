---
title: "VBRGoogleCloudRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrgooglecloudrepository.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# VBRGoogleCloudRepository


Contains Google Cloud object storage repository.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | Guid | Id of a Google Cloud object storage. |
| Name | string | Name of a Google Cloud object storage. |
| Description | string | Description of a Google Cloud object storage. |
| Type | [VBRObjectStorageRepositoryType](enums.md#VBRObjectStorageRepositoryType) | Type of a Google Cloud object storage |
| GateWayMode | [VBRRepositoryConnectionType](enums.md#VBRRepositoryConnectionType) | Gateway mode. |
| GatewayServer | CHost[] | Gateway server. |
| MountServerOptions | [VBRRepositoryMountServerOptions](vbrrepositorymountserveroptions.md) | Mount server settings. |
| SizeLimitEnabled | bool | Defines that size limits are enabled (TRUE) or not enabled (FALSE) for for the Google Cloud storage. |
| SizeLimit | Int | Size limits in GB. |
| Folder | [VBRGoogleCloudFolder](vbrgooglecloudfolder.md) | Google Cloud folder. |
| EnableNearlineStorageClass | bool | Defines that the nearline storage class is enabled (TRUE) or not enabled (FALSE) for for the Google Cloud storage. |
| MaxTaskCount | Int | Number of concurrent tasks. |

Related Commands

[Add-VBRGoogleCloudRepository](add-vbrgooglecloudrepository.md)


