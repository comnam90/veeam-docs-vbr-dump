---
title: "Get-VBRPublishedBackupContentInfo"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrpublishedbackupcontentinfo.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Get-VBRPublishedBackupContentInfo

In this article

Short Description

Returns details on the published disks.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRPublishedBackupContentInfo -Session <VBRBackupContentPublicationSession>  [<CommonParameters>] |

Detailed Description

This cmdlet returns details on the published disks.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a session that is running to publish disks. The cmdlet will return details on the disks published during this session. | Accepts the VBRBackupContentPublicationSession object. To get this object, run the [Get-VBRPublishedBackupContentSession](get-vbrpublishedbackupcontentsession.md) cmdlet. | True | 0 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRPublishedBackupContentSession object that contains details on the published disks.

Examples

Getting Details on Content of Backup Files

This example shows how to get details on the published disks.

|  |
| --- |
| $session = Get-VBRPublishedBackupContentSession  Get-VBRPublishedBackupContentInfo -Session $session |

Perform the following steps:

1. Run the [Get-VBRPublishedBackupContentSession](get-vbrpublishedbackupcontentsession.md) cmdlet. Save the result to the $session variable.
2. Run the Get-VBRPublishedBackupContentInfo cmdlet. Set the $session variable as the Session parameter value.

The cmdlet output will contain the following details on the mounted content of backup files: Mode, ServerIps, ServerPort and the Disks.

Related Commands

[Get-VBRPublishedBackupContentSession](get-vbrpublishedbackupcontentsession.md)

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
