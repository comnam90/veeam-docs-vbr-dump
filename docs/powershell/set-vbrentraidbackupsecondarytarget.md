---
title: "Set-VBREntraIDBackupSecondaryTarget"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrentraidbackupsecondarytarget.html"
last_updated: "9/11/2025"
product_version: "13.0.1.1071"
---

# Set-VBREntraIDBackupSecondaryTarget


Short Description

Modifies secondary repository settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBREntraIDBackupSecondaryTarget -SecondaryTarget <VBREntraIDBackupSecondaryTarget> [-BackupRepository <CBackupRepository>] [-EnableCustomRetention] [-CustomRetentionType <VBRUnstructuredBackupShortTermRetentionType>] [-CustomRetentionPeriod <Int32>] [-UseCustomEncryptionKey] [-CustomEncryptionKey <VBREncryptionKey>] [-EnableBackupWindow] [-BackupWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies secondary repository settings of an Entra ID tenant backup job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SecondaryTarget | Specifies the secondary backup repository. The cmdlet will modify this repository. | Accepts the VBREntraIDBackupSecondaryTarget object. To get this object, run the [New-VBREntraIDBackupSecondaryTarget](new-vbrentraidbackupsecondarytarget.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| BackupRepository | Specifies the backup repository to use as a secondary target for Entra ID tenant backups. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| EnableBackupWindow | Defines that the cmdlet will enable the backup window option.  If you provide this parameter, Veeam Backup & Replication will create copies of backups that were created by the backup job according to these settings.  Otherwise, Veeam Backup & Replication will copy data to the repository continuously. | SwitchParameter | False | Named | False |
| BackupWindow | Specifies a time interval within which a backup job is allowed to create copies of Entra ID tenant backups. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| UseCustomEncryptionKey | Defines that the cmdlet will enable the custom encryption key option.  If you provide this parameter, Veeam Backup & Replication will use the encryption key to encrypt data that is stored in the secondary repository.  Otherwise, Veeam Backup & Replication will apply an encryption key that is set for the backup job. | SwitchParameter | False | Named | False |
| CustomEncryptionKey | Specifies an encryption key. Veeam Backup & Replication will use this key to encrypt data that is stored in the secondary repository.  Note: If you do not specify this parameter, Veeam Backup & Replication will apply an encryption key set for the backup job. | Accepts the VBREncryptionKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| EnableCustomRetention | Defines that the cmdlet will enable the custom retention policy.  If you provide this parameter, Veeam Backup & Replication will apply this policy for backups located on the secondary backup repository. Otherwise, Veeam Backup & Replication will apply the retention policy of the backup job to the secondary repository. | SwitchParameter | False | Named | False |
| CustomRetentionPeriod | Specifies the period of time to keep data on the secondary repository. When this period is expired, Veeam Backup & Replication will move data to the long-term repository. | Int32 | False | Named | False |
| CustomRetentionType | Specifies a retention policy for the secondary repository. You can set retention policy to either of the following periods:   * Daily: use this option if you want Veeam Backup & Replication to apply retention policy daily. * Monthly: use this option if you want Veeam Backup & Replication to apply retention policy monthly.   Note: If you do not specify this parameter, Veeam Backup & Replication will apply the retention policy configured for the backup job. | VBRUnstructuredBackupShortTermRetentionType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIDBackupSecondaryTarget](vbrentraidbackupsecondarytarget.md) object that defines secondary repository settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Custom Retention Policy

|  |  |
| --- | --- |
| This example shows how to enable custom retention policy for the SecondaryBackupRepository08 secondary repository. The custom retention policy will be enabled with the following settings:   * Veeam Backup & Replication will apply retention policy daily. * Veeam Backup & Replication will keep data in the secondary repository for 7 days.   |  | | --- | | $repository = Get-VBRBackupRepository -Name "SecondaryBackupRepository08"  Set-VBREntraIDBackupSecondaryTarget -SecondaryTarget $repository -EnableCustomRetention -CustomRetentionType Daily -CustomRetentionPeriod 7 |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Set-VBREntraIDBackupSecondaryTarget cmdlet. Specify the following settings:  * Set the $repository variable as the SecondaryTarget parameter value. * Provide the EnableCustomRetention parameter value. * Set the Daily option for the CustomRetentionType parameter. * Specify the CustomRetentionPeriod parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling Custom Encryption Key

|  |  |
| --- | --- |
| This example shows how to enable custom encryption key for the SecondaryBackupRepository08 secondary repository.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "SecondaryBackupRepository08"  $key = Get-VBREncryptionKey -Description "KeyForEncryption"  Set-VBREntraIDBackupSecondaryTarget -SecondaryTarget $repository -UseCustomEncryptionKey -CustomEncryptionKey $key |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save the result to the $key variable. 3. Run the Set-VBREntraIDBackupSecondaryTarget cmdlet. Specify the following settings:  * Set the $repository as the SecondaryTarget parameter value. * Provide the UseCustomEncryptionKey parameter. * Set the $key variable as the CustomEncryptionKey parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Secondary Repository Settings for Existing Entra ID Tenant Backup Job

|  |  |
| --- | --- |
| This example shows how to modify secondary repository settings for the existing Entra ID tenant backup job.  |  | | --- | | $repository = Get-VBRBackupRepository -Name ‘Off-site repository’  $job = Get-VBREntraIDTenantBackupJob -Name ‘Tenant backup’  $secondaryTarget = $job.SecondaryTarget  $newSecondaryOptions = Set-VBREntraIDBackupSecondaryTarget -SecondaryTarget $secondaryTarget -BackupRepository $repository  Set-VBREntraIDTenantBackupJob -Job $job -SecondaryTarget $newSecondaryOptions |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 3. Specify the SecondaryTarget property for the $job variable. Save the result to the $secondaryTarget variable. 4. Run the Set-VBREntraIDBackupSecondaryTarget cmdlet. Set the $secondaryTarget as the SecondaryTarget parameter value. Set the $repository as the BackupRepository parameter value. 5. Run the [Set-VBREntraIDTenantBackupJob](set-vbrentraidtenantbackupjob.md) cmdlet. Set the $job as the Job parameter value. Set the $newSecondaryOptions as the SecondaryTarget parameter value. |

Related Commands

* [New-VBREntraIDBackupSecondaryTarget](new-vbrentraidbackupsecondarytarget.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)


