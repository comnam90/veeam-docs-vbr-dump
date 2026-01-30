---
title: "Get-VBRPublishedBackupContentSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrpublishedbackupcontentsession.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VBRPublishedBackupContentSession


Short Description

Returns sessions that are running to publish disks from a backup or replica.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRPublishedBackupContentSession -Id <Guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of sessions that are running to publish disks.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of session IDs. The cmdlet will return sessions that have the specified IDs. | Guid[] | True | 0 | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRPublishedBackupContentSession object that contains settings of the publishing sessions.

Examples

Getting Sessions that are Running to Publish Disks

This command returns an array of sessions that are running to publish disks.

|  |
| --- |
| Get-VBRPublishedBackupContentSession |


