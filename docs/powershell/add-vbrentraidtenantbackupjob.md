---
title: "Add-VBREntraIDTenantBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrentraidtenantbackupjob.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# Add-VBREntraIDTenantBackupJob

In this article

Short Description

Creates a Microsoft Entra ID tenant backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBREntraIDTenantBackupJob [-Name <String>] [-Description <String>] -Tenant <VBREntraIDTenant> [-RetentionPolicy <Int32>] [-NotificationOptions <VBRNotificationOptions>] [-EnableSchedule] [-ScheduleOptions <VBRServerScheduleOptions>] [-EncryptionOptions <VBREncryptionOptions>] [-SecondaryTarget <VBREntraIDBackupSecondaryTarget[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a backup job that protects a Microsoft Entra ID tenant.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Tenant | Specifies the tenant whose data you want to back up. | Accepts the VBREntraIDTenant object. To get this object, run the [Get-VBREntraIDTenant](get-vbrentraidtenant.md) cmdlet. | True | Named | False |
| Name | Specifies the name of the tenant backup job. | String | False | Named | False |
| Description | Specifies the description of the tenant backup job. | String | False | Named | False |
| RetentionPolicy | Specifies the retention policy in days for backups created by the tenant backup job. | Int32 | False | Named | False |
| NotificationOptions | Specifies notification options. The cmdlet will create the tenant backup job with these notification options. | Accepts the VBRNotificationOptions object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| EnableSchedule | Defines that the cmdlet will enable the custom schedule for the tenant backup job.  If you provide this parameter, the tenant backup job will run according to the schedule specified in ScheduleOptions. Otherwise, to run the job, you will need to start it manually. | SwitchParameter | False | Named | False |
| ScheduleOptions | Specifies schedule options. | Accepts the VBRServerScheduleOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | False | Named | True (ByPropertyName, ByValue) |
| EncryptionOptions | Specifies encryption options. | Accepts the VBREncryptionOptions object. To create this object, run the [New-VBREncryptionOptions](new-vbrencryptionoptions.md) cmdlet. | False | Named | False |
| SecondaryTarget | Specifies secondary repository settings. | Accepts the VBREntraIDBackupSecondaryTarget object. To create this object, run the [New-VBREntraIDBackupSecondaryTarget](new-vbrentraidbackupsecondarytarget.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIDTenantBackupJob](vbrentraidtenantbackupjob.md) object that contains setting of the created tenant backup job.

Examples

Creating Entra ID Tenant Backup Job

This example shows how to add a tenant backup job with scheduling options and enabled encryption.

|  |
| --- |
| $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxx"  $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 7:00  $scheduleOptions = New-VBRServerScheduleOptions -Type Daily -DailyOptions $daily  $encKey = Get-VBREncryptionKey -Description "For Entra ID encryption"  $encOptions = New-VBREncryptionOptions -EnableEncryption -EncryptionKey $encKey  $backupJob = Add-VBREntraIDTenantBackupJob -Name "Tenant Backup" -Tenant $tenant -EnableSchedule -ScheduleOptions $scheduleOptions -EncryptionOptions $encOptions |

Perform the following steps:

1. Run the [Get-VBREntraIdTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable.
2. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek and Period parameter values. Save the result to the $daily variable.
3. Run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. Set the Daily value as the Type parameter value. Set the $daily variable as the DailyOptions parameter value. Save the result to the $scheduleOptions variable.
4. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save the result to the $encKey variable.
5. Run the [New-VBREncryptionOptions](new-vbrencryptionoptions.md) cmdlet. Specify the EnableEncryption parameter. Set the $encKey variable as the EncryptionKey parameter value. Save the result to the $encOptions variable.
6. Run the Add-VBREntraIDTenantBackupJob cmdlet. Specify the following settings:

* Specify the Name parameter value.
* Set the $tenant variable as the Tenant parameter value.
* Provide the EnableSchedule parameter.
* Set the $scheduleOptions variable as the ScheduleOptions parameter value.
* Set the $encOptions variable as the EncryptionOptions parameter value.
* Save the result to the $backupJob variable.

Related Commands

* [Get-VBREntraIdTenant](get-vbrentraidtenant.md)
* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)
* [New-VBREncryptionOptions](new-vbrencryptionoptions.md)
* [New-VBREntraIDBackupSecondaryTarget](new-vbrentraidbackupsecondarytarget.md)

Page updated 7/28/2025

Page content applies to build 13.0.1.1071
