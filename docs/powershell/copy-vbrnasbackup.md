---
title: "Copy-VBRNASBackup (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrnasbackup.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Copy-VBRNASBackup (obsolete)


Short Description

Copies file share backups to another repository or local or shared folder.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Copy-VBRUnstructuredBackup](copy-vbrunstructuredbackup.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Copy-VBRNASBackup -Backup <VBRNASBackup[]> -BackupRepository <CBackupRepository> [-ArchiveRepository <IRepository>] [-RunAsync] [<CommonParameters>] |

Detailed Description

This cmdlet copies file share backups to another repository or local or shared folder. Veeam Backup & Replication copies the whole backup chain. When Veeam Backup & Replication performs the copy operation, it disables the job, copies files to the target location and then enables the job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an array of file share backups. The cmdlet will copy these backups to a specified backup repository. | Accepts the VBRNASBackup[] object. To get this object, run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. | True | Named | True (ByValue) |
| BackupRepository | Specifies the backup repository. The cmdlet will copy the specified file share backups to this backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| ArchiveRepository | Specifies the archive repository. The cmdlet will copy the archive associated with the file share backup being copied to this long-term archive repository. | Accepts the CBackupRepository object. To get this object, run the following cmdlets:   * [Get-VBRBackupRepository](get-vbrbackuprepository.md): use this cmdlet to get backup repositories. * [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md): use this cmdlet to get object storage repositories. | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Copying File Share Backups to Another Repository

This example shows how to copy file share backups to another repository.

|  |
| --- |
| $backup = Get-VBRNASBackup  $repository = Get-VBRBackupRepository  Copy-VBRNASBackup -Backup $backup[3] -BackupRepository $repository |

Perform the following steps:

1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Save the result to the $backup variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $repository variable.
3. Run the Copy-VBRNASBackup cmdlet. Set the $backup[3] variable as the Backup parameter value. Set the $repository variable as the BackupRepository parameter value.

Related Commands

* [Get-VBRNASBackup](get-vbrnasbackup.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


