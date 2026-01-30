---
title: "New-VBREntraIDBackupSecondaryTarget"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrentraidbackupsecondarytarget.html"
last_updated: "9/11/2025"
product_version: "13.0.1.1071"
---

# New-VBREntraIDBackupSecondaryTarget


Short Description

Defines secondary repository settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBREntraIDBackupSecondaryTarget -BackupRepository <CBackupRepository> [-CustomRetentionType <VBRUnstructuredBackupShortTermRetentionType>] [-CustomRetentionPeriod <Int32>] [-CustomEncryptionKey <VBREncryptionKey>] [-BackupWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines secondary repository settings for a Entra ID tenant backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupRepository | Specifies the backup repository to use as a secondary target for Entra ID tenant backups. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| BackupWindow | Specifies a time interval within which a backup job is allowed to create copies of Entra ID tenant backups. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| CustomEncryptionKey | Specifies an encryption key. Veeam Backup & Replication will use this key to encrypt data that is stored in the secondary repository.  Note: If you do not specify this parameter, Veeam Backup & Replication will apply an encryption key set for the backup job. | Accepts the VBREncryptionKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| CustomRetentionPeriod | Specifies the period of time to keep data on the secondary repository. When this period is expired, Veeam Backup & Replication will move data to the long-term repository. | Int32 | False | Named | False |
| CustomRetentionType | Specifies a retention policy for the secondary repository. You can set retention policy to either of the following periods:   * Daily: use this option if you want Veeam Backup & Replication to apply retention policy daily. * Monthly: use this option if you want Veeam Backup & Replication to apply retention policy monthly.   Note: If you do not specify this parameter, Veeam Backup & Replication will apply the retention policy configured for the backup job. | VBRUnstructuredBackupShortTermRetentionType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIDBackupSecondaryTarget](vbrentraidbackupsecondarytarget.md) object that defines secondary repository settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Secondary Repository Settings

|  |  |
| --- | --- |
| This example shows how to define the following secondary repository settings for a Entra ID tenant backup job:   * Veeam Backup & Replication will apply a retention policy that is configured for the backup job. * Veeam Backup & Replication will apply an encryption key that is set for the backup job. * Veeam Backup & Replication will copy data to the repository continuously.       |  | | --- | | $repository = Get-VBRBackupRepository -Name "repository-01"  New-VBREntraIDBackupSecondaryTarget -BackupRepository $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the New-VBREntraIDBackupSecondaryTarget cmdlet. Set the $repository variable as the BackupRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Secondary Repository Settings with Custom Retention Policy

|  |  |
| --- | --- |
| This example shows how to define the secondary repository settings with a custom retention policy. Veeam Backup & Replication will keep versions of backup files on the secondary backup repository for 7 days.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "repository-01"  New-VBREntraIDBackupSecondaryTarget -BackupRepository $repository -CustomRetentionType Daily -CustomRetentionPeriod 7 |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the New-VBREntraIDBackupSecondaryTarget cmdlet. Specify the following settings:  * Set the $repository variable as the BackupRepository parameter value. * Set the Daily option for the CustomRetentionType parameter. * Specify the value for the CustomRetentionPeriod parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Secondary Repository Settings with Backup Window

|  |  |
| --- | --- |
| This example shows how to define the secondary repository settings with a custom schedule settings. Veeam Backup & Replication will copy data to the secondary repository according to the following schedule:   * From 22:00 to 22:59 on Friday * From 22:00 to 22:59 on Saturday     |  | | --- | | $repository = Get-VBRBackupRepository -Name "Backup Repository 07"  $windowoptions = New-VBRBackupWindowOptions -FromDay Friday -FromHour 22 -ToDay Saturday -ToHour 22 -Enabled  New-VBREntraIDBackupSecondaryTarget -BackupRepository $repository -BackupWindow $windowoptions |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. Specify the FromDay, FromHour, ToDay and ToHour parameter values. Save the result to the $windowoptions variable. 3. Run the New-VBREntraIDBackupSecondaryTarget cmdlet. Set the $repository variable as the BackupRepository parameter value. Set the $windowoptions variable as the BackupWindow parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Defining Secondary Repository Settings for New Entra ID Tenant Backup Job

|  |  |
| --- | --- |
| This example shows how to define secondary repository settings for a new Entra ID tenant backup job.  |  | | --- | | $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxx"  $primaryRepo = Get-VBRBackupRepository -Name ‘Primary repository’  $copyRepo = Get-VBRBackupRepository -Name ‘Off-site repository’  $secondaryTarget = New-VBREntraIDBackupSecondaryTarget -BackupRepository $copyRepo  $notifications = New-VBRNotificationOptions  Add-VBREntraIDTenantBackupJob -Name ‘Tenant backup’ -Tenant $tenant -NotificationOptions $notificationOptions -SecondaryTarget $secondaryTarget |  Perform the following steps:   1. Run the [Get-VBREntraIDTenant](get-vbrentraidtenant.md) cmdlet. Specify the AzureTenantId parameter value. Save the result to the $tenant variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $primaryRepo variable. 3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $copyRepo variable. 4. Run the New-VBREntraIDBackupSecondaryTarget cmdlet. Specify the BackupRepository parameter value. Save the result to the $secondaryTarget variable. 5. Run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. Save the result to the $notifications variable. 6. Run the [Add-VBREntraIDTenantBackupJob](add-vbrentraidtenantbackupjob.md) cmdlet. Specify the following settings:  * Provide the Name parameter. * Set the $tenant variable as the Tenant parameter value. * Set the $notificationOptions variable as the NotificationOptions parameter value. * Set the $secondaryTarget variable as the SecondaryTarget parameter value. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)
* [Add-VBREntraIDTenantBackupJob](add-vbrentraidtenantbackupjob.md)
* [New-VBRNotificationOptions](new-vbrnotificationoptions.md)


