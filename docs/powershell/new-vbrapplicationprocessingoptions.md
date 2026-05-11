---
title: "New-VBRApplicationProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrapplicationprocessingoptions.html"
last_updated: "5/7/2026"
product_version: "13.0.1.2067"
---

# New-VBRApplicationProcessingOptions


Short Description

Creates application-aware processing settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRApplicationProcessingOptions -BackupObject <Object> -OSPlatform <VBRAgentType> {Windows | Linux | Mac} [-Enable] [-GeneralTransactionLogAction <VBRGeneralTransactionLogAction> {ProcessLogsWithJob | PerformCopyOnly}] [-IgnoreErrors] [-SQLProcessingOptions <VBRSQLProcessingOptions>] [-SharePointCredentials <CCredentials>] [-OracleProcessingOptions <VBROracleProcessingOptions>] [-ScriptProcessingOptions <VBRScriptProcessingOptions>] [-MySQLProcessingOptions <VBRMySQLProcessingOptions>] [-PostgreSQLProcessingOptions <VBRPostgreSQLProcessingOptions>] [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRApplicationProcessingOptions object. This object contains application-aware processing settings that you can apply to Veeam Agent backup jobs.

For more information about job application-aware settings, see the [Application-Aware Processing](https://helpcenter.veeam.com/docs/vbr/userguide/agent_job_vss_general.html?ver=13) section of the Veeam Backup & Replication User Guide.

|  |
| --- |
| ![New-VBRApplicationProcessingOptions](images/icon_note.webp) Note: |
| You cannot set up application-aware processing for Veeam Agent jobs that back up workstations. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| BackupObject | Specifies a protection group or an individual computer, for which you want to set up application-aware processing settings. | Accepts the Object object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) or [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue) |
| OSPlatform | Specifies the OS of the protected computers:   * Windows: for Windows computers. * Linux: for Linux computers.  * Mac: for macOS computers. Note: Application-aware processing for macOS computers is not supported in current version of Veeam PowerShell. | VBRAgentType | True | Named | False |
| Enable | Enables application-aware processing. Veeam Backup & Replication will turn on application-aware processing option for the selected protection group or a discovered computer.  Note: For Veeam Agent jobs that back up Linux computers, this parameter will also stop the backup process if any error occurs during application-aware processing. | SwitchParameter | False | Named | False |
| IgnoreErrors | Defines that Veeam Backup & Replication will ignore application processing errors. In case an error occurs during application-aware processing, Veeam Backup & Replication will continue to run the backup job. The resulting backup will be crash-consistent.  Note: This parameter works for Veeam Agent jobs that back up Linux computers only. You must use the Enable parameter to set up processing options with the IgnoreErrors option. | SwitchParameter | False | Named | False |
| GeneralTransactionLogAction | Specifies transaction logs action:   * ProcessLogsWithJob: use this option to allow Veeam Backup & Replication to process transaction logs.  Note: For Veeam Agent jobs that back up Windows computers, this option enables SQL and Oracle logs processing options. * PerformCopyOnly: use this option if you have another tool to maintain consistency of the database state. Veeam Agent for Microsoft Windows will create a copy-only backup.   Note:   * This parameter is required for Veeam Agent jobs that back up Windows computers. * This parameter does not work for Veeam Agent jobs that back up Linux computers. | VBRGeneralTransactionLogAction | False | Named | False |
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
| This example shows how to specify application-aware processing settings for a Veeam Agent job that backs up Linux computers. With these settings applied, the job will run with the following options:   * Veeam Backup & Replication will run pre-freeze and post-thaw scripts to create a transactionally consistent backup. * Veeam Backup & Replication will use a user account that has SYSDBA rights on the database to connect to an Oracle database. * Veeam Backup & Replication will apply the application-aware processing settings to a Veeam Agent backup job but will stop the backup job in case an error occurs during application-aware processing.   |  | | --- | | $script = New-VBRScriptProcessingOptions -ProcessingAction RequireSuccess -ScriptPrefreezeCommand "/scripts/pre.sh" -ScriptPostthawCommand "/scripts/post.sh"  $creds = Get-VBRCredentials -Name "UserName"  $oracle = New-VBROracleProcessingOptions -Credentials $creds  $group = Get-VBRProtectionGroup -Name "LinuxGroup"  $job = Get-VBRComputerBackupJob -Name "LinuxBackupJob"  $newoption = New-VBRApplicationProcessingOptions -Enable -OSPlatform Linux -BackupObject $group -OracleProcessingOptions $oracle -ScriptProcessingOptions $script  Set-VBRComputerBackupJob -Job $job -ApplicationProcessingOptions $newoption -EnableApplicationProcessing |  Perform the following steps:   1. Run the [New-VBRScriptProcessingOptions](new-vbrscriptprocessingoptions.md) cmdlet. Specify the ProcessingAction, ScriptPrefreezeCommand and ScriptPostthawCommand parameter values. Save the result to the $script variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet to get credentials for the Oracle database. Specify the Name parameter value. Save the result to the $creds variable. 3. Run the [New-VBROracleProcessingOptions](new-vbroracleprocessingoptions.md) cmdlet. Set the $creds variable as the Credentials parameter value. Save the result to the $oracle variable. 4. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 5. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 6. Run the New-VBRApplicationProcessingOptions cmdlet. Specify the following settings:  * Provide the Enable parameter. * Set the Linux value as the OSPlatform parameter value. * Set the $group variable as the BackupObject parameter value. * Set the $oracle variable as the OracleProcessingOptions parameter value. * Set the $script variable as the ScriptProcessingOptions parameter value. * Save the result to the $newoption variable.  1. Run the [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md) cmdlet. Set the $job variable as the Job parameter value. Set the $newoption variable as the ApplicationProcessingOptions parameter value. Provide the EnableApplicationProcessing parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Specifying Application-Aware Processing Settings for Veeam Agent Backup Job (Windows)

|  |  |
| --- | --- |
| This example shows how to create application-aware processing settings for a Veeam Agent job that backs up Windows computers. The job will create a consistent backup and will run with the following options:   * Veeam Backup & Replication will run pre-freeze and post-thaw scripts to create a transactionally consistent backup. * Veeam Backup & Replication will apply SQL processing settings to back up SQL transaction logs every 15 minutes.   |  | | --- | | $script = New-VBRScriptProcessingOptions -ProcessingAction RequireSuccess -ScriptPrefreezeCommand "C:\scripts\pre-script.bat" -ScriptPostthawCommand "C:\scripts\post-script.bat"  $creds = Get-VBRCredentials -Name "UserName"  $sql = New-VBRSQLProcessingOptions -TransactionAction BackupPeriodically -LogBackupPeriod 15 -Credentials $creds  $group = Get-VBRProtectionGroup -Name "WindowsGroup"  $job = Get-VBRComputerBackupJob -Name "WindowsBackupJob"  $newoption = New-VBRApplicationProcessingOptions -Enable -OSPlatform Windows -BackupObject $group -GeneralTransactionLogAction ProcessLogsWithJob -SQLProcessingOptions $sql -ScriptProcessingOptions $script  Set-VBRComputerBackupJob -Job $job -ApplicationProcessingOptions $newoption -EnableApplicationProcessing |  Perform the following steps:   1. Run the [New-VBRScriptProcessingOptions](new-vbrscriptprocessingoptions.md) cmdlet. Specify the ProcessingAction, ScriptPrefreezeCommand and ScriptPostthawCommand parameter values. Save the result to the $script variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet to get credentials for SQL processing. Specify the Name parameter value. Save the result to the $creds variable. 3. Run the [New-VBRSQLProcessingOptions](new-vbrsqlprocessingoptions.md) cmdlet. Specify the TransactionAction and LogBackupPeriod parameter values. Set the $creds variable as the Credentials parameter value. Save the result to the $sql variable. 4. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 5. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 6. Run the New-VBRApplicationProcessingOptions cmdlet. Specify the following settings:  * Provide the Enable parameter. * Set the Windows option for the OSPlatform parameter. * Set the $group variable as the BackupObject parameter value. * Set the ProcessLogsWithJob option for the GeneralTransactionLogAction parameter. * Set the $sql variable as the SQLProcessingOptions parameter value. * Set the $script variable as the ScriptProcessingOptions parameter value. * Save the result to the $newoption variable.  1. Run the [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md) cmdlet. Set the $job variable as the Job parameter value. Set the $newoption variable as the ApplicationProcessingOptions parameter value. Provide the EnableApplicationProcessing parameter. |

Related Commands

* [New-VBRScriptProcessingOptions](new-vbrscriptprocessingoptions.md)
* [New-VBROracleProcessingOptions](new-vbroracleprocessingoptions.md)
* [New-VBRSQLProcessingOptions](new-vbrsqlprocessingoptions.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)
* [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)
* [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md)


