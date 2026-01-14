---
title: "Get-VBRSOBRObjectStorageRestorePoint"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsobrobjectstoragerestorepoint.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRSOBRObjectStorageRestorePoint

In this article

Short Description

Returns restore points stored in archive extents and capacity extents of a scale-out backup repository.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get restore points stored in archive extents or capacity extents by the name of a backed-up machine.

|  |
| --- |
| Get-VBRSOBRObjectStorageRestorePoint [-Name <String[]>] [-CapacityTier] [-ArchiveTier]  [<CommonParameters>] |

* Get restore points stored in archive extents or capacity extents associated with specific backups.

|  |
| --- |
| Get-VBRSOBRObjectStorageRestorePoint -Backup <VBRSOBRObjectStorageBackup> [-Name <String[]>]  [<CommonParameters>] |

* Get restore points stored in archive extents or capacity extents by their IDs.

|  |
| --- |
| Get-VBRSOBRObjectStorageRestorePoint -Id <Guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points of machines stored in archive extents and capacity extents of a scale-out backup repository.

|  |
| --- |
| Important |
| You can use the restore points you get with this cmdlet only in the removal operations. Run the [Remove-VBRRestorePoint](remove-vbrrestorepoint.md) cmdlet to delete restore points from archive extents and capacity extents of scale-out backup repositories. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for machines. The cmdlet will return restore points of these machines. | String[] | False | Named | False |
| CapacityTier | Defines that the cmdlet will return restore points of machines stored on capacity extents.  Note: You do not need to provide this parameter if you specify the IDs of backed-up machines. | SwitchParameter | False | Named | False |
| ArchiveTier | Defines that the cmdlet will return restore points of machines stored in archive extents.  Note: You do not need to provide this parameter if you specify the IDs of backed-up machines. | SwitchParameter | False | Named | False |
| Backup | Specifies an array of backups stored in archive extents or capacity extents. The cmdlet will return restore points of these backups. | Accepts the VBRSOBRObjectStorageBackup object. To get this object, run the [Get-VBRSOBRObjectStorageBackup](get-vbrsobrobjectstoragebackup.md) cmdlet. | False | Named | True (ByValue) |
| Id | Specifies an array of IDs of backed-up machines. The cmdlet will return restore points of these machines. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSOBRObjectStorageRestorePoint](vbrsobrobjectstoragerestorepoint.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Restore Points from Archive and Capacity Extents

|  |  |
| --- | --- |
| This command returns all restore points stored on archive and capacity extents of a scale-out backup repository.  |  | | --- | | Get-VBRSOBRObjectStorageRestorePoint | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Points of Certain Machines from Archive Extent

|  |  |
| --- | --- |
| This example shows how to get restore points of the LinServ2049 and WinServ2049 machines with the following settings:   * Restore points are created by the DailyBackup job. * Restore points are stored in archive extents of a scale-out backup repository.   |  | | --- | | $backup = Get-VBRSOBRObjectStorageBackup -Name "DailyBackup"  Get-VBRSOBRObjectStorageRestorePoint -Backup $backup -Name "LinServ2049", "WinServ2049" -ArchiveTier |  Perform the following steps:   1. Run the [Get-VBRSOBRObjectStorageBackup](get-vbrsobrobjectstoragebackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Get-VBRSOBRObjectStorageRestorePoint cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Restore Points with Certain IDs

|  |  |
| --- | --- |
| This command returns the c2befce4-c7f4-4a53-a08b-e37580a682e7 and 9577ab06-8ca5-4a5a-bd5c-d6124b0a4058 restore points. The cmdlet will get these restore points from capacity tier extents of a scale-out backup repository.  |  | | --- | | Get-VBRSOBRObjectStorageRestorePoint -Id "c2befce4-c7f4-4a53-a08b-e37580a682e7", "9577ab06-8ca5-4a5a-bd5c-d6124b0a4058" | |

Related Commands

[Get-VBRSOBRObjectStorageBackup](get-vbrsobrobjectstoragebackup.md)

Page updated 2/29/2024

Page content applies to build 13.0.1.1071
