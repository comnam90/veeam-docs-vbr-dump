---
title: "Get-VBRSOBRObjectStorageBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsobrobjectstoragebackup.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRSOBRObjectStorageBackup


Short Description

Returns backups available in archive extents and capacity extents of scale-out backup repositories.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get backups available in archive extents and capacity extents by the job name.

|  |
| --- |
| Get-VBRSOBRObjectStorageBackup [-Name <String[]>] [-ArchiveTier] [-CapacityTier]  [<CommonParameters>] |

* Get backups available in archive extents and capacity extents by the backup ID.

|  |
| --- |
| Get-VBRSOBRObjectStorageBackup -Id <Guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns backups stored in archive extents and capacity extents of scale-out backup repositories.

|  |
| --- |
| Important |
| You can use the backups you get with this cmdlet only in the removal operations. Run the [Remove-VBRBackup](remove-vbrbackup.md) cmdlet and provide the FromDisk parameter to delete backups from archive extents and capacity extents of scale-out backup repositories. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of backup IDs. The cmdlet will return backups with these IDs. | Guid[] | True  Note: This parameter is not required, if you get backups using the job name. | Named | False |
| ArchiveTier | Defines that the cmdlet will return backups stored in archive extents of the scale-out backup repository.  Note: You do not need to provide this parameter if you specify the IDs of backed-up machines. | SwitchParameter | False | Named | False |
| CapacityTier | Defines that the cmdlet will return backups stored on capacity extents of the scale-out backup repository.  Note: You do not need to provide this parameter if you specify the IDs of backed-up machines. | SwitchParameter | False | Named | False |
| Name | Specifies an array of the job names. The cmdlet will return backups produced with these jobs. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSOBRObjectStorageBackup](vbrsobrobjectstoragebackup.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Backups from Archive and Capacity Extents

|  |  |
| --- | --- |
| This command returns all backups stored on archive and capacity extents of scale-out backup repositories.  |  | | --- | | Get-VBRSOBRObjectStorageBackup | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting all Backups from Capacity Extents

|  |  |
| --- | --- |
| This command returns all backups stored on capacity extents of scale-out backup repositories.  |  | | --- | | Get-VBRSOBRObjectStorageBackup -CapacityTier | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting all Backups from Archive Extents

|  |  |
| --- | --- |
| This command returns all backups stored in archive extents of scale-out backup repositories.  |  | | --- | | Get-VBRSOBRObjectStorageBackup -ArchiveTier | |


