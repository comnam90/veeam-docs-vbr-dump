---
title: "Upgrade-VBRBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/upgrade-vbrbackup.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Upgrade-VBRBackup

In this article

Short Description

Upgrades the backup chain format of backups from per-machine (split machine) to true per-machine.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Upgrade all per-machine (split machine) backups stored on a repository to the true per-machine format.

|  |
| --- |
| Upgrade-VBRBackup [-BackupRepository <CBackupRepository>] [-Force] [-RunAsync]  [<CommonParameters>] |

* Upgrade per-machine (split machine) backups of a backup job to the true per-machine format.

|  |
| --- |
| Upgrade-VBRBackup [-Backup <CBackup[]>] [-Force] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet upgrades the backup chain format of backups from per-machine (split machine) to true per-machine. Note that the cmdlet does not upgrade single storage backups.

If you want to change the backup chain format for other backups, you need to use the [Detach-VBRBackup](detach-vbrbackup.md) cmdlet to detach backups from the job. Ensure that the job is targeted to the repository that creates backups of the required backup chain format. Then launch the job. For more information on backup chain formats and how to change them, see the [Changing Backup Chain Formats](https://helpcenter.veeam.com/docs/vbr/userguide/backup_change_type.html?ver=13) section in Veeam Backup & Replication User Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupRepository | Specifies the repository whose backups you want to upgrade. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByValue) |
| Backup | Specifies an array of backups that you want to upgrade.  Note: Backups must be stored on one repository. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | False | Named | True (ByValue) |
| Force | Defines that the cmdlet will upgrade backups without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBaseSession object that defines settings of the upgrade session.

Examples

Upgrading Backups in Specific Repository

This example shows how to upgrade backups located in specific repository.

|  |
| --- |
| $repository = Get-VBRBackupRepository -Name "Backup Repository 1"  Upgrade-VBRBackup -BackupRepository $repository |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the Upgrade-VBRBackup cmdlet. Set the $repository variable as the BackupRepository parameter value.

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
