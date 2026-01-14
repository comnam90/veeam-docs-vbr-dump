---
title: "VBRAmazonS3GlacierRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbramazons3glacierrepository.html"
last_updated: "3/27/2024"
product_version: "13.0.1.1071"
---

# VBRAmazonS3GlacierRepository

In this article

Amazon S3 Glacier archive storage repository.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Connection | [VBRAmazonS3Connection](vbramazons3connection.md) | Amazon connection. |
| AmazonS3Folder | [VBRAmazonS3Folder](vbramazons3folder.md) | Amazon folder. |
| AmazonProxySpec | [VBRAmazonEC2ProxyAppliance](vbramazonec2proxyappliance.md) | Proxy appliance. |
| Name | String | Storage name. |
| Description | Bool | Storage description. |
| UseDeepArchive | SwitchParameter | Defines that the Glacier Deep Archive storage class is assigned (TRUE) or not assigned (FALSE) for backup files. |
| UseInstantRetrieval | SwitchParameter | Defines that the Amazon S3 Glacier Instant Retrieval storage class is assigned (TRUE) or not assigned (FALSE) for backup files. |
| EnableBackupImmutability | SwitchParameter | Defines if backup immutability option enabled (TRUE) or not enabled (FALSE). |
| Force | SwitchParameter | Defines that the cmdlet will add object storage without showing warnings in the PowerShell console. |

Page updated 3/27/2024

Page content applies to build 13.0.1.1071
