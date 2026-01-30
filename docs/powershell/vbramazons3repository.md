---
title: "VBRAmazonS3Repository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbramazons3repository.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRAmazonS3Repository


Contains settings of the Amazon S3 object storage repository.

Properties

| Property | Type | Description |
| --- | --- | --- |
| AmazonS3Folder | [VBRAmazonS3Folder](vbramazons3folder.md) | Amazon folder. |
| EnableIAStorageClass | Bool | Defines that the infrequent access storage class is enabled (TRUE) or not enabled (FALSE). |
| EnableOZIAStorageClass | Bool | Defines that the One Zone-IA storage class enabled (TRUE) or not enabled (FALSE). |
| BackupImmutabilityEnabled | Bool | Defines that the backup immutability option enabled (TRUE) or not enabled (FALSE). |
| ImmutabilityPeriod | Int | Immutability period in days. |
| MountServerOptions | [VBRRepositoryMountServerOptions](vbrrepositorymountserveroptions.md) | Mount server settings. |


