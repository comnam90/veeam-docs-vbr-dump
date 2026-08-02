---
title: "New-VBRApplicationBackupSnapshot"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrapplicationbackupsnapshot.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRApplicationBackupSnapshot


Short Description

Creates a new snapshot of the application backup repository.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRApplicationBackupSnapshot -Repository <VBRApplicationBackupRepository>  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new snapshot of the application backup repository. You can use this snapshot to perform instant recovery or data recovery operations.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Repository | Specifies the application backup repository in which you want to create a snapshot. | Accepts the [VBRApplicationBackupRepository](vbrapplicationbackuprepository.md) object. To get this object, run the [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRApplicationBackupSnapshot](vbrapplicationbackupsnapshot.md) object that contains information about the application backup repository snapshot.

Examples

Creating Application Backup Repository Snapshot

This example shows how to create a snapshot in an application backup repository.

|  |
| --- |
| $repository = Get-VBRApplicationBackupRepository -Name "Application Backup Repository 01"  New-VBRApplicationBackupSnapshot -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the New-VBRApplicationBackupSnapshot cmdlet. Set the $repository variable as the Repository parameter value.

Related Commands

[Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md)

Page updated 2026-06-04

