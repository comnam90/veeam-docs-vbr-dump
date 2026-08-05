---
title: "Get-VBRSnapshotBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsnapshotbackup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRSnapshotBackup


Short Description

Returns InterSystems IRIS snapshot backups.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSnapshotBackup [-Id <Guid[]>] [-Name <String[]>] [-JobId <Guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns InterSystems IRIS snapshot backups created by application backup policies.

Use the returned object to get restore points with the [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Id | Specifies an array of IDs of snapshot backups. The cmdlet will return snapshot backups with these IDs. | Guid[] | False | Named | False |
| Name | Specifies an array of names of snapshot backups. The cmdlet will return snapshot backups with these names. | String[] | False | Named | False |
| JobId | Specifies an array of IDs of application backup policies. The cmdlet will return snapshot backups created by jobs with these IDs. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns an array of [VBRSnapshotBackup](vbrsnapshotbackup.md) objects that contain InterSystems IRIS snapshot backups.

Examples

Getting InterSystems IRIS Snapshot Backups by Name

This example shows how to get an InterSystems IRIS snapshot backup by its name.

|  |
| --- |
| Get-VBRSnapshotBackup -Name "IRIS Backup Job" |

Run the Get-VBRSnapshotBackup cmdlet. Specify the Name parameter value.

Related Commands

* [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md)

Page updated 2026-06-18

