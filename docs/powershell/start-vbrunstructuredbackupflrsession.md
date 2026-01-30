---
title: "Start-VBRUnstructuredBackupFLRSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrunstructuredbackupflrsession.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Start-VBRUnstructuredBackupFLRSession


Short Description

Starts a restore session to explore objects backed-up by file backup jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start a restore of files, folders or individual objects.

|  |
| --- |
| Start-VBRUnstructuredBackupFLRSession -Backup <VBRUnstructuredBackup> -Server <VBRUnstructuredServer>  [<CommonParameters>] |

* Start a restore of files, folders or individual objects. This parameter set recovers backup files or objects to the specified restore point.

|  |
| --- |
| Start-VBRUnstructuredBackupFLRSession -RestorePoint <VBRUnstructuredBackupRestorePoint>  [<CommonParameters>] |

Detailed Description

This cmdlet mounts backup content and allows you to restore files, folders and objects that are backed-up by file backup jobs or object storage backup jobs. You can mount backup content to one of the following options:

* Mount backup to the specific restore point.
* Mount all versions of backup files that are located on the specific file share or object storage. The cmdlet will mount all versions of backup files that are located on the short-term and long-term repositories.

You might want to use this mount session to restore specifics files and folders that are backed-up by file backup jobs and object storage backup jobs.

Run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet to get items that you want to restore.

Run the [Restore-VBRUnstructuredBackupFLRItem](restore-vbrunstructuredbackupflritem.md) cmdlet to restore the necessary files and folders.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the backup file. The cmdlet will start a file-level restore to recover all versions of a backup file that is located on the short-term and long-term repositories. | Accepts the  VBRUnstructuredBackup object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | True | Named | True (ByPropertyName |
| Server | Specifies file shares or object storage. The cmdlet will start a restore of files, folders or individual objects. This parameter set recovers backup files or objects to the specified restore point. | Accepts the VBRUnstructuredServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| RestorePoint | Specifies a restore point. The cmdlet will start a restore of files, folders or individual objects. This parameter set recovers backup files or objects to the specified restore point. | Accepts the VBRUnstructuredBackupRestorePoint object. To get this object, run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupFLRSession object that contains settings of restore sessions that are started to perform a file-level restore of backups that are created by file backup jobs and object storage backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Backups on Specific Object Storage

|  |  |
| --- | --- |
| This example shows how to start a file-level restore of backups that are located on a specific file share.  |  | | --- | | $backup = Get-VBRUnstructuredBackup  $server = Get-VBRUnstructuredServer -Backup $backup  Start-VBRUnstructuredBackupFLRSession -Backup $backup -Server $server |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Save the result to the $backup variable. 2. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $server variable. 3. Run the Start-VBRUnstructuredBackupFLRSession cmdlet. Set the $backup variable as the Backup parameter value. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Backups to Specific Restore Point

|  |  |
| --- | --- |
| This example shows how to start a file-level restore of backups to a specific restore point.  |  | | --- | | $restorepoint = Get-VBRUnstructuredBackupRestorePoint  Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint[3] |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable.   The Get-VBRUnstructuredBackupRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore session in the array).   1. Run the Start-VBRUnstructuredBackupFLRSession cmdlet. Set the $restorepoint[3] variable as the RestorePoint parameter value. |

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md)


