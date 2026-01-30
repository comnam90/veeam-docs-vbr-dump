---
title: "Set-VBREC2BackupCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrec2backupcopyjob.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Set-VBREC2BackupCopyJob


Short Description

Modifies backup copy jobs for backups of Amazon EC2 instances.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBREC2BackupCopyJob -Job <CBackupJob> [-Name <string>] [-Description <string>] [-Backup <VBREC2Backup[]>] [-Repository <CBackupRepository>] [-RecoveryPointObjective <VBRRecoveryPointObjective>] [-RetentionPolicy <VBRRetentionPolicy>] [-BackupWindowOptions <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies backup copy jobs that copy backups of Amazon EC2 instances.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a backup copy job that you want to modify. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of a backup copy job. | String | False | Named | False |
| Description | Specifies a description of a backup copy job. | String | False | Named | False |
| Backup | Specifies an array of EC2 instance backups that you want to copy. | Accepts the VBREC2Backup[] object. To get this object, run the [Get-VBREC2Backup](get-vbrec2backup.md) cmdlet. | False | Named | False |
| Repository | Specifies a target backup repository. The cmdlet will copy EC2 instance backups to this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| RecoveryPointObjective | Specifies a backup copy interval. The cmdlet will copy new restore points of EC2 instance backups to the target backup repository. | Accepts the VBRRetentionPolicy object. To get this object, run the following cmdlets:   * [New-VBRGFSRetentionPolicy](new-vbrgfsretentionpolicy.md) * [New-VBRSimpleRetentionPolicy](new-vbrsimpleretentionpolicy.md) | False | Named | False |
| RetentionPolicy | Specifies a number of restore points to keep on a target backup repository. | Accepts the VBRRetentionPolicy object. To get this object, run the [Get-VBRRetentionPolicy](get-vbrretentionpolicy.md) cmdlet. | False | Named | False |
| BackupWindowOptions | Specifies the period of time when a backup copy job is allowed to run. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBREC2Backup object that contains an array of EC2 instance backups.

Examples

Adding Amazon EC2 Instance to Backup Copy Job

This example shows how to add an Amazon EC2 instance to a backup copy job.

|  |
| --- |
| $copyjob = Get-VBRJob -Name "VMEC2 Instance Copy Job SRV10"  $instance = Get-VBREC2Backup -Name "VMEC2 Instance SRV10 01"  Set-VBREC2BackupCopyJob -Job $copyjob -Backup $instance |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $copyjob variable.
2. Run the [Get-VBREC2Backup](get-vbrec2backup.md) cmdlet. Specify the Name parameter value. Save the result to the $instance variable.
3. Run the Set-VBREC2BackupCopyJob cmdlet. Set the $copyjob variable as the Job parameter value. Set the $instance variable as the Backup parameter value.

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBREC2Backup](get-vbrec2backup.md)


