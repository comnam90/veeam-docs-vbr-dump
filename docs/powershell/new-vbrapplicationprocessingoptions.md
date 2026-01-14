---
title: "New-VBRApplicationProcessingOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrapplicationprocessingoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRApplicationProcessingOptions

In this article

Short Description

Creates application-aware processing settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRApplicationProcessingOptions -BackupObject <Object> -OSPlatform <VBRAgentType> {Windows | Linux | Mac} [-Enable] [-GeneralTransactionLogAction <VBRGeneralTransactionLogAction> {ProcessLogsWithJob | PerformCopyOnly}] [-IgnoreErrors] [-SQLProcessingOptions <VBRSQLProcessingOptions>] [-SharePointCredentials <CCredentials>] [-OracleProcessingOptions <VBROracleProcessingOptions>] [-ScriptProcessingOptions <VBRScriptProcessingOptions>] [-MySQLProcessingOptions <VBRMySQLProcessingOptions>] [-PostgreSQLProcessingOptions <VBRPostgreSQLProcessingOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRApplicationProcessingOptions object. This object contains application-aware processing settings for Veeam Agent backup jobs.

For more information about job application-aware settings, see the [Application-Aware Processing](https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_vss_general.html?ver=13) section of the Veeam Agent Management Guide.

|  |
| --- |
| ![New-VBRApplicationProcessingOptions](images/icon_note.webp) Note: |
| You cannot set up application-aware processing for Veeam Agent jobs that back up workstations. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupObject | Specifies a protection group or a discovered computer, for which you want to set up application-aware processing settings. | Accepts the Object object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | True (ByValue) |
| OSPlatform | Specifies the OS of the protected computers:   * Windows: for Windows computers. * Linux: for Linux computers.  * Mac: for macOS computers. | VBRAgentType | True | Named | False |
| Enable | Enables application-aware processing. Veeam Backup & Replication will turn on application-aware processing option for the selected protection group or a discovered computer.  Note: For Veeam Agent jobs that back up Linux computers, this parameter will also stop the backup process if any error occurs during application-aware processing. | SwitchParameter | False | Named | False |
| IgnoreErrors | Defines that Veeam Backup & Replication will ignore application processing errors. In case an error occurs during application-aware processing, Veeam Backup & Replication will continue to run the backup job. The resulting backup will be crash-consistent.  Note: This parameter works for Veeam Agent jobs that back up Linux computers only. You must use the Enable parameter to set up processing options with the IgnoreErrors option. | SwitchParameter | False | Named | False |
| GeneralTransactionLogAction | Specifies transaction logs action:   * ProcessLogsWithJob: use this option to allow Veeam Backup & Replication to process transaction logs. * PerformCopyOnly: use this option if you have another tool to maintain consistency of the database state. Veeam Agent for Microsoft Windows will create a copy-only backup.   Note:   * This parameter is required for Veeam Agent jobs that back up Windows computers. * This parameter does not work for Veeam Agent jobs that back up Linux computers. | VBRGeneralTransactionLogAction | False | Named | False |
| SQLProcessingOptions | Specifies SQL processing settings. | Accepts the VBRSQLProcessingOptions object. To get this object, run the [New-VBRSQLProcessingOptions](new-vbrsqlprocessingoptions.md) cmdlet. | False | Named | False |
| SharePointCredentials | Specifies the credentials for the SharePoint user account that has enough permissions on the application. Veeam Agent for Microsoft Windows will use these credentials to connect to SharePoint and to back up the application. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| OracleProcessingOptions | Specifies Oracle processing settings. | Accepts the VBROracleProcessingOptions object. To get this object, run the [New-VBROracleProcessingOptions](new-vbroracleprocessingoptions.md) cmdlet. | False | Named | False |
| ScriptProcessingOptions | Specifies custom script settings. Veeam Agent will run pre-freeze and post-thaw scripts per these settings. | Accepts the VBRScriptProcessingOptions object. To get this object, run the [New-VBRScriptProcessingOptions](new-vbrscriptprocessingoptions.md) cmdlet. | False | Named | False |
| MySQLProcessingOptions | Specifies MySQL processing settings. Veeam Agent will apply these settings to a Veeam Agent backup job. | Accepts the VBRMySQLProcessingOptions object. To get this object, run the [New-VBRMySQLProcessingOptions](new-vbrmysqlprocessingoptions.md) cmdlet. | False | Named | False |
| PostgreSQLProcessingOptions | Specifies PostgreSQL processing settings. Veeam Agent will apply these settings to a Veeam Agent backup job. | Accepts the VBRPostgreSQLProcessingOptions object. To get this object, run the [New-VBRPostgreSQLProcessingOptions](new-vbrpostgresqlprocessingoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRApplicationProcessingOptions object that contains application-aware processing settings for Veeam Agent backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Specifying Application-Aware Processing Settings for Veeam Agent Backup Job (Linux)

|  |  |
| --- | --- |
| This example shows how to specify application-aware processing settings for a Veeam Agent job that backs up Linux computers. The job will run with the following options:   * Veeam Backup & Replication will run pre-freeze and post-thaw scripts to create a transactionally consistent backup. * Veeam Backup & Replication will use a user account that has SYSDBA rights on the database to connect to an Oracle database. * In case an error occurs during application-aware processing, Veeam Backup & Replication will proceed with the backup job and will create a crash-consistent backup.   |  | | --- | | $script = New-VBRScriptProcessingOptions -ProcessingAction RequireSuccess -ScriptPrefreezeCommand "C:\scripts\pre-scipt.bat" -ScriptPostthawCommand "C:\scripts\post-script.bat"  $creds = Get-Credential  $oracle = New-VBROracleProcessingOptions -Credentials $creds  $group = Get-VBRProtectionGroup -Name "LinuxGroup"  New-VBRApplicationProcessingOptions -BackupObject $group -OSPlatform Linux -Enable -IgnoreErrors -OracleProcessingOptions $oracle -ScriptProcessingOptions $script |  Perform the following steps:   1. Run the [New-VBRScriptProcessingOptions](new-vbrscriptprocessingoptions.md) cmdlet. Specify the ProcessingAction, ScriptPrefreezeCommand and ScriptPostthawCommand parameter values. Save the result to the $script variable. 2. Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet to specify credentials for the Oracle database. Save the result to the $creds variable. 3. Run the [New-VBROracleProcessingOptions](new-vbroracleprocessingoptions.md) cmdlet. Set the $creds variable as the Credentials parameter value. Save the result to the $oracle variable. 4. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 5. Run New-VBRApplicationProcessingOptions cmdlet. Specify the following settings:  * Set the $group variable as the BackupObject parameter value. * Set the Linux value as the OSPlatform parameter value. * Provide the Enable parameter. * Provide the IgnoreErrors parameter. * Set the $oracle variable as the OracleProcessingOptions parameter value. * Set the $script variable as the ScriptProcessingOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Specifying Application-Aware Processing Settings for Veeam Agent Backup Job (Windows)

|  |  |
| --- | --- |
| This example shows how to create application-aware processing settings for a Veeam Agent job that backs up Windows computers. The job will create a consistent backup and will run with the following options:   * Veeam Backup & Replication will apply SQL processing settings. * Veeam Backup & Replication will use SharePoint admin credentials.   |  | | --- | | $creds = Get-Credential  $group = Get-VBRProtectionGroup -Name "WindowsGroup"  $sql = New-VBRSQLProcessingOptions -TransactionAction BackupPeriodically -LogBackupPeriod 25 -LogRetainAction KeepOnlyLastDays -LogRetainPeriod 7  New-VBRApplicationProcessingOptions -BackupObject $group -OSPlatform Windows -Enable -GeneralTransactionLogAction ProcessLogsWithJob -SQLProcessingOptions $sql -SharePointCredentials $creds |  Perform the following steps:   1. Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet. Save the result to the $creds variable. 2. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 3. Run the [New-VBRSQLProcessingOptions](new-vbrsqlprocessingoptions.md) cmdlet. Specify the TransactionAction, LogBackupPeriod, LogRetainAction and LogRetainPeriod parameter values. Save the result to the $sql variable. 4. Run the New-VBRApplicationProcessingOptions cmdlet. Specify the following settings:  * Set the $group variable as the BackupObject parameter value. * Set the Windows option for the OSPlatform parameter. * Provide the Enable parameter. * Set the ProcessLogsWithJob option for the GeneralTransactionLogAction parameter. * Set the $sql variable as the SQLProcessingOptions parameter value. * Set the $creds variable as the SharePointCredentials parameter value. |

Related Commands

* [New-VBRScriptProcessingOptions](new-vbrscriptprocessingoptions.md)
* [New-VBROracleProcessingOptions](new-vbroracleprocessingoptions.md)
* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [New-VBRSQLProcessingOptions](new-vbrsqlprocessingoptions.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
