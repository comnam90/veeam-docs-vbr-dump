---
title: "New-VBRSQLProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsqlprocessingoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# New-VBRSQLProcessingOptions


Short Description

Defines settings for processing Microsoft SQL database transaction logs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSQLProcessingOptions -TransactionAction <VBRSQLTransactionLogAction> {Truncate | NotTruncate | BackupPeriodically} [-Credentials <CCredentials>] [-LogBackupPeriod <int>] [-LogRetainAction <VBRLogRetainAction> {WaitForBackupDeletion | KeepOnlyLastDays}] [-LogRetainPeriod <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRSQLProcessingOptions object. This object contains Microsoft SQL database transaction logs settings for Veeam Agent backup jobs. You can set up the following options:

* The way Veeam Backup & Replication will process transaction logs.
* Specify schedule settings for processing transaction logs.

For more information about custom scripts, see the [Transaction Log Settings: Microsoft SQL Server](https://helpcenter.veeam.com/docs/backup/agents/agent_job_vss_sql.html?ver=120) section of the Veeam Agent Management Guide.

|  |
| --- |
| ![New-VBRSQLProcessingOptions](images/icon_note.webp) Note: |
| This cmdlet works for the Veeam Agent jobs that back up Windows computers only. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| TransactionAction | Specifies transaction logs processing actions.   * Truncate: use this option to truncate transaction logs after successful backups. * NotTruncate: use this option to preserve transaction logs after the backup job completes. * BackupPeriodically: use this option to back up transaction logs periodically. | VBRSQLTransactionLogAction | True | Named | False |
| Credentials | Specifies the credentials that Veeam Agent for Microsoft Windows will use to connect to the Microsoft SQL Server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| LogBackupPeriod | For the BackupPeriodically action.  Specifies the number of minutes for transaction logs backups.  Default: 15. | Int | False | Named | False |
| LogRetainAction | For the BackupPeriodically action.  Specifies retention policy for transaction logs stored in the backup repository.   * WaitForBackupDeletion: use this option to keep transaction logs backups the same period as image-level backups.  * KeepOnlyLastDays: use this option to keep transaction log backups for a specific number of days. Use the LogRetainPeriod to specify the number of days. | VBRLogRetainAction | False | Named | False |
| LogRetainPeriod | For the BackupPeriodically action.  Specifies the number of days to keep the transaction logs.  Default: 15. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSQLProcessingOptions object that contains settings for processing Microsoft SQL database transaction logs.

Examples

Creating SQL Processing Settings for Veeam Agent Job (Windows)

This command creates SQL processing settings for a Veeam Agent job that backs up Windows computers. The job will run with the following options:

* Veeam Backup & Replication will backup SQL transaction logs every 25 minutes.
* Veeam Backup & Replication will keep the transaction logs for last 7 days.

|  |
| --- |
| New-VBRSQLProcessingOptions -TransactionAction BackupPeriodically -LogBackupPeriod 25 -LogRetainAction KeepOnlyLastDays -LogRetainPeriod 7 |


