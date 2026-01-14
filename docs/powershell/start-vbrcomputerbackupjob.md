---
title: "Start-VBRComputerBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcomputerbackupjob.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Start-VBRComputerBackupJob

In this article

Short Description

Starts Veeam Agent backup jobs and Veeam Agent backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRComputerBackupJob -Job <VBRComputerBackupJob[]> [-FullBackup] [-RetryBackup] [-Object <VBRDiscoveredComputer[]>] [-StartChainedJobs] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts Veeam Agent backup jobs and Veeam Agent backup policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a Veeam Agent backup job or a Veeam Agent backup policy that you want to start. | Accepts the VBRComputerBackupJob[] object. To get this object, run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| FullBackup | Defines that the Veeam Agent backup job will create an active full backup. | SwitchParameter | False | Named | False |
| RetryBackup | Defines that Veeam Backup & Replication will restart the failed job. The cmdlet will start the job from the moment when it has failed. | SwitchParameter | False | Named | False |
| Object | Specifies an array of protected machines. | Accepts the VBRDiscoveredComputer[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | False  Named  False |  |  |
| StartChainedJobs | Defines that Veeam Backup & Replication will start jobs that are scheduled to run after this the Veeam Agent backup job. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the [VBRSession](vbrsession.md)[] object that contains settings of running Veeam Agent backup jobs and of Veeam Agent backup policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Veeam Agent Backup Job

|  |  |
| --- | --- |
| This example shows how to start the Veeam Agent backup job.  |  | | --- | | $job = Get-VBRComputerBackupJob -Name "WinSrv2049"  Start-VBRComputerBackupJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Start-VBRComputerBackupJob cmdlet. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Full Backup by Veeam Agent Backup Job

|  |  |
| --- | --- |
| This example shows how to create an active full backup by the Veeam Agent backup job.  |  | | --- | | $job = Get-VBRComputerBackupJob -Name "WinSrv2049"  Start-VBRComputerBackupJob -Job $job -FullBackup |  Perform the following steps:   1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Start-VBRComputerBackupJob cmdlet. Set the $job variable as the Job parameter value. Provide the FullBackup parameter. |

Related Commands

[Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
