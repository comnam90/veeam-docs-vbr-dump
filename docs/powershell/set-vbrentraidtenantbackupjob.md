---
title: "Set-VBREntraIDTenantBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrentraidtenantbackupjob.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# Set-VBREntraIDTenantBackupJob


Short Description

Modifies a backup job that protects a Microsoft Entra ID tenant.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBREntraIDTenantBackupJob -Job <VBREntraIDTenantBackupJob> [-Name <String>] [-Description <String>] [-RetentionPolicy <Int32>] [-NotificationOptions <VBRNotificationOptions>] [-EnableSchedule] [-ScheduleOptions <VBRServerScheduleOptions>] [-EncryptionOptions <VBREncryptionOptions>] [-SecondaryTarget <VBREntraIDBackupSecondaryTarget[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies an Entra ID tenant backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the tenant backup job that you want to modify. | Accepts the VBREntraIDTenantBackupJob object. To get this object, run the [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Name | Specifies the name of the tenant backup job. | String | False | Named | False |
| Description | Specifies the description of the tenant backup job. | String | False | Named | False |
| RetentionPolicy | Specifies the retention policy in days for backups created by the tenant backup job. | Int32 | False | Named | False |
| NotificationOptions | Specifies notification options. The cmdlet will create the log backup job with these notification options. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| EnableSchedule | Defines that the cmdlet will enable the custom schedule for the tenant backup job.  If you provide this parameter, the tenant backup job will run according to the schedule specified in ScheduleOptions. Otherwise, to run the job, you will need to start it manually. | SwitchParameter | False | Named | False |
| ScheduleOptions | Specifies schedule options. | Accepts the VBRServerScheduleOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | True (ByPropertyName, ByValue) |
| EncryptionOptions | Specifies encryption options. | Accepts the VBREncryptionOptions object. To create this object, run the [New-VBREncryptionOptions](new-vbrencryptionoptions.md) cmdlet. | False | Named | False |
| SecondaryTarget | Specifies secondary repository settings. | Accepts the VBREntraIDBackupSecondaryTarget object. To create this object, run the [New-VBREntraIDBackupSecondaryTarget](new-vbrentraidbackupsecondarytarget.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIDTenantBackupJob](vbrentraidtenantbackupjob.md) object that contains setting of the created tenant backup job.

Examples

Changing Settings of Entra ID Backup Job

This example shows how to change the settings of the Tenant Backup backup job and disable encryption.

|  |
| --- |
| $backupJob = Get-VBREntraIDTenantBackupJob -Name "Tenant Backup"  $encOptions = New-VBREncryptionOptions -EnableEncryption:$false  Set-VBREntraIDTenantBackupJob -Job $backupJob -Description "Backup of Entra ID tenant" -RetentionPolicy 12 -EncryptionOptions $encOptions |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $backupJob variable.
2. Run the [New-VBREncryptionOptions](new-vbrencryptionoptions.md) cmdlet. Set the EnableEncryption parameter value to $false. Save the result to the $encOptions variable.
3. Run the Set-VBREntraIDTenantBackupJob cmdlet. Specify the following:

* Set the $backupJob variable as the Job parameter value.
* Specify the Description and RetentionPolicy parameter values.
* Set the $encOptions variable as the EncryptionOptions parameter value.

Related Commands

* [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md)
* [New-VBREncryptionOptions](new-vbrencryptionoptions.md)
* [New-VBREntraIDBackupSecondaryTarget](new-vbrentraidbackupsecondarytarget.md)


