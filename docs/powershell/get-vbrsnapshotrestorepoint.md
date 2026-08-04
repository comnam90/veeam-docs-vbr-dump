---
title: "Get-VBRSnapshotRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsnapshotrestorepoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRSnapshotRestorePoint


Short Description

Returns restore points of InterSystems IRIS snapshot backups.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSnapshotRestorePoint [-Backup <VBRSnapshotBackup>] [-Id <Guid[]>] [-ObjectName <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points of InterSystems IRIS snapshot backups.

Use these restore points to restore InterSystems IRIS instances with the [Start-VBRIrisInstanceRestore](start-vbririsinstancerestore.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Backup | Specifies the snapshot backup whose restore points you want to get. | Accepts the [VBRSnapshotBackup](vbrsnapshotbackup.md) object. To get this object, run the [Get-VBRSnapshotBackup](get-vbrsnapshotbackup.md) cmdlet. | False | Named | True (ByPropertyName, ByValue) |
| Id | Specifies an array of IDs of restore points. The cmdlet will return restore points with these IDs. | Guid[] | False | Named | False |
| ObjectName | Specifies an array of names of InterSystems IRIS instances. The cmdlet will return restore points of these instances. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns an array of [VBRSnapshotRestorePoint](vbrsnapshotrestorepoint.md) objects that contain restore points of InterSystems IRIS snapshot backups.

Examples

Getting Restore Points of an InterSystems IRIS Snapshot Backup

This example shows how to get restore points of a specific InterSystems IRIS snapshot backup.

|  |
| --- |
| $backup = Get-VBRSnapshotBackup -Name "IRIS Backup Job"  Get-VBRSnapshotRestorePoint -Backup $backup[0] |

Perform the following steps:

1. Run the [Get-VBRSnapshotBackup](get-vbrsnapshotbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the Get-VBRSnapshotRestorePoint cmdlet. Set the $backup variable as the Backup parameter value.

Related Commands

* [Get-VBRSnapshotBackup](get-vbrsnapshotbackup.md)
* [Start-VBRIrisInstanceRestore](start-vbririsinstancerestore.md)

Page updated 2026-06-18

