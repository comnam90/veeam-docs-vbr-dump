---
title: "Set-VBRNASBackupSecondaryTarget (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnasbackupsecondarytarget.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Set-VBRNASBackupSecondaryTarget (obsolete)


Short Description

Modifies settings of secondary backup repositories.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Set-VBRUnstructuredBackupSecondaryTarget](set-vbrunstructuredbackupsecondarytarget.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNASBackupSecondaryTarget -SecondaryTarget <VBRNASBackupSecondaryTarget> [-BackupRepository <CBackupRepository>] [-EnableCustomRetention] [-CustomRetentionType <VBRNASBackupShortTermRetentionType> {Daily |Monthly}] [-CustomRetentionPeriod <int>] [-UseCustomEncryptionKey] [-CustomEncryptionKey <VBREncryptionKey>] [-EnableBackupWindow] [-BackupWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of secondary backup repositories.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SecondaryTarget | Specifies the secondary backup repository. The cmdlet will modify this repository. | Accepts the VBRNASBackupSecondaryTarget object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| BackupRepository | Specifies the backup repository that you want to add as a secondary backup repository to a file backup job. | Accepts the CBackupRepository object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| EnableCustomRetention | Enables the custom retention policy.  If you provide this parameter, Veeam Backup & Replication will apply this policy for backups located on the secondary backup repository. Otherwise, Veeam Backup & Replication will apply the retention policy of the file backup job to the secondary repository. | SwitchParameter | False | Named | False |
| CustomRetentionType | Specifies a retention policy for the secondary repository. You can set retention policy to either of the following periods:   * Daily: use this option if you want Veeam Backup & Replication to apply retention policy daily. * Monthly: use this option if you want Veeam Backup & Replication to apply retention policy monthly.   Use the ShortTermRetentionPeriod to specify the number of days or months.  Note: If you do not specify this parameter, Veeam Backup & Replication will apply the retention policy of the file backup job to the secondary repository. | VBRNASBackupShortTermRetentionType | False | Named | False |
| CustomRetentionPeriod | For the ShortTermRetentionType option.  Specifies the period of time to keep data on the secondary repository. When this period is passed, Veeam Backup & Replication will move data to the long-term repository. | Int32 | False | Named | False |
| UseCustomEncryptionKey | Defines that the cmdlet will enable the custom encryption key option.  If you provide this parameter, Veeam Backup & Replication will use the encryption key to encrypt data that is stored on the secondary repository.  Otherwise, Veeam Backup & Replication will apply an encryption key that is set to the file backup job to the secondary repository. | SwitchParameter | False | Named | False |
| CustomEncryptionKey | Specifies an encryption key. Veeam Backup & Replication will use this key to encrypt data that is stored on the secondary repository.  Note: If you do not specify this parameter, Veeam Backup & Replication will apply an encryption key that is set to the file backup job to the secondary repository. | Accepts the VBREncryptionKey object. To create this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| EnableBackupWindow | Enables the backup window option.  If you provide this parameter, Veeam Backup & Replication will create copies of backups that were created by file backup jobs according to these settings.  Otherwise, Veeam Backup & Replication will copy data to the repository continuously. | SwitchParameter | False | Named | False |
| BackupWindow | Specifies backup window settings. Veeam Backup & Replication will create copies of backups that were created by file backup jobs according to these settings. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNASBackupSecondaryTarget](vbrnasbackupsecondarytarget.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Custom Retention Policy

|  |  |
| --- | --- |
| This example shows how to enable custom retention policy for the SecondaryBackupRepository08 secondary backup repository. The custom retention policy will be enabled with the following settings:   * Veeam Backup & Replication will apply retention policy daily * Veeam Backup & Replication will keep data on the secondary repository for 7 days     |  | | --- | | $repository = Get-VBRBackupRepository -Name "SecondaryBackupRepository08"  Set-VBRNASBackupSecondaryTarget -SecondaryTarget $repository -EnableCustomRetention -CustomRetentionType Daily -CustomRetentionPeriod 7 |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Set-VBRNASBackupSecondaryTarget cmdlet. Specify the following settings:  * Set the $repository variable as the SecondaryTarget parameter value. * Provide the EnableCustomRetention parameter. * Set the Daily option as the CustomRetentionType parameter value. * Specify the CustomRetentionPeriod parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling Custom Encryption Key

|  |  |
| --- | --- |
| This example shows how to enable custom encryption key for the SecondaryBackupRepository08 secondary backup repository.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "SecondaryBackupRepository08"  $key = Get-VBREncryptionKey -Description NasEncryption  Set-VBRNASBackupSecondaryTarget -SecondaryTarget $repository -UseCustomEncryptionKey -CustomEncryptionKey $key |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. 3. Run the Set-VBRNASBackupSecondaryTarget cmdlet. Specify the following settings:  * Set the $repository as the SecondaryTarget parameter value. * Provide the UseCustomEncryptionKey parameter. * Set the $key variable as the CustomEncryptionKey parameter value. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)


