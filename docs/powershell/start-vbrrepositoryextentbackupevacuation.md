---
title: "Start-VBRRepositoryExtentBackupEvacuation"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrrepositoryextentbackupevacuation.html"
last_updated: "2/9/2024"
product_version: "13.0.1.1071"
---

# Start-VBRRepositoryExtentBackupEvacuation

In this article

Short Description

Evacuates backups from a scale-out backup repository extent.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRRepositoryExtentBackupEvacuation -Extent <VBRRepositoryExtent[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet evacuates backups from a scale-out backup repository extent. When you evacuate backups, Veeam moves them to other extents according to the configured policy.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Extent | Specifies the array of scale-out repository extents. The cmdlets will evacuate backups from these extents.  Accepts extents with different policies and of different scale-out repositories. | Accepts the following object:   * ID * String (name of the backup repository that is used as extent) * [VBRRepositoryExtent](vbrrepositoryextent.md)   To get this object, run the [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Evacuating Backups from Extents

This command evacuates backups from the Backup Repository 1, Backup Repository 2, Backup Repository 3 extents.

|  |
| --- |
| Start-VBRRepositoryExtentBackupEvacuation –Extent “Backup Repository 1”, “Backup Repository 2”, “Backup Repository 3” |

Related Commands

[Get-VBRRepositoryExtent](get-vbrrepositoryextent.md)

Page updated 2/9/2024

Page content applies to build 13.0.1.1071
