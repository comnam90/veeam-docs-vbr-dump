---
title: "Unpublish-VBRBackupContent"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/unpublish-vbrbackupcontent.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Unpublish-VBRBackupContent


Short Description

Unpublishes disks.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Unpublish-VBRBackupContent -Session <VBRBackupContentPublicationSession[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet unpublishes disks.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the array of sessions that are running to publish disks. | Accepts the VBRBackupContentPublicationSession[] object. To get this object, run the [Get-VBRPublishedBackupContentSession](get-vbrpublishedbackupcontentsession.md) cmdlet. | True | 0 | True (ByPropertyName, ByValue) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Unpublishing Disks [Using Pipeline]

This command unpublishes disks.

|  |
| --- |
| Get-VBRPublishedBackupContentSession | Unpublish-VBRBackupContent -RunAsync |

Related Commands

[Get-VBRPublishedBackupContentSession](get-vbrpublishedbackupcontentsession.md)


