---
title: "Copy-VBRBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrbackup.html"
last_updated: "10/13/2025"
product_version: "13.0.1.1071"
---

# Copy-VBRBackup


Short Description

Copies backups to a repository or local or shared folder.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Copy backups to a local or shared folder.

|  |
| --- |
| Copy-VBRBackup -Backup <CBackup> [-Name <String[]>] [-Path <String>] [-ShareCredentials <CCredentials>] [-AutoDelete <VBRMoveCopyRetention>] [-RetentionNumber <Int32>] [-RetentionPeriodType <VBRRetentionPeriodType>] [-RunAsync] [-Force] [-Confirm]  [<CommonParameters>] |

* Copy backups to a repository.

|  |
| --- |
| Copy-VBRBackup -Backup <CBackup> [-Name <String[]>] [-Repository <CBackupRepository>] [-AutoDelete <VBRMoveCopyRetention>] [-RetentionNumber <Int32>] [-RetentionPeriodType <VBRRetentionPeriodType>] [-RunAsync] [-Force] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet copies the whole backup chains to a repository or local or shared folder.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the backups that will be copied. | Accepts the CBackup object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Name | Specifies an array of names of the workloads that you want to move.  Note: This parameter applies only if backups are per-machine with metadata for each workload. | String[] | False | Named | True (ByPropertyName, ByValue) |
| Path | Specifies a path to the local or shared folder to which you want to copy backups. | String | False | Named | True (ByPropertyName, ByValue) |
| ShareCredentials | Specifies the credentials that will be used to access the shared folder. | Accepts the CCredentials object. To get this object, run the Get-VBRCredentials cmdlet. | False | Named | True (ByPropertyName, ByValue) |
| Repository | Specifies the repository to which you want to copy backups. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByPropertyName, ByValue) |
| AutoDelete | Specifies the time interval after which Veeam Backup & Replication will delete copied backups.  The parameter accepts the following values:   * In1Month * In3Months * In6Months * In1Year * In2Years * In3Years * In5Years * In7Years | AutoDelete | False | Named | False |
| RetentionPeriodType | Specifies the type of the retention policy. You can set the following types:   * Days: use this option if you want Veeam Backup & Replication to apply retention policy daily. * Months: use this option if you want Veeam Backup & Replication to apply retention policy monthly. * Years: use this option if you want Veeam Backup & Replication to apply retention policy yearly.   Use the RetentionNumber to specify the number of days, months or years.  Note: Use this parameter if the AutoDelete parameter is not specified. | VBRRetentionPeriodType | False | Named | False |
| RetentionNumber | For the RetentionPeriodType option.  Specifies the period of time to keep the copied data. After this period finishes, Veeam Backup & Replication will remove data. | Int32 | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will copy backups without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRCopyBackupSession](vbrcopybackupsession.md) object that contains settings of the copy session.

Examples

Copying Backups

This example shows how to copy backups to a repository.

|  |
| --- |
| $backup = Get-VBRBackup  $repository = Get-VBRBackupRepository  Copy-VBRBackup -Backup $backup -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Save the result to the $backup variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $repository variable.
3. Run the Copy-VBRBackup cmdlet. Set the $backup variable as the Backup parameter value. Set the $repository variable as the Repository parameter value.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


