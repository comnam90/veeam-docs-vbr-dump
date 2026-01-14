---
title: "Get-VBRNASBackupRestorePoint (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasbackuprestorepoint.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNASBackupRestorePoint (obsolete)

In this article

Short Description

Returns restore points of backups created by file backup jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all restore points that are created by file backup jobs.

|  |
| --- |
| Get-VBRNASBackupRestorePoint  [<CommonParameters>] |

* Get a restore point by the restore point ID.

|  |
| --- |
| Get-VBRNASBackupRestorePoint -Id <guid[]>  [<CommonParameters>] |

* Get a restore point available for the specific backup located on the specific file share.

|  |
| --- |
| Get-VBRNASBackupRestorePoint -NASBackup <VBRNASBackup[]> [-NASServer <VBRNASServer[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points created by file backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs of backed-up file shares. The cmdlet will return restore points of these file shares. | Guid[] | True | Named | False |
| NASBackup | Specifies an array of backup files created by the file backup job. The cmdlet will return restore points that are available for these backup files. | Accepts the VBRNASBackup[] object. To get this object, run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| NASServer | Specifies an array of file shares. The cmdlet will return backup files that are located on these file shares. | Accepts the VBRNASServer[] object. To get this object, run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNASBackupRestorePoint](vbrnasbackuprestorepoint.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Restore Points

|  |  |
| --- | --- |
| This command returns all restore points that are created by file backup jobs.  |  | | --- | | Get-VBRNASBackupRestorePoint | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Point by ID

|  |  |
| --- | --- |
| This command returns the 51e4eced-3fce-465b-b516-f24cb5a068a4 restore point.  |  | | --- | | Get-VBRNASBackupRestorePoint -ID "51e4eced-3fce-465b-b516-f24cb5a068a4" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Restore Point From Specific File Share

|  |  |
| --- | --- |
| This example shows how to get restore points of the NFS Backup backup file. The restore points are located on the \\WinSRV2049\Documents file share.  |  | | --- | | $backupfile = Get-VBRNASBackup -Name "NFS Backup"  $server = Get-VBRNASServer -Name "\\WinSRV2049\Documents"  Get-VBRNASBackupRestorePoint -NASServer $server -NASBackup $backupfile |  Perform the following steps:   1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backupfile variable. 2. Run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the Get-VBRNASBackupRestorePoint cmdlet. Set the $server variable as the NASServer parameter value. Set the $backupfile variable as the NASBackup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Latest Restore Point

|  |  |
| --- | --- |
| This command gets the latest restore point from an array of restore points.  |  | | --- | | $restorepoint = Get-VBRNASBackupRestorePoint | Sort-Object -Property CreationTime | Select-Object -Last 1 |  Perform the following steps:   1. Run the Get-VBRNASBackupRestorePoint cmdlet. Save the result to the $restorepoint variable. 2. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value as the Property parameter. Provide the Descending parameter. 3. Run the Select-Object cmdlet. Set the 1 value for the Last parameter. |

Related Commands

* [Get-VBRNASBackup](get-vbrnasbackup.md)
* [Get-VBRNASServer](get-vbrnasserver.md)
* [Select-Object](https://docs.microsoft.com/en-us/PowerShell/module/microsoft.powershell.utility/select-object?view=powershell-6)

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
