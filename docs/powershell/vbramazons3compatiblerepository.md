---
title: "VBRAmazonS3CompatibleRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbramazons3compatiblerepository.html"
last_updated: "11/4/2024"
product_version: "13.0.1.1071"
---

# VBRAmazonS3CompatibleRepository


Contains settings of S3 compatible object storage repository.

Properties

| Property | Type | Description |
| --- | --- | --- |
| AmazonS3Folder | [VBRAmazonS3Folder](vbramazons3folder.md) | Amazon folder. |
| ServicePoint | String | Service point settings. |
| BackupImmutabilityEnabled | Bool | Indicates if backup immutability option enabled (TRUE) or not enabled (FALSE). |
| ImmutabilityPeriod | Int | Immutability period in days. |
| MountServerOptions | [VBRRepositoryMountServerOptions](vbrrepositorymountserveroptions.md) | Mount server settings. |
| ProxyAppliance | CHost | Proxy appliance host. |
| BucketAutoProvisionEnabled | Boolean | Defines if the multiple buckets option for S3 compatible object storage repository is enabled. |
| MachinesPerBucketLimit | Int32 | Amount of per-machine backup chains per a child bucket. |


