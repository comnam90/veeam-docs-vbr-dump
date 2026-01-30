---
title: "Set-VBRApplicationProcessingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrapplicationprocessingoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRApplicationProcessingOptions


Short Description

Modifies application-aware processing settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRApplicationProcessingOptions -Options <VBRApplicationProcessingOptions> [-Enable] [-GeneralTransactionLogAction <VBRGeneralTransactionLogAction> {ProcessLogsWithJob | PerformCopyOnly}] [-IgnoreErrors] [-SQLProcessingOptions <VBRSQLProcessingOptions>] [-SharePointCredentials <CCredentials>] [-OracleProcessingOptions <VBROracleProcessingOptions>] [-ScriptProcessingOptions <VBRScriptProcessingOptions>] [-MySQLProcessingOptions <VBRMySQLProcessingOptions>] [-PostgreSQLProcessingOptions <VBRPostgreSQLProcessingOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies application-aware processing settings for Veeam Agent backup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies application processing settings that you want to modify. | Accepts the VBRApplicationProcessingOptions object. To get this object, run the [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md) cmdlet. | True | Named | True (ByValue) |
| Enable | Enables application-aware processing. Veeam Backup & Replication will turn on the application-aware processing option for the selected protection group or a discovered computer.  Note: For Veeam Agent jobs that back up Linux computers, this parameter will also stop the backup process if any error occurs during application-aware processing. | SwitchParameter | False | Named | False |
| IgnoreErrors | Defines that Veeam Backup & Replication will ignore application processing errors. In case an error occurs during application-aware processing, Veeam Backup & Replication will continue to run the backup job. The resulting backup will be crash-consistent.  Note: This parameter works for Veeam Agent jobs that back up Linux computers only. You must use the Enable parameter to set up processing options with the IgnoreErrors option. | SwitchParameter | False | Named | False |
| GeneralTransactionLogAction | Specifies transaction logs action:   * ProcessLogsWithJob: use this option to allow Veeam Backup & Replication to process transaction logs. * PerformCopyOnly: use this option if you use another tool to maintain consistency of the database state. Veeam Agent for Microsoft Windows will create a copy-only backup.   Note:   * This parameter is required for Veeam Agent backup jobs that back up Windows computers. * This parameter does not work for Veeam Agent backup jobs that back up Linux computers. | VBRGeneralTransactionLogAction | False | Named | False |
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

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling Oracle and SQL Processing Settings for Veeam Agent Backup Job (Windows)

|  |  |
| --- | --- |
| This example shows how to disable Oracle and SQL processing settings for a Veeam Agent job that backs up Windows computers.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "Windows Group"  $processoptions = New-VBRApplicationProcessingOptions -BackupObject $group -OSPlatform Windows -Enable -GeneralTransactionLogAction ProcessLogsWithJob -SQLProcessingOptions $sql -SharePointCredentials $creds  Set-VBRApplicationProcessingOptions -Options $processoptions -Enable -GeneralTransactionLogAction PerformCopyOnly -SharePointCredentials $creds -ScriptProcessingOptions $script |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md) cmdlet. Set the $group variable as the BackupObject parameter value. Specify the OSPlatform, GeneralTransactionLogAction, SQLProcessingOptions and SharePointCredentials parameter values. Provide the Enable parameter. Save the result to the $processoptions variable. 3. Run the Set-VBRApplicationProcessingOptions cmdlet. Specify the following settings:  * Set the $processoptions variable as the Options parameter value. * Provide the Enable parameter. * Set the PerformCopyOnly option for the GeneralTransactionLogAction parameter. * Set the $creds variable as the SharePointCredentials parameter value. * Set the $script variable as the ScriptProcessingOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Application-Aware Processing Settings for Veeam Agent Backup Job (Linux)

|  |  |
| --- | --- |
| This example shows how to modify application-aware processing settings for a Veeam Agent backup job that backs up Linux computers. The job will run with the following options:   * Veeam Backup & Replication will run pre-freeze and post-thaw scripts to create a transactionally consistent backup. * Veeam Backup & Replication will use a user account that has SYSDBA rights on the database to connect to the Oracle database.  * In case an error occurs, Veeam Backup & Replication will stop the backup job.   |  | | --- | | $group = Get-VBRProtectionGroup -Name "Linux Group"  $processoptions = New-VBRApplicationProcessingOptions -BackupObject $group -OSPlatform Linux -IgnoreErrors -OracleProcessingOptions $oracle -ScriptProcessingOptions $script  Set-VBRApplicationProcessingOptions -Options $processoptions -OracleProcessingOptions $oracle -ScriptProcessingOptions $script -Enable |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md) cmdlet. Set the $group variable as the BackupObject parameter value. Specify the OSPlatform, OracleProcessingOptions and ScriptProcessingOptions parameter values. Provide the IgnoreErrors parameter. Save the result to the $processoptions variable. 3. Run the Set-VBRApplicationProcessingOptions cmdlet. Specify the following settings:  * Set the $processoptions variable as the Options parameter value. * Set the $oracle variable as the OracleProcessingOptions parameter value. * Set the $script variable as the ScriptProcessingOptions parameter value. * Provide the Enable parameter. |

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [New-VBRApplicationProcessingOptions](new-vbrapplicationprocessingoptions.md)


