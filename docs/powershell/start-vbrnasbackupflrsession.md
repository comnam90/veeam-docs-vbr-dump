---
title: "Start-VBRNASBackupFLRSession (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrnasbackupflrsession.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Start-VBRNASBackupFLRSession (obsolete)

In this article

Short Description

Starts a restore session to explore objects backed-up by file backup jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start a file-level restore to recover backup files to the specified restore point.

|  |
| --- |
| Start-VBRNASBackupFLRSession -RestorePoint <VBRNASBackupRestorePoint>  [<CommonParameters>] |

* Start a file-level restore to recover all versions of backup files.

|  |
| --- |
| Start-VBRNASBackupFLRSession -NASBackup <VBRNASBackup> -NASServer <VBRNASServer>  [<CommonParameters>] |

Detailed Description

This cmdlet mounts backup content and allows you to restore files and folders that are backed-up by file backup jobs. You can mount backup content to one of the following options:

* Mount backup to the specific restore point.
* Mount all versions of backup files that are located on the specific file share. The cmdlet will mount all versions of backup files that are located on the short-term and long-term repositories.

You might want to use this mount session to restore specifics files and folders that are backed-up by file backup jobs.

Run the [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md) cmdlet to get items that you want to restore.

Run the [Restore-VBRNASBackupFLRItem](restore-vbrnasbackupflritem.md) cmdlet to restore the necessary files and folders.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point. The cmdlet will start a file-level restore to recover backup files to the specified restore point. | Accepts the VBRNASBackupRestorePoint object. To get this object, run the [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| NASBackup | Specifies an array of backup files. The cmdlet will start a file-level restore to recover all versions of backup files that are located on the short-term and long-term repositories. | Accepts the VBRNASBackup object. To get this object, run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. | True | Named | True (ByPropertyName |
| NASServer | Specifies an array of file shares. The cmdlet will start a file-level restore to recover all versions of backup files that are located on the specified file shares. | Accepts the VBRNASServer object. To get this object, run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNASBackupRestorePoint](vbrnasbackuprestorepoint.md) object that contains settings of restore sessions that are started to perform a file-level restore of backups that are created by file backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Backups to Specific Restore Point

|  |  |
| --- | --- |
| This example shows how to start a file-level restore of backups to a specific restore point.  |  | | --- | | $restorepoint = Get-VBRNASBackupRestorePoint  Start-VBRNASBackupFLRSession -RestorePoint $restorepoint |  Perform the following steps:   1. Run the [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the Start-VBRNASBackupFLRSession cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Backups on Specific File Share

|  |  |
| --- | --- |
| This example shows how to start a file-level restore of backups that are located on a specific file share.  |  | | --- | | $backup = Get-VBRNASBackup  $server = Get-VBRNASServer  Start-VBRNASBackupFLRSession -NASBackup $backup -NASServer $server |  Perform the following steps:   1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Save the result to the $backup variable. 2. Run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. Save the result to the $server variable. 3. Run the Start-VBRNASBackupFLRSession cmdlet. Set the $backup variable as the NASBackup parameter value. Set the $server variable as the NASServer parameter value. |

Related Commands

* [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md)
* [Get-VBRNASBackup](get-vbrnasbackup.md)
* [Get-VBRNASServer](get-vbrnasserver.md)

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
