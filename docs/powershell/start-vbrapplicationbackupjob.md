---
title: "Start-VBRApplicationBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrapplicationbackupjob.html"
last_updated: "8/16/2024"
product_version: "13.0.1.1071"
---

# Start-VBRApplicationBackupJob


Short Description

Starts application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRApplicationBackupJob [-Job] <VBRApplicationBackupJobBase[]> [-RunAsync] [-FullBackup] [-RetryBackup] [-StartChainedJobs] [<CommonParameters>] |

Detailed Description

This cmdlet starts application backup policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an application backup policy that you want to start. | Accepts the VBRApplicationBackupJobBase[] object. To get this object, run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| FullBackup | Defines that the application backup policy will create an active full backup. | SwitchParameter | False | Named | False |
| RetryBackup | Defines that Veeam Backup & Replication will restart the failed job. The cmdlet will start the job from the moment when it has failed. | SwitchParameter | False | Named | False |
| StartChainedJobs | Defines that Veeam Backup & Replication will start jobs that are scheduled to run after this job. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSession[] object that contains settings of running application backup policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Application Backup Policy

|  |  |
| --- | --- |
| This example shows how to start the application backup policy.  |  | | --- | | $job = Get-VBRApplicationBackupJob -Name "DbsSrv2049"  Start-VBRApplicationBackupJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Start-VBRApplicationBackupJob cmdlet. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Full Backup by Application Backup Policy

|  |  |
| --- | --- |
| This example shows how to create an active full backup by the application backup policy.  |  | | --- | | $job = Get-VBRApplicationBackupJob -Name "DbsSrv2049"  Start-VBRApplicationBackupJob -Job $job -FullBackup |  Perform the following steps:   1. Run the [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Start-VBRComputerBackupJob cmdlet. Set the $job variable as the Job parameter value. Specify the FullBackup parameter. |

Related Commands

[Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md)


