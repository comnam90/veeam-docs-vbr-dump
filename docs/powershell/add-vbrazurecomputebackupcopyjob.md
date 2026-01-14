---
title: "Add-VBRAzureComputeBackupCopyJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrazurecomputebackupcopyjob.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Add-VBRAzureComputeBackupCopyJob (obsolete)

In this article

Short Description

Creates Azure IaaS backup copy jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete and only works for creating a simple mode backup copy job. It is recommended to create a new backup job using the [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) cmdlet. |

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAzureComputeBackupCopyJob -Backup <VBRAzureComputeBackup[]> [-Name <string>] [-Description <string>] [-Repository <CBackupRepository>] [-RecoveryPointObjective <VBRRecoveryPointObjective>] [-RetentionPolicy <VBRRetentionPolicy>] [-BackupWindowOptions <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates Azure IaaS backup copy jobs of Azure Virtual Machines that are stored on a Microsoft Azure Blob Storage repository. Azure IaaS backup copy jobs will copy the backups from Microsoft Azure Blob Storage external repositories to target repositories.

|  |
| --- |
| Note |
| The cmdlet creates jobs in a disabled state. Run the [Enable-VBRJob](enable-vbrjob.md) cmdlet to enable jobs. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an array of Azure backups that you want to copy. | Accepts the VBRAzureComputeBackup[] object. To get this object, run the [Get-VBRAzureComputeBackup](get-vbrazurecomputebackup.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of a backup copy job. The cmdlet will create the job with this name. | String | False | Named | False |
| Description | Specifies a description of a backup copy job. The cmdlet will create the job with this description. | String | False | Named | False |
| Repository | Specifies a target backup repository. The cmdlet will copy Azure backups to this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| RecoveryPointObjective | Specifies a backup copy interval. The cmdlet will copy new restore points of Azure IaaS backup copy jobs to the target backup repository. | Accepts the VBRRecoveryPointObjective object. To create this object, run the [New-VBRRecoveryPointObjective](new-vbrrecoverypointobjective_azure.md) cmdlet. | False | Named | False |
| RetentionPolicy | Specifies a number of restore points to keep on a target backup repository. | Accepts the VBRRetentionPolicy object. To get this object, run the following cmdlets:   * [New-VBRGFSRetentionPolicy](new-vbrgfsretentionpolicy_azure.md) * [New-VBRSimpleRetentionPolicy](new-vbrsimpleretentionpolicy_azure.md) | False | Named | False |
| BackupWindowOptions | Specifies the period of time when a backup copy job is allowed to run. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAzureComputeBackupCopyJob object that contains an array of Azure IaaS backup copy jobs.

Examples

Creating Azure Backup Copy Job

This example shows how to create an Azure backup copy job.

|  |
| --- |
| $backup = Get-VBRAzureComputeBackup -Name "November report"  Add-VBRAzureComputeBackupCopyJob -Backup $backup |

Perform the following steps:

1. Run the [Get-VBRAzureComputeBackup](get-vbrazurecomputebackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the Add-VBRAzureComputeBackupCopyJob cmdlet. Set the $backup variable as the Backup parameter value.

Related Commands

[Get-VBRAzureComputeBackup](get-vbrazurecomputebackup.md)

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
