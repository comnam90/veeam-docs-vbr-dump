---
title: "New-VBRNASBackupSecondaryTarget (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrnasbackupsecondarytarget.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# New-VBRNASBackupSecondaryTarget (obsolete)


Short Description

Creates secondary backup repositories for file backup jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [New-VBRUnstructuredBackupSecondaryTarget](new-vbrunstructuredbackupsecondarytarget.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRNASBackupSecondaryTarget -BackupRepository <CBackupRepository> [-CustomRetentionType <VBRNASBackupShortTermRetentionType> {Daily | Monthly}] [-CustomRetentionPeriod <int>] [-CustomEncryptionKey <VBREncryptionKey>] [-BackupWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates secondary backup repositories. These repositories will keep copies of backup files that were created by file backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupRepository | Specifies the backup repository that you want to add as a secondary backup repository to a file backup job. | Accepts the CBackupRepository object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| CustomRetentionType | Specifies a retention policy for the secondary repository. You can set retention policy to either of the following periods:   * Daily: use this option if you want Veeam Backup & Replication to apply retention policy daily. * Monthly: use this option if you want Veeam Backup & Replication to apply retention policy monthly.   Use the ShortTermRetentionPeriod to specify the number of days or months.  Note: If you do not specify this parameter, Veeam Backup & Replication will apply the retention policy of the file backup job to the secondary repository. | VBRNASBackupShortTermRetentionType | False | Named | False |
| CustomRetentionPeriod | For the ShortTermRetentionType option.  Specifies the period of time to keep data on the secondary repository. When this period is passed, Veeam Backup & Replication will move data to the long-term repository. | Int32 | False | Named | False |
| CustomEncryptionKey | Specifies an encryption key. Veeam Backup & Replication will use this key to encrypt data that is stored on the secondary repository.  Note: If you do not specify this parameter, Veeam Backup & Replication will apply an encryption key that is set to the file backup job to the secondary repository. | Accepts the VBREncryptionKey object. To create this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| BackupWindow | Specifies backup window settings. Veeam Backup & Replication will create copies of backups that were created by file backup jobs according to these settings. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNASBackupSecondaryTarget](vbrnasbackupsecondarytarget.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Backup Repository

|  |  |
| --- | --- |
| This example shows how to create a secondary backup repository. The secondary repository will be created with the following settings:   * Veeam Backup & Replication will apply a retention policy that is set to the file backup job. * Veeam Backup & Replication will apply an encryption key that is set to the file backup job. * Veeam Backup & Replication will copy data to the repository continuously.       |  | | --- | | $repository = Get-VBRBackupRepository -Name "Backup Repository 07"  New-VBRNASBackupSecondaryTarget -BackupRepository $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the New-VBRNASBackupSecondaryTarget cmdlet. Set the $repository variable as the BackupRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Backup Repository with Custom Retention Policy

|  |  |
| --- | --- |
| This example shows how to create a secondary backup repository with the custom retention policy. Veeam Backup & Replication will keep versions of backup files on the secondary backup repository for 7 days.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "Backup Repository 07"  New-VBRNASBackupSecondaryTarget -BackupRepository $repository -CustomRetentionType Daily -CustomRetentionPeriod 7 |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the New-VBRNASBackupSecondaryTarget cmdlet. Specify the following settings:  * Set the $repository variable as the BackupRepository parameter value. * Set the Daily option for the CustomRetentionType parameter. * Specify the CustomRetentionPeriod parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Backup Repository with Backup Window

|  |  |
| --- | --- |
| This example shows how to create a secondary backup repository. Veeam Backup & Replication will copy data to the secondary repository according to the following schedule:   * From 22:00 to 22:59 on Friday * From 22:00 to 22:59 on Saturday     |  | | --- | | $repository = Get-VBRBackupRepository -Name "Backup Repository 07"  $windowoptions = New-VBRBackupWindowOptions -FromDay Friday -FromHour 22 -ToDay Saturday -ToHour 22 -Enabled  New-VBRNASBackupSecondaryTarget -BackupRepository $repository -BackupWindow $windowoptions |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. Specify the necessary parameters. Save the result to the $windowoptions variable. 3. Run the New-VBRNASBackupSecondaryTarget cmdlet. Set the $repository variable as the BackupRepository parameter value. Set the $windowoptions variable as the BackupWindow parameter value. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)


