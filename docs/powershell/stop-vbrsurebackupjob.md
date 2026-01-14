---
title: "Stop-VBRSureBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrsurebackupjob.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRSureBackupJob

In this article

Short Description

Stops the SureBackup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRSureBackupJob -Job <VBRSureBackupJobBase> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet stops the SureBackup job.

Run the [Start-VBRSureBackupJob](start-vbrsurebackupjob.md) cmdlet to start the SureBackup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a SureBackup job. The cmdlet will stop that job. | Accepts the VBRSureBackupJobBase object. To create this object, run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. | True | Named | True (ByValue, |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParamter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParamter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Stopping SureBackup Job

This example shows how to stop a SureBackup Job.

|  |
| --- |
| $job = Get-VBRSureBackupJob -Name "SureJob 2"  Stop-VBRSureBackupJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Stop-VBRSureBackupJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRSureBackupJob](get-vbrsurebackupjob.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
