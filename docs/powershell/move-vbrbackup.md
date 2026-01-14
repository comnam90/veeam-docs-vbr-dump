---
title: "Move-VBRBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/move-vbrbackup.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Move-VBRBackup

In this article

Short Description

Moves all backups of a job to another repository or specific workloads and their backups to another job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Move backups of a job (backup, backup copy, veeamZIP, and other) to another repository.

|  |
| --- |
| Move-VBRBackup -Backup <CBackup> -Repository <CBackupRepository> [-RunAsync] [-Force] [-Confirm]  [<CommonParameters>] |

* Move workloads and their backups to another job (backup, backup copy, veeamZIP, and other).

|  |
| --- |
| Move-VBRBackup -Backup <CBackup> -Job <CBackupJob> -Name <String[]> [-RunAsync] [-Force] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet moves backups to another repository or to another job. For more information on the move operation and its considerations, see the [Moving Backups](https://helpcenter.veeam.com/docs/vbr/userguide/backup_moving.html?ver=13) section in the Veeam Backup & Replication User Guide.

When you move backups to another repository, the cmdlet reconfigures the job to target to the new location. When you move workload and their backups to another job, backups are moved to the repository which the specified job is targeted to.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies backups that will be moved. | Accepts the CBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Repository | Specifies the repository to which backups will be moved. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Name | Specifies an array of names of the workloads that you want to move.  Note: This parameter applies only if backups are true per-machine (with metadata for each workload). This parameter is required if the Job parameter is set. | String[] | True | Named | True (ByPropertyName, ByValue) |
| Job | Specifies the job to which you want to move workloads and their backups.  Note: This parameter applies only if backups are true per-machine (with metadata for each workload). This parameter is required if the Name parameter is set. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will move backups without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRMoveBackupSession](vbrmovebackupsession.md) object that contains settings of the move session.

Examples

Moving Backups

This example shows how to move all backups to another repository.

|  |
| --- |
| $backup = Get-VBRBackup  $repository = Get-VBRBackupRepository  Move-VBRBackup -Backup $backup -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Save the result to the $backup variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $repository variable.
3. Run the Move-VBRBackup cmdlet. Set the $backup variable as the Backup parameter value. Set the $repository variable as the Repository parameter value.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
