---
title: "Start-VBRJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrjob.html"
last_updated: "12/16/2025"
product_version: "13.0.1.1071"
---

# Start-VBRJob

In this article

Short Description

Starts a backup or replication job.

Applies to

Platform: VMware, Hyper-V, file shares

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRJob -Job <CBackupJob[]> [-Object <CObjectInJob[]>] [-FullBackup] [-RetryBackup] [-StartChainedJobs] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to start a created or stopped job. You can start a backup, replication or tape job.

This cmdlet allows you to start a job for an ordinary run, force a full backup, or set the job to restart in case it failed.

When you create a job, you need to run it manually unless you enable a job schedule. Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to schedule the job to run automatically.

Run the [Stop-VBRJob](stop-vbrjob.md) cmdlet to stop a running job.

Run the [Enable-VBRJob](enable-vbrjob.md) cmdlet to enable a disabled job.

Run the [Sync-VBRBackupCopyJob](sync-vbrbackupcopyjob.md) cmdlet to start a backup copy job.

Run the [Start-VBRComputerBackupJob](start-vbrcomputerbackupjob.md) cmdlet to start Veeam Agent backup jobs and Veeam Agent backup policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs you want to start. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) or [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |
| Object | Specifies an array of job objects (VMs and VM containers). The cmdlet will start jobs with these objects. | Accepts the CObjectInJob[]object. To get this object, run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. | False | Named | False |
| FullBackup | Defines that the job will create an active full backup. | SwitchParameter | False | Named | False |
| RetryBackup | Defines that Veeam Backup & Replication will restart the job in case it fails. | SwitchParameter | False | Named | False |
| StartChainedJobs | Defines that Veeam Backup & Replication will start jobs that are scheduled to run after this job. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Specific Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to start the WebApplications Server Backup and Fileserver Copy Job jobs.  |  | | --- | | Get-VBRJob -Name "WebApplications Server Backup", "Fileserver Copy Job" | Start-VBRJob |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Start-VBRJob cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Cloud Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to start a Cloud backup job right after it the job is created. The RunAsync parameter is set to bring the process to the background.  |  | | --- | | $vCloudServer = Add-VBRvCloud -Name "vCloudDirectorServer.domain.com" -User Administrator -Password password -Url "https://vclouddirectorserver:443" -Description "Cloud Director Server"  Add-VBRvCloudJob -Entity $vCloudServer -Name "vCloud Server Backup" | Start-VBRJob -RunAsync |  Perform the following steps:   1. Run the [Add-VBRvCloud](add-vbrvcloud.md) cmdlet. Specify the necessary parameters. Save the result to the $vCloudServer variable. 2. Run the [Add-VBRvCloudJob](add-vbrvcloudjob.md) cmdlet. Set the $vCloudServer variable as the Entity parameter value. Specify the Name parameter value. 3. Pipe the cmdlet output to the Start-VBRJob cmdlet. Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Performing Full Backup [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to perform a full backup for the WebApplications Server Backup job.  |  | | --- | | Get-VBRJob -Name "WebApplications Server Backup" | Start-VBRJob -FullBackup |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Start-VBRJob cmdlet. Provide the FullBackup parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Restarting Failed Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to restart a failed job represented by the $job variable. The RunAsync parameter is set to bring the process to the background.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job"  Start-VBRJob -Job $job -RetryBackup -RunAsync |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Start-VBRJob cmdlet. Specify the following settings:  * Set the $job variable as the Job parameter value. * Provide the RetryBackup parameter. * Provide the RunAsync parameter. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Add-VBRvCloud](add-vbrvcloud.md)
* [Add-VBRvCloudJob](add-vbrvcloudjob.md)

Page updated 12/16/2025

Page content applies to build 13.0.1.1071
