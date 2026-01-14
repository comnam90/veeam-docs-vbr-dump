---
title: "Set-VBROracleProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbroracleprocessingoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBROracleProcessingOptions

In this article

Short Description

Modifies settings for processing Oracle database archived logs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBROracleProcessingOptions -Options <VBROracleProcessingOptions> [-Credentials <CCredentials>] [-ArchivedLogAction <VBROracleArchivedLogAction> {NotDelete | DeleteByTime | DeleteBySize}] [-ArchiveLogDeletionPeriod <int>] [-ArchiveLogDeletionSize <int>] [-EnableArchiveLogBackup] [-ArchiveLogBackupPeriod <int>] [-ArchiveLogRetainAction <VBRLogRetainAction> {WaitForBackupDeletion | KeepOnlyLastDays}] [-ArchiveLogRetainPeriod <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the Oracle database processing settings for Veeam Agent backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies Oracle processing options that you want to modify. | Accepts the VBROracleProcessingOptions object. To get this object, run the [New-VBROracleProcessingOptions](new-vbroracleprocessingoptions.md) cmdlet. | True | Named | True (ByValue) |
| Credentials | Specifies the credentials of the account with SYSDBA privileges. Veeam Backup & Replication will use these credentials to connect to the Oracle database.  Note: this parameter is required for the backup policy that Veeam Agent job applies to Linux computers. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| ArchivedLogAction | Specifies action for Oracle archived logs.   * NotDelete: use this option to keep archived logs. * DeleteByTime: use this option if you want to delete archived logs that are older than <N> hours. * DeleteBySize: use this option if you want to delete archived logs that are larger than <N> GB. | VBROracleArchivedLogAction | False | Named | False |
| ArchiveLogDeletionPeriod | For the DeleteByTime action.  Specifies the number of hours for keeping archived logs. | Int | False | Named | False |
| ArchiveLogDeletionSize | For the DeleteBySize action.  Specifies the size limits in GB for the logs to keep them on the server. | Int | False | Named | False |
| EnableArchiveLogBackup | Enables the option to backup Oracle archived logs.  Note: This parameter does not work for backup policies that Veeam Agent job applies to Linux computers. | SwitchParameter | False | Named | False |
| ArchiveLogBackupPeriod | For the EnableArchiveLogBackup parameter.  Specifies how often Veeam Backup & Replication will back up archived logs.  Default: every 15 minutes. | Int | False | Named | False |
| ArchiveLogRetainAction | For the EnableArchiveLogBackup parameter.  Specifies retention policy for the archived logs backups. Veeam Backup & Replication will apply the policy for archived logs stored in the backup repository.   * WaitForBackupDeletion: use this option to keep archived log backups the same period as the image-level backups. * KeepOnlyLastDays: use this option to keep archived log backups for a specific number of days. | VBRLogRetainAction | False | Named | False |
| ArchiveLogRetainPeriod | For the EnableArchiveLogBackup parameter.  Specifies the number of days to keep backups of the archived logs. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBROracleProcessingOptions object that contains settings for processing Oracle database archived logs.

Examples

Modifying Oracle Processing Settings for Veeam Agent Backup Job (Windows)

This example shows how to modify Oracle processing settings for a Veeam Agent job that backs up Windows computers. The job will run with the following options:

* Veeam Backup & Replication will trigger the truncation of the logs which are older than 17 hours.
* Veeam Backup & Replication will back up the archived logs every 25 minutes.
* Veeam Backup & Replication will keep the backups of the archived logs the same period as the image-level backups.

|  |
| --- |
| $oracle = New-VBROracleProcessingOptions -ArchivedLogAction DeleteBySize -ArchiveLogDeletionSize 20  Set-VBROracleProcessingOptions -Options $oracle -ArchivedLogAction DeleteByTime -ArchiveLogDeletionPeriod 17 -ArchiveLogBackupPeriod 25 -ArchiveLogRetainAction WaitForBackupDeletion -EnableArchiveLogBackup |

Perform the following steps:

1. Run the [New-VBROracleProcessingOptions](new-vbroracleprocessingoptions.md) cmdlet. Specify the ArchivedLogAction and ArchiveLogDeletionSize parameter values. Save the result to the $oracle variable.
2. Run the Set-VBROracleProcessingOptions cmdlet. Specify the following settings:

* Set the $oracle variable as the Options parameter value.
* Set the DeleteByTime option for the ArchivedLogAction parameter.
* Specify the ArchiveLogDeletionPeriod parameter value.
* Specify the ArchiveLogBackupPeriod parameter value.
* Set the WaitForBackupDeletion option for the ArchiveLogRetainAction parameter.
* Provide the EnableArchiveLogBackup parameter.

Related Commands

[New-VBROracleProcessingOptions](new-vbroracleprocessingoptions.md)

Page updated 5/6/2024

Page content applies to build 13.0.1.1071
