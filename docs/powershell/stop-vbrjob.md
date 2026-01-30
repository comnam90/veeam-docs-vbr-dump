---
title: "Stop-VBRJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrjob.html"
last_updated: "12/16/2025"
product_version: "13.0.1.1071"
---

# Stop-VBRJob


Short Description

Stops a running backup, replication or copy job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRJob -Job <CBackupJob[]> [-Gracefully] [-RunAsync] [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet stops a running backup, replication or tape job. The job is stopped once, the scheduled job will start the next scheduled time.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start the job manually.

Run the [Disable-VBRJob](disable-vbrjob.md) cmdlet to temporarily disable a job.

Run the [Stop-VSBJob](stop-vsbjob.md) cmdlet to stop a SureBackup job.

Run the [Stop-VBRComputerBackupJob](stop-vbrcomputerbackupjob.md) cmdlet to stop Veeam Agent backup jobs and Veeam Agent backup policies.

Run the [Stop-VBRBackupCopyJob](stop-vbrbackupcopyjob.md) cmdlet to stop a backup copy job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs you want to stop. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) or [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |
| RunAsync | Defines that the command will return immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Gracefully | Defines that the cmdlet will stop a job gracefully. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Stopping Specific Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to stop the SharePoint File Copy Job copy job.  |  | | --- | | Get-VBRJob -Name "SharePoint File Copy Job" | Stop-VBRJob |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Stop-VBRJob cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Stopping Specific Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to stop the copy job represented by the $SharePointFileCopyJob variable.  |  | | --- | | $SharePointFileCopyJob = Get-VBRJob -Name "SharePoint File Copy Job"  Stop-VBRJob -Job $SharePointFileCopyJob |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $SharePointFileCopyJob variable. 2. Run the Stop-VBRJob cmdlet. Set the $SharePointFileCopyJob variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)


