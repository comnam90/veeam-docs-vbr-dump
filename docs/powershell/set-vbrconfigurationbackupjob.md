---
title: "Set-VBRConfigurationBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrconfigurationbackupjob.html"
last_updated: "5/15/2024"
product_version: "13.0.1.1071"
---

# Set-VBRConfigurationBackupJob


Short Description

Modifies the configuration backup job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRConfigurationBackupJob [-Enable] [-Repository <CBackupRepository>] [-ScheduleOptions <VBRConfigurationBackupScheduleOptions>] [-RestorePointsToKeep <int>] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-NotificationOptions <VBRNotificationOptions>] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of the configuration backup job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Enable | Defines that the job will run automatically on schedule.  If set to $False, you will need to run the job manually.  Default: True.  Note: To disable the configuration job schedule, specify the $false value for the Enable parameter. | SwitchParameter | False | Named | False |
| Repository | Specifies the backup repository where you want to store the configuration backups.  You cannot specify a cloud repository that is created on base of scale-out backup repository. | Accepts the CBackupRepository object or string (repository name). To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| ScheduleOptions | Specifies the schedule for the configuration backup job. | Accepts the [VBRConfigurationBackupScheduleOptions](vbrconfigurationbackupscheduleoptions.md) object. To get this object, run the [New-VBRConfigurationBackupScheduleOptions](new-vbrconfigurationbackupscheduleoptions.md) cmdlet. | False | Named | False |
| RestorePointsToKeep | Specifies the number of restore points you want to keep on disk.  You can set 1 to 255. | Int32 | False | Named | False |
| EnableEncryption | If set to true, the configuration backup will be encrypted.  Use the EncryptionKey parameter to specify the encryption key.  Note: if you have created at least one password in the Password Manager on the backup server, you must enable encryption for the configuration backup. | SwitchParameter | False | Named | False |
| EncryptionKey | Used to set the encryption key for the EnableEncryption parameter.  Specifies the encryption key you want to use to encrypt the data. | Accepts the [VBREncryptionKey](pscryptokey.md) object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies email notification options for the configuration backup job. | Accepts the [VBRNotificationOptions](vbrnotificationoptions.md) object. Run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet to create this object. | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRConfigurationBackupJob](vbrconfigurationbackupjob.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling Configuration Backup Job

|  |  |
| --- | --- |
| This command disables the configuration backup job.  |  | | --- | | Set-VBRConfigurationBackupJob -Enable:$False | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Configuration Backup Schedule and Enabling Encryption

|  |  |
| --- | --- |
| This command modifies the configuration backup schedule and enables encryption. The job is set to run at 00:00 every Saturday.  |  | | --- | | $daily = New-VBRDailyOptions -Period "05:00" -DayOfWeek Saturday  $dailyschedule = New-VBRConfigurationBackupScheduleOptions -Type Daily -DailyOptions $daily  $encryptionkey = Get-VBREncryptionKey -Description "veeam encryption"  Set-VBRConfigurationBackupJob -ScheduleOptions $dailyschedule -EnableEncryption -EncryptionKey $encryptionkey |  Perform the following steps:   1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the Period and the DayOfWeek parameter values. Save the result to the $daily variable. 2. Run the [New-VBRConfigurationBackupScheduleOptions](new-vbrconfigurationbackupscheduleoptions.md) cmdlet. Set the Daily option for the Type parameter. Set the $daily variable as the DailyOptions parameter value. Save the result to the $dailyschedule variable. 3. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save it to the $encryptionkey variable. 4. Run the Set-VBRConfigurationBackupJob cmdlet. Set the $dailyschedule variable as the ScheduleOptions parameter value. Provide the EnableEncryption parameter. Set the $encryptionkey variable as the EncryptionKey parameter value. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRConfigurationBackupScheduleOptions](new-vbrconfigurationbackupscheduleoptions.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)


