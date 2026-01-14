---
title: "Sync-VBRBackupCopyJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrbackupcopyjob.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Sync-VBRBackupCopyJob

In this article

Short Description

Starts a backup copy job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-VBRBackupCopyJob -Job <IJob> [-FullBackup] [-ImmediateCopyLastRestorePoint]  [<CommonParameters>] |

Detailed Description

This cmdlet starts a backup copy job.

By default, the backup copy job runs continuously synchronizing the backup repositories in user-defined time periods. You can also use this cmdlet to synchronize the source and the target repositories manually.

|  |
| --- |
| Important |
| If you start a backup copy job in the periodic copy mode, the cmdlet will copy the latest source restore point according to schedule specified in backup copy job settings. To run the cmdlet, you must provide either the ImmediateCopyLastRestorePoint or FullBackup parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the backup copy job. The cmdlet will start this job. | Accepts string or the IJob object. To get this object, run the [Get-VBRJobs](get-vbrjob.md) cmdlet. | True | Named | True (ByValue, |
| FullBackup | Defines that the job will create an active full backup. | SwitchParameter | False | Named | False |
| ImmediateCopyLastRestorePoint | Defines that the cmdlet will enable the immediate copy mode.  If you specify this parameter, Veeam Backup & Replication will copy only the latest restore point for each source job.  Otherwise, Veeam Backup & Replication will copy all restore points created by the source jobs that were not copied since the last backup copy job session. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Backup Copy Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to start the backup copy job using variable.  |  | | --- | | $copyjob = Get-VBRJob -Name "AD Backup Copy"  Sync-VBRBackupCopyJob -Job $copyjob |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $copyjob variable. 2. Run the Sync-VBRBackupCopyJob cmdlet. Set the $copyjob variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Backup Copy Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to start the backup copy job using pipeline.  |  | | --- | | Get-VBRJob -Name "AD Backup Copy" | Sync-VBRBackupCopyJob |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Sync-VBRBackupCopyJob cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Starting Backup Copy Job and Creating Active Full Backup

|  |  |
| --- | --- |
| This example shows how to start the backup copy job and create an active full backup for the AD Job backup copy job.  |  | | --- | | $copyjob = Get-VBRJob -Name "AD Job"  Sync-VBRBackupCopyJob -Job $copyjob -FullBackup |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $copyjob variable. 2. Run the Sync-VBRBackupCopyJob cmdlet. Set the $copyjob variable as the Job parameter value. Provide the FullBackup parameter. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 4/24/2024

Page content applies to build 13.0.1.1071
