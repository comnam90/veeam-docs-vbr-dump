---
title: "Add-VBRApplicationBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrapplicationbackupjob.html"
last_updated: "1/28/2026"
product_version: "13.0.1.1071"
---

# Add-VBRApplicationBackupJob


Short Description

Creates application backup policies.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRApplicationBackupJob -BackupObject <Object[]> -BackupRepository <CBackupRepository> [-Name <string>] [-Description <string>] [-BackupOptions <VBRApplicationBackupOptions>] [-RetentionPolicy <int>] [-EnableSchedule] [-ScheduleOptions <VBRApplicationScheduleOptions>] [-NotificationOptions <VBRNotificationOptions>] [-DatabaseProcessingOptions <VBRDatabaseProcessingOptions[]>] [-SAPOnOracleMode {RMAN | BACKINT}] [-SAPOnOracleStorageOptions <VBRSAPOnOracleStorageOptions>] [-SAPOnOracleOptions <VBRSAPOnOracleOptions>] [-OracleRMANStorageOptions <VBROracleRMANStorageOptions>] [-OracleRMANOptions <VBROracleRMANOptions>] [-SAPHANAOptions <VBRSAPHANAOptions>] [-SAPHANACredentialsOptions <VBRSAPHANACredentialsOptions[]>] [-SAPHANAStorageOptions <VBRSAPHANAStorageOptions>] [-MSSQLOptions <VBRMSSQLOptions>] [-MSSQLCredentialsOptions <VBRMSSQLCredentialsOptions[]>] [-MSSQLStorageOptions <VBRMSSQLStorageOptions>] [<CommonParameters>] |

Detailed Description

This cmdlet creates application backup policies.

To create application backup policies, you must specify a container object with discovered application entities (for example, individual computers, databases, protection groups, and so on) that you plan to back up and the target location for storing backups.

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet to get the protection group.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get the repository.
3. Run the Add-VBRApplicationBackupJob cmdlet to create application backup policy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupObject | Specifies an array of discovered application entities: individual computers, databases, protection groups, and so on. The cmdlet will add these entities to the application backup policy. | Accepts the Object[] object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | False |
| BackupRepository | Specifies the target backup location for the application backup policy. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| Name | Specifies the name that you want to assign to the application backup policy. | String | False | Named | False |
| Description | Specifies the description of the application backup policy. | String | False | Named | False |
| BackupOptions | Specifies backup settings for the application backup policy. | Accepts the VBRApplicationBackupOptions object. To define this object, run the [New-VBRApplicationBackupOptions](new-vbrapplicationbackupoptions.md) cmdlet. | False | Named | False |
| RetentionPolicy | Specifies the retention policy for backups created by Veeam Plug-In.  Note: The retention policy specifies the number of restore points or a number of days. | Int32 | False | Named | False |
| EnableSchedule | Enables the option to schedule the application backup policy to run on a regular basis. | SwitchParameter | False | Named | False |
| ScheduleOptions | Specifies the settings for the application backup policy schedule. | Accepts the VBRApplicationScheduleOptions object. To get this object, run the one of the following cmdlets:   * [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) * [New-VBRApplicationScheduleOptions](new-vbrapplicationscheduleoptions.md) | False | Named | False |
| NotificationOptions | Specifies notification settings for the application backup policy. | Accepts the VBRNotificationOptions object. To define this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| DatabaseProcessingOptions | Specifies database processing settings for the application backup policy. | Accepts the VBRDatabaseProcessingOptions[] object. To define this object, run the [New-VBRDatabaseProcessingOptions](new-vbrdatabaseprocessingoptions.md) cmdlet. | False | Named | False |
| SAPOnOracleMode | Note: This option works only for Veeam Plug-In for SAP on Oracle.  Specifies the backup mode for Veeam Plug-In for SAP on Oracle:   * RMAN: for BR\*Tools with RMAN (rman\_util mode). * BACKINT: for BR\*Tools with BACKINT (util\_file\_online mode). | VBRSAPOnOracleMode | False | Named | False |
| SAPOnOracleStorageOptions | Note: This option works only for Veeam Plug-In for SAP on Oracle.  Specifies the storage settings for Veeam Plug-In for SAP on Oracle. | Accepts the VBRDatabaseProcessingOptions object. To define this object, run the [New-VBRSAPOnOracleStorageOptions](new-vbrsaponoraclestorageoptions.md) cmdlet. | False | Named | False |
| SAPOnOracleOptions | Note: This option works only for Veeam Plug-In for SAP on Oracle.  Specifies the backup settings for Veeam Plug-In for SAP on Oracle. | Accepts the VBRSAPOnOracleOptions object. To define this object, run the [New-VBRSAPOnOracleOptions](new-vbrsaponoracleoptions.md) cmdlet. | False | Named | False |
| OracleRMANStorageOptions | Note: This option works only for Veeam Plug-In for Oracle RMAN.  Specifies the storage options for Veeam Plug-In for Oracle RMAN. | Accepts the VBROracleRMANStorageOptions object. To define this object, run the [New-VBROracleRMANStorageOptions](new-vbroraclermanstorageoptions.md) cmdlet. | False | Named | False |
| OracleRMANOptions | Note: This option works only for Veeam Plug-In for Oracle RMAN.  Specifies the backup settings for Veeam Plug-In for Oracle RMAN. | Accepts the VBROracleRMANOptions object. To define this object, run the [New-VBROracleRMANOptions](new-vbroraclermanoptions.md) cmdlet. | False | Named | False |
| SAPHANAOptions | Note: This option works only for Veeam Plug-In for SAP HANA.  Specifies the backup settings for Veeam Plug-In for SAP HANA. | Accepts the VBRSAPHANAOptions object. To define this object, run the [New-VBRSAPHANAOptions](new-vbrsaphanaoptions.md) cmdlet. | False | Named | False |
| SAPHANACredentialsOptions | Note: This option works only for Veeam Plug-In for SAP HANA.  Specifies an array of the credentials for Veeam Plug-In for SAP HANA. | Accepts the VBRSAPHANACredentialsOptions[] object. To define this object, run the [New-VBRSAPHANACredentialsOptions](new-vbrsaphanacredentialsoptions.md) cmdlet. | False | Named | False |
| SAPHANAStorageOptions | Note: This option works only for Veeam Plug-In for SAP HANA.  Specifies the storage settings for Veeam Plug-In for SAP HANA. | Accepts the VBRSAPHANAStorageOptions object. To define this object, run the [New-VBRSAPHANAStorageOptions](new-vbrsaphanastorageoptions.md) cmdlet. | False | Named | False |
| MSSQLStorageOptions | Note: This option works only for Veeam Plug-In for Microsoft SQL Server.  Specifies the storage settings for Veeam Plug-In for Microsoft SQL Server. | Accepts the VBRMSSQLStorageOptions object. To define this object, run the [New-VBRMSSQLStorageOptions](new-vbrmssqlstorageoptions.md) cmdlet. | False | Named | False |
| MSSQLOptions | Note: This option works only for Veeam Plug-In for Microsoft SQL Server.  Specifies the backup settings for Veeam Plug-In for Microsoft SQL Server. | Accepts the VBRMSSQLOptions. To define this object, run the [New-VBRMSSQLOptions](new-vbrmssqloptions.md) cmdlet. | False | Named | False |
| MSSQLCredentialsOptions | Note: This option works only for Veeam Plug-In for Microsoft SQL Server.  Specifies an array of the credentials for Veeam Plug-In for Microsoft SQL Server. | Accepts the VBRMSSQLCredentialsOptions[] object. To define this object, run the [New-VBRMSSQLCredentialsOptions](new-vbrmssqlcredentialsoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRApplicationBackupJob[] object that contains settings of application backup policies.

Examples

Creating Application Backup Policy for Veeam Plug-In for SAP HANA

This example shows how to create the application backup policy for Veeam Plug-In for SAP HANA.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Database Servers"  $repository = Get-VBRBackupRepository -Name "Default Backup Repository"  $backup\_options = New-VBRApplicationBackupOptions -FullBackupScheduleType Weekly -WeeklyScheduleType SelectedDays -SelectedDays Sunday, Wednesday  $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 7:00  $schedule\_options = New-VBRApplicationScheduleOptions -Type Daily -DailyOptions $daily  $processing\_settings = New-VBRSAPHANAProcessingOptions -RedoLogsBackupPeriod 60 -LogBackupMode VeeamManaged  $db\_processing\_options = New-VBRDatabaseProcessingOptions -BackupObject $group -SAPHANAProcessingOptions $processing\_settings  $hana\_options = New-VBRSAPHANAOptions -ParallelChannelsCount 3  $os\_administrator = Get-VBRCredentials  $db\_hana\_administrator = Get-VBRCredentials  $hana\_credentials = New-VBRSAPHANACredentialsOptions -SAPSystem SH4 -SSHCredentials $os\_administrator -BackupCredentials $db\_hana\_administrator  Add-VBRApplicationBackupJob -BackupObject $group -BackupRepository $repository -Name "Backup Job" -Description "Daily backup of SAP systems" -BackupOptions $backup\_options -EnableSchedule -ScheduleOptions $schedule\_options -DatabaseProcessingOptions $db\_processing\_options -SAPHANAOptions $hana\_options -SAPHANACredentialsOptions $hana\_credentials |

Perform the following steps:

1. Get a protection group and a backup repository:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.

1. Define backup settings and backup schedule:

1. Run the [New-VBRApplicationBackupOptions](new-vbrapplicationbackupoptions.md) cmdlet. Specify the FullBackupScheduleType, WeeklyScheduleType and the SelectedDays parameter values. Save the result to the $backup\_options variable.
2. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek and the Period parameter values. Save the result to the $daily variable.
3. Run the [New-VBRApplicationScheduleOptions](new-vbrapplicationscheduleoptions.md) cmdlet. Specify the Type and the DailyOptions parameter values. Save the result to the $schedule\_options variable.

1. Define processing and backup settings:

1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $db\_administrator variable.
2. Run the [New-VBRSAPHANAProcessingOptions](new-vbrsaphanaprocessingoptions.md) cmdlet. Specify the RedoLogsBackupPeriod and LogBackupMode parameter values. Save the result to the $processing\_settings variable.
3. Run the [New-VBRDatabaseProcessingOptions](new-vbrdatabaseprocessingoptions.md) cmdlet. Specify the DayOfWeek and the SAPHANAProcessingOptions parameter values. Save the result to the $db\_processing\_options variable.
4. Run the [New-VBRSAPHANAOptions](new-vbrsaphanaoptions.md) cmdlet. Specify the ParallelChannelsCount parameter value. Save the result to the $hana\_options variable.

1. Get SAP HANA credentials settings:

1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $os\_administrator variable.
2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $db\_hana\_administrator variable.
3. Run the [New-VBRSAPHANACredentialsOptions](new-vbrsaphanacredentialsoptions.md) cmdlet. Specify the SAPSystem, SSHCredentials and the BackupCredentials parameter values. Save the result to the $hana\_credentials variable.

1. Run the Add-VBRApplicationBackupJob cmdlet. Specify the following settings:

* Set the $group variable as the BackupObject parameter value.
* Set the $repository variable as the BackupRepository parameter value.
* Specify the Name parameter value.
* Specify the Description parameter value.
* Set the $backup\_options variable as the BackupOptions parameter value.
* Provide the EnableSchedule parameter.
* Set the $schedule\_options variable as the ScheduleOptions parameter value.
* Set the $db\_processing\_options variable as the DatabaseProcessingOptions parameter value.
* Set the $hana\_options variable as the SAPHANAOptions parameter value.
* Set the $hana\_credentials variable as the SAPHANACredentialsOptions parameter value.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRApplicationBackupOptions](new-vbrapplicationbackupoptions.md)
* [New-VBRApplicationScheduleOptions](new-vbrapplicationscheduleoptions.md)
* [New-VBRSAPHANAProcessingOptions](new-vbrsaphanaprocessingoptions.md)
* [New-VBRDatabaseProcessingOptions](new-vbrdatabaseprocessingoptions.md)
* [New-VBRSAPHANAOptions](new-vbrsaphanaoptions.md)
* [New-VBRSAPHANACredentialsOptions](new-vbrsaphanacredentialsoptions.md)


