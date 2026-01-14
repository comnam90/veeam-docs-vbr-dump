---
title: "Get-VBRUnstructuredBackupRestorePoint"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrunstructuredbackuprestorepoint.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRUnstructuredBackupRestorePoint

In this article

Short Description

Returns restore points created by file backup jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get a restore point for backups created by file backup jobs and object storage backup jobs.

|  |
| --- |
| Get-VBRUnstructuredBackupRestorePoint -Backup <VBRUnstructuredBackup[]> [-Server <VBRUnstructuredServer[]>]  [<CommonParameters>] |

* Get a restore point for backups created by file backup jobs and object storage backup jobs by the restore point ID.

|  |
| --- |
| Get-VBRUnstructuredBackupRestorePoint -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points created by file backup jobs file backup jobs and object storage backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an array of backup files created by file backup jobs and object storage backup jobs. The cmdlet will return restore points that are available for these backup files. | Accepts the VBRUnstructuredBackup[] object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Server | Specifies an array of file shares and object storage. The cmdlet will return backup files that are located on these file shares and object storage. | Accepts the VBRUnstructuredServer[] object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | False | Named | True (ByPropertyName) |
| Id | Specifies an array of IDs of restore points. The cmdlet will return restore points with this IDs. | Guid[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupRestorePoint object that contains settings of restore points created by file backup jobs file backup jobs and object storage backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Restore Point Created by Object Storage Job by ID

|  |  |
| --- | --- |
| This command returns the 51e4eced-3fce-465b-b516-f24cb5a068a4 restore point created by object storage job.  |  | | --- | | Get-VBRUnstructuredBackupRestorePoint -ID "51e4eced-3fce-465b-b516-f24cb5a068a4" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Point From Specific File Share

|  |  |
| --- | --- |
| This example shows how to get restore points of the NFS Backup backup file. The restore points are located on the \\WinSRV2049\Documents file share.  |  | | --- | | $backupfile = Get-VBRUnstructuredBackup -Name "NFS Backup"  $server = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  Get-VBRUnstructuredBackupRestorePoint -Server $server -Backup $backupfile |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backupfile variable. 2. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the Get-VBRUnstructuredBackupRestorePoint cmdlet. Set the $server variable as the Server parameter value. Set the $backupfile variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Latest Restore Point Created by File Backup job

|  |  |
| --- | --- |
| This command gets the latest restore point from an array of restore points.  |  | | --- | | $restorepoint = Get-VBRUnstructuredBackupRestorePoint | Sort-Object -Property CreationTime | Select-Object -Last 1 |  Perform the following steps:   1. Run the Get-VBRUnstructuredBackupRestorePoint cmdlet. Save the result to the $restorepoint variable. 2. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value as the Property parameter. Provide the Descending parameter. 3. Run the Select-Object cmdlet. Set the 1 value for the Last parameter. |

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)

* [Select-Object](https://docs.microsoft.com/en-us/PowerShell/module/microsoft.powershell.utility/select-object?view=powershell-6)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
