---
title: "Add-VBREC2BackupCopyJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrec2backupcopyjob.html"
last_updated: "2/19/2024"
product_version: "13.0.1.1071"
---

# Add-VBREC2BackupCopyJob (obsolete)

In this article

Short Description

Creates backup copy jobs for backups of Amazon EC2 instances.

|  |
| --- |
| Note |
| This cmdlet is obsolete and only works for creating a simple mode backup copy job. It is recommended to create a new backup job using the [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) cmdlet. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBREC2BackupCopyJob -Backup <VBREC2Backup[]> [-Name <string>] [-Description <string>] [-Repository <CBackupRepository>] [-RecoveryPointObjective <VBRRecoveryPointObjective>] [-RetentionPolicy <VBRRetentionPolicy>] [-BackupWindowOptions <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates backup copy jobs for backups of Amazon EC2 instances. Backup copy jobs will copy the backups from Amazon S3 external repositories to target repositories.

|  |
| --- |
| ![Add-VBREC2BackupCopyJob (obsolete)](images/icon_note.webp) Note: |
| The cmdlet creates jobs in a disabled state. Run the [Enable-VBRJob](enable-vbrjob.md) cmdlet to enable jobs. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an array of EC2 instance backups that you want to copy. | Accepts the VBREC2Backup[] object. To get this object, run the [Get-VBREC2Backup](get-vbrec2backup.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of a backup copy job. The cmdlet will create the job with this name. | String | False | Named | False |
| Description | Specifies a description of a backup copy job. The cmdlet will create the job with this description. | String | False | Named | False |
| Repository | Specifies a target backup repository. The cmdlet will copy EC2 instance backups to this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| RecoveryPointObjective | Specifies a backup copy interval. The cmdlet will copy new restore points of EC2 instance backups to the target backup repository. | Accepts the VBRRecoveryPointObjective object. To create this object, run the [New-VBRRecoveryPointObjective](new-vbrrecoverypointobjective.md) cmdlet. | False | Named | False |
| RetentionPolicy | Specifies a number of restore points to keep on a target backup repository. | Accepts the VBRRetentionPolicy object. To get this object, run the following cmdlets:   * [New-VBRGFSRetentionPolicy](new-vbrgfsretentionpolicy.md) * [New-VBRSimpleRetentionPolicy](new-vbrsimpleretentionpolicy.md) | False | Named | False |
| BackupWindowOptions | Specifies the period of time when a backup copy job is allowed to run. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Creating Backup Copy Job

This example shows how to create a backup copy job.

|  |
| --- |
| $instance = Get-VBREC2Backup -Name "VMEC2 Instance SRV10"  Add-VBREC2BackupCopyJob -Backup $instance |

Perform the following steps:

1. Run the [Get-VBREC2Backup](get-vbrec2backup.md) cmdlet. Specify the Name parameter value. Save the result to the $instance variable.
2. Run the Add-VBREC2BackupCopyJob cmdlet. Set the $instance variable as the Backup parameter value.

Related Commands

[Get-VBREC2Backup](get-vbrec2backup.md)

Page updated 2/19/2024

Page content applies to build 13.0.1.1071
