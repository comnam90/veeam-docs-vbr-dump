---
title: "Set-VBRApplicationBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrapplicationbackupjob.html"
last_updated: "10/22/2025"
product_version: "13.0.1.1071"
---

# Set-VBRApplicationBackupJob


Short Description

Modifies application backup policies.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRApplicationBackupJob -Job <VBRApplicationBackupJob> [-Description <string>] [-BackupObject <Object[]> ] [-BackupRepository <CBackupRepository>] [-BackupOptions <VBRApplicationBackupOptions>] [-EnableRetentionPolicy] [-RetentionPolicy <int>] [-EnableSchedule] [-ScheduleOptions <VBRApplicationScheduleOptions>] [-NotificationOptions <VBRNotificationOptions>] [-DatabaseProcessingOptions <VBRDatabaseProcessingOptions[]>] [-SAPOnOracleMode {RMAN | BACKINT}] [-SAPOnOracleStorageOptions <VBRSAPOnOracleStorageOptions>] [-SAPOnOracleOptions <VBRSAPOnOracleOptions>] [-OracleRMANStorageOptions <VBROracleRMANStorageOptions>] [-OracleRMANOptions <VBROracleRMANOptions>] [-SAPHANAOptions <VBRSAPHANAOptions>] [-SAPHANACredentialsOptions <VBRSAPHANACredentialsOptions[]>] [-SAPHANAStorageOptions <VBRSAPHANAStorageOptions>] [-MSSQLOptions <VBRMSSQLOptions>] [-MSSQLCredentialsOptions <VBRMSSQLCredentialsOptions[]>] [-MSSQLStorageOptions <VBRMSSQLStorageOptions>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of application backup policies.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the application backup policy that you want to modify. | Accepts the VBRApplicationBackupJob object. To get this object, run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) group cmdlet. | True | Named | True (ByValue) |
| BackupObject | Specifies an array of protection groups and discovered computers that you want to add to the application backup policy. | Accepts the Object[] object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | False | Named | False |
| BackupRepository | Specifies the target backup location for the application backup policy. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Name | Specifies the name that you want to assign to the application backup policy. | String | False | Named | False |
| Description | Specifies the description of the application backup policy. | String | False | Named | False |
| BackupOptions | Specifies backup settings for the application backup policy. | Accepts the VBRApplicationBackupOptions object. To define this object, run the [New-VBRApplicationBackupOptions](new-vbrapplicationbackupoptions.md) cmdlet. | False | Named | False |
| EnableRetentionPolicy | Enables retention policy. | SwitchParameter | False | Named | False |
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
| SAPHANAOptions | Note: This option works only for Veeam Plug-In for SAP HANA.  Specifies the backup settings for Veeam Plug-In for SAP HANA. | Accepts the VBROracleRMANOptions object. To define this object, run the [New-VBRSAPHANAOptions](new-vbrsaphanaoptions.md) cmdlet. | False | Named | False |
| SAPHANACredentialsOptions | Note: This option works only for Veeam Plug-In for SAP HANA.  Specifies the credentials settings for Veeam Plug-In for SAP HANA. | Accepts the VBRSAPHANACredentialsOptions[] object. To define this object, run the [New-VBRSAPHANAOptions](new-vbrsaphanaoptions.md) cmdlet. | False | Named | False |
| SAPHANAStorageOptions | Note: This option works only for Veeam Plug-In for SAP HANA.  Specifies the storage settings for Veeam Plug-In for SAP HANA. | Accepts the VBRSAPHANAStorageOptions object. To define this object, run the [New-VBRSAPHANAStorageOptions](new-vbrsaphanastorageoptions.md) cmdlet. | False | Named | False |
| MSSQLStorageOptions | Note: This option works only for Veeam Plug-In for Microsoft SQL Server.  Specifies the storage settings for Veeam Plug-In for Microsoft SQL Server. | Accepts the VBRMSSQLStorageOptions object. To define this object, run the [New-VBRMSSQLStorageOptions](new-vbrmssqlstorageoptions.md) cmdlet. | False | Named | False |
| MSSQLOptions | Note: This option works only for Veeam Plug-In for Microsoft SQL Server.  Specifies the backup settings for Veeam Plug-In for Microsoft SQL Server. | Accepts the VBRMSSQLOptions object. To define this object, run the [New-VBRMSSQLOptions](new-vbrmssqloptions.md) cmdlet. | False | Named | False |
| MSSQLCredentialsOptions | Note: This option works only for Veeam Plug-In for Microsoft SQL Server.  Specifies an array of the credentials for Veeam Plug-In for Microsoft SQL Server | Accepts the VBRMSSQLCredentialsOptions[] object. To define this object, run the [New-VBRMSSQLCredentialsOptions](new-vbrmssqlcredentialsoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Objet

This cmdlet returns the VBRApplicationBackupJob[] object that contains settings of application backup policies.

Examples

Modifying SAP HANA Backup Settings for Application Backup Policy

This example shows how to modify the number of data processing channels that can be assigned to the Plugin Policy 05 application backup policy.

|  |
| --- |
| $policy = Get-VBRApplicationBackupJob -Name "Plugin Policy 05"  $hana\_options = New-VBRSAPHANAOptions -ParallelChannelsCount 5  Set-VBRApplicationBackupJob -Job $policy -SAPHANAOptions $hana\_options |

Perform the following steps:

1. Run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $policy variable.
2. Run the [New-VBRSAPHANAOptions](new-vbrsaphanaoptions.md) cmdlet. Specify the ParallelChannelsCount parameter value. Save the result to the $hana\_options variable.
3. Run the Set-VBRApplicationBackupJob cmdlet. Set the $policy variable as the Job parameter value. Set the $hana\_options variable as the SAPHANAOptions parameter value.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRApplicationBackupOptions](new-vbrapplicationbackupoptions.md)
* [New-VBRApplicationScheduleOptions](new-vbrapplicationscheduleoptions.md)
* [New-VBRSAPHANAProcessingOptions](new-vbrsaphanaprocessingoptions.md)
* [New-VBRDatabaseProcessingOptions](new-vbrdatabaseprocessingoptions.md)
* [New-VBRSAPHANAOptions](new-vbrsaphanaoptions.md)
* [New-VBRSAPHANACredentialsOptions](new-vbrsaphanacredentialsoptions.md)
* [Add-VBRApplicationBackupJob](add-vbrapplicationbackupjob.md)


