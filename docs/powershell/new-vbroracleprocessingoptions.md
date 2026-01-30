---
title: "New-VBROracleProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbroracleprocessingoptions.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# New-VBROracleProcessingOptions


Short Description

Creates settings for processing Oracle database archived logs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Specify Oracle processing settings for the backup policy that Veeam Agent job applies to Linux computers.

|  |
| --- |
| New-VBROracleProcessingOptions -Credentials <CCredentials>  [<CommonParameters>] |

* Specify Oracle processing settings for the other types of Veeam Agent backup jobs.

|  |
| --- |
| New-VBROracleProcessingOptions -ArchivedLogAction <VBROracleArchivedLogAction> {NotDelete | DeleteByTime | DeleteBySize} [-Credentials <CCredentials>] [-ArchiveLogDeletionPeriod <int>] [-ArchiveLogDeletionSize <int>] [-EnableArchiveLogBackup] [-ArchiveLogBackupPeriod <int>] [-ArchiveLogRetainAction <VBRLogRetainAction> {WaitForBackupDeletion | KeepOnlyLastDays}] [-ArchiveLogRetainPeriod <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a VBROracleProcessingOptions object. This object contains settings for processing Oracle archived logs in Veeam Agent backup jobs. You can set Veeam Backup & Replication to apply the following settings:

* Preserve the archived logs
* Delete them after a certain retention period
* Delete the archived logs that are larger than the specified GB

|  |
| --- |
| ![New-VBROracleProcessingOptions](images/icon_note.webp) Note: |
| Processing of the Oracle database logs is not available for failover clusters. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ArchivedLogAction | Specifies action for Oracle archived logs.   * NotDelete: use this option to keep archived logs. * DeleteByTime: use this option if you want to delete archived logs that are older than <N> hours. * DeleteBySize: use this option if you want to delete archived logs that are larger than <N> GB. | VBROracleArchivedLogAction | True | Named | False |
| Credentials | Specifies the credentials of the account with SYSDBA privileges. Veeam Backup & Replication will use these credentials to connect to the Oracle database.  Note: this parameter is required for the backup policy that Veeam Agent job applies to Linux computers. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| ArchiveLogDeletionPeriod | For the DeleteByTime action.  Specifies the number of hours for keeping archived logs.  Default: 24. | Int | False | Named | False |
| ArchiveLogDeletionSize | For the DeleteBySize action.  Specifies the size limits in GB for the logs to keep them on the server.  Default: 10. | Int | False | Named | False |
| EnableArchiveLogBackup | Enables the option to backup Oracle archived logs.  Note: This parameter does not work for backup policies that Veeam Agent job applies to Linux computers. | SwitchParameter | False | Named | False |
| ArchiveLogBackupPeriod | For the EnableArchiveLogBackup parameter.  Specifies how often Veeam Backup & Replication will back up archived logs.  Default: every 15 minutes. | Int | False | Named | False |
| ArchiveLogRetainAction | For the EnableArchiveLogBackup parameter.  Specifies retention policy for the archived logs backups. Veeam Backup & Replication will apply the policy for archived logs stored in the backup repository.   * WaitForBackupDeletion: use this option to keep archived log backups the same period as the image-level backups. * KeepOnlyLastDays: use this option to keep archived log backups for a specific number of days. | VBRLogRetainAction | False | Named | False |
| ArchiveLogRetainPeriod | For the EnableArchiveLogBackup parameter.  Specifies the number of days to keep backups of the archived logs.  Default: 15. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBROracleProcessingOptions object that contains settings for processing Oracle database archived logs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Oracle Processing Settings for Veeam Agent Backup Job (Linux)

|  |  |
| --- | --- |
| This example shows how to create Oracle processing settings for a Veeam Agent job that backs up Linux computers.  |  | | --- | | $creds = Get-VBRCredentials  New-VBROracleProcessingOptions -Credentials $creds |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $creds variable. 2. Run the New-VBROracleProcessingOptions cmdlet. Set the $creds variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Oracle Processing Settings for Veeam Agent Backup Job (Windows)

|  |  |
| --- | --- |
| This command creates Oracle processing settings for a Veeam Agent job that backs up Windows computers. The job will run with the following options:   * Veeam Backup & Replication will trigger the truncation of the logs if they exceed 17 GB. * Veeam Backup & Replication will back up the archived logs every 25 minutes.   |  | | --- | | New-VBROracleProcessingOptions -ArchivedLogAction DeleteBySize -ArchiveLogDeletionSize 17 -ArchiveLogBackupPeriod 25 -ArchiveLogRetainAction -EnableArchiveLogBackup | |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)


