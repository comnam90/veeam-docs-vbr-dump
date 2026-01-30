---
title: "Set-VBRAzureComputeBackupCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrazurecomputebackupcopyjob.html"
last_updated: "1/24/2024"
product_version: "13.0.1.1071"
---

# Set-VBRAzureComputeBackupCopyJob


Short Description

Modifies Azure IaaS backup copy jobs.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAzureComputeBackupCopyJob -Job <CBackupJob> [-Name <string>] [-Description <string>] [-Backup <VBRAzureComputeBackup[]>] [-Repository <CBackupRepository>] [-RecoveryPointObjective <VBRRecoveryPointObjective>] [-RetentionPolicy <VBRRetentionPolicy>] [-BackupWindowOptions <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies Azure IaaS backup copy jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an Azure backup copy job. The cmdlet will modify this job. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of a backup copy job. The cmdlet will create the job with this name. | String | False | Named | False |
| Description | Specifies a description of a backup copy job. The cmdlet will create the job with this description. | String | False | Named | False |
| Backup | Specifies an array of Azure backups that you want to copy. | Accepts the VBRAzureComputeBackup[] object. To get this object, run the [Get-VBRAzureComputeBackup](get-vbrazurecomputebackup.md) cmdlet. | False | Named | False |
| Repository | Specifies a target backup repository. The cmdlet will copy Azure backups to this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| RecoveryPointObjective | Specifies a backup copy interval. The cmdlet will copy new restore points of Azure IaaS backup copy jobs to the target backup repository. | Accepts the VBRRecoveryPointObjective object. To create this object, run the [New-VBRRecoveryPointObjective](new-vbrrecoverypointobjective_azure.md) cmdlet. | False | Named | False |
| RetentionPolicy | Specifies a number of restore points to keep on a target backup repository. | Accepts the VBRRetentionPolicy object. To get this object, run the following cmdlets:   * [New-VBRGFSRetentionPolicy](new-vbrgfsretentionpolicy_azure.md) * [New-VBRSimpleRetentionPolicy](new-vbrsimpleretentionpolicy_azure.md) | False | Named | False |
| BackupWindowOptions | Specifies the period of time when a backup copy job is allowed to run. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAzureComputeBackupCopyJob object that contains an array of Azure IaaS backup copy jobs.

Examples

Modifying Backup Repository of Azure Backup Copy Job

This example shows how to modify a backup repository of an Azure backup copy job.

|  |
| --- |
| $copyjob = Get-VBRJob -Name "Azure backup copy"  $repository = Get-VBRBackupRepository  Set-VBRAzureComputeBackupCopyJob -Job $copyjob -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $copyjob variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $repository variable.
3. Run the Set-VBRAzureComputeBackupCopyJob cmdlet. Set the $copyjob variable as the Job parameter value. Set the $repository variable as the Repository parameter value.

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


