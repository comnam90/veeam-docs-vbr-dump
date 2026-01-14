---
title: "Set-VBRSQLProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsqlprocessingoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSQLProcessingOptions

In this article

Short Description

Modifies settings for processing Microsoft SQL database transaction logs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSQLProcessingOptions -Options <VBRSQLProcessingOptions> [-Credentials <CCredentials>] [-TransactionAction <VBRSQLTransactionLogAction> {Truncate | NotTruncate | BackupPeriodically}] [-LogBackupPeriod <int>] [-LogRetainAction <VBRLogRetainAction> {WaitForBackupDeletion | KeepOnlyLastDays}] [-LogRetainPeriod <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies Microsoft SQL database transaction logs settings for Veeam Agent backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies SQL transaction logs processing settings that you want to modify. | Accepts the VBRSQLProcessingOptions object. To get this object, run the [New-VBRSQLProcessingOptions](new-vbrsqlprocessingoptions.md) cmdlet. | True | Named | True (ByValue) |
| Credentials | Specifies the credentials that Veeam Agent for Microsoft Windows will use to connect to the Microsoft SQL Server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| TransactionAction | Specifies transaction logs processing.   * Truncate: use this option to truncate transaction logs after the successful backup job. * NotTruncate: use this option to preserve transaction logs after the backup job completes. * BackupPeriodically: use this option to back up transaction logs periodically. | VBRSQLTransactionLogAction | False | Named | False |
| LogBackupPeriod | For the BackupPeriodically action.  Specifies the number of minutes for transaction logs backups. | Int | False | Named | False |
| LogRetainAction | For the BackupPeriodically action.  Specifies retention policy for transaction logs stored in the backup location.   * WaitForBackupDeletion: use this option to keep transaction logs backups the same period as image-level backups. * KeepOnlyLastDays: use this option to keep transaction log backups for a specific number of days. | VBRLogRetainAction | False | Named | False |
| LogRetainPeriod | For the BackupPeriodically action.  Specifies the number of days to keep the transaction logs. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSQLProcessingOptions object that contains settings for processing Microsoft SQL database transaction logs.

Examples

Modifying SQL Processing Settings for Veeam Agent Backup Job (Windows)

This example shows how to modify the existing SQL processing settings for a Veeam Agent job that backs up Windows computers. The job will run with the following options:

* Veeam Backup & Replication will back up the transaction logs every 30 minutes.
* Veeam Backup & Replication will keep the transaction logs backups until the image-level backup is deleted.

|  |
| --- |
| $sql = New-VBRSQLProcessingOptions -TransactionAction BackupPeriodically -LogBackupPeriod 25 -LogRetainAction KeepOnlyLastDays -LogRetainPeriod 7  Set-VBRSQLProcessingOptions -Options $sql -TransactionAction BackupPeriodically -LogBackupPeriod 30 -LogRetainAction WaitForBackupDeletion |

Perform the following steps:

1. Run the [New-VBRSQLProcessingOptions](new-vbrsqlprocessingoptions.md) cmdlet. Specify the TransactionAction, LogBackupPeriod, LogRetainAction and LogRetainPeriod parameter values. Save the result to the $sql variable.
2. Run the Set-VBRSQLProcessingOptions cmdlet. Specify the following settings:

* Set the $sql variable as the Options parameter value.
* Set the BackupPeriodically option for the TransactionAction parameter.
* Specify the LogBackupPeriod parameter value.
* Set the WaitForBackupDeletion option for the LogRetainAction parameter.

Related Commands

[New-VBRSQLProcessingOptions](new-vbrsqlprocessingoptions.md)

Page updated 5/6/2024

Page content applies to build 13.0.1.1071
