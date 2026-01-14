---
title: "Get-VBRGoogleCloudBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudbackup.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudBackup

In this article

Short Description

Returns backups of Google Cloud VM instances.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGoogleCloudBackup [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns backups of Google Cloud VM instances. You can use these backups to restore Google Cloud VM instances or to create a backup copy job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of backup names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRGoogleCloudBackup object that contains backups of Google Cloud VM instances.

Examples

Getting all Backups of Google Cloud VM Instances

This command returns all backups of Google Cloud VM instances that were created by Veeam Backup & Replication.

|  |
| --- |
| Get-VBRGoogleCloudBackup |

Page updated 2/29/2024

Page content applies to build 13.0.1.1071
