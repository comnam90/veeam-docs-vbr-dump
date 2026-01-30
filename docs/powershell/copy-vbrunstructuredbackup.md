---
title: "Copy-VBRUnstructuredBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrunstructuredbackup.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Copy-VBRUnstructuredBackup


Short Description

Copies backups created by file backup jobs and object storage backup jobs to another location.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Copy-VBRUnstructuredBackup -Backup <VBRUnstructuredBackup[]> -BackupRepository <CBackupRepository> [-ArchiveRepository <IRepository>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet copies backups created by file backup jobs and object storage backup jobs to one of the following locations:

* Another repository
* Local folder
* Shared folder
* Archive repository

Veeam Backup & Replication copies the whole backup chain. When Veeam Backup & Replication performs the copy operation, it disables the job, copies files to the target location and then enables the job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an array of backups created by file backup jobs and object storage backup jobs. The cmdlet will copy these backups to a specified backup repository. | Accepts the VBRUnstructuredBackup[] object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | True | Named | True (ByValue) |
| BackupRepository | Specifies the backup repository. The cmdlet will copy the backups created by file backup jobs and object storage backup jobs to this backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| ArchiveRepository | Specifies the archive repository. The cmdlet will copy the backups created by file backup jobs and object storage backup jobs to this long-term archive repository. | Accepts the CBackupRepository object. To get this object, run the following cmdlets:   * [Get-VBRBackupRepository](get-vbrbackuprepository.md): use this cmdlet to get backup repositories. * [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md): use this cmdlet to get object storage repositories. | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Copying Object Storage Backups to Another Repository

This example shows how to copy object storage backups to another repository.

|  |
| --- |
| $backup = Get-VBRUnstructuredBackup  $repository = Get-VBRBackupRepository  Copy-VBRUnstructuredBackup -Backup $backup[3] -BackupRepository $repository |

Perform the following steps:

1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Save the result to the $backup variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $repository variable.
3. Run the Copy-VBRUnstructuredBackup cmdlet. Set the $backup[3] variable as the Backup parameter value. Set the $repository variable as the BackupRepository parameter value.

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


