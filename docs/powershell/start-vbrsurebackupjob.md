---
title: "Start-VBRSureBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrsurebackupjob.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Start-VBRSureBackupJob


Short Description

Starts the SureBackup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRSureBackupJob -Job <VBRSureBackupJobBase> [-DateTime <DateTime>] [-RestorePointType <VBRSureBackupRestorePointType>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts the SureBackup job.

Run the [Stop-VBRSureBackupJob](stop-vbrsurebackupjob.md) cmdlet to stop the SureBackup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a SureBackup job. The cmdlet will start that job. | Accepts the VBRSureBackupJob object. To create this object, run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. | True | Named | True (ByValue, |
| DateTime | Specifies a restore point that is created by the SureBackup job. The cmdlet will start VMs backed up by the SureBackup job from the specified restore point.  Note: If you do not specify this parameter, the cmdlet will start VMs from the most recent restore point. | DateTime | False | Named | False |
| RestorePointType | Specifies one of the restore point types, AppConsisrent or CrashConsistent. | VBRSureBackupRestorePointType |  |  |  |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting SureBackup Jobs From Recent Restore Point

|  |  |
| --- | --- |
| This example shows how to start the Job02 SureBackup job from the most recent restore point.  |  | | --- | | $job = Get-VBRSureBackupJob -Name "Job02"  Start-VBRSureBackupJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Start-VBRSureBackupJob cmdlet. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting SureBackup Jobs From Specified Restore Point

|  |  |
| --- | --- |
| This example shows how to start the Job02 SureBackup job from the specified restore point.  |  | | --- | | $job = Get-VBRSureBackupJob -Name "Job02"  $date = Get-Date -Year 2020 -Month 2 -Day 2 -Hour 0 -Minute 0 -Second 0  Start-VBRSureBackupJob -Job $job -DateTime $date "2/20/2020" |  Perform the following steps:   1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. Specify the Year, Month, Day, Hour, Minute and Second parameter values. Save the result to the $date variable. 3. Run the Start-VBRSureBackupJob cmdlet. Set the $job variable as the Job parameter value.  Set the $date variable as the DateTime parameter value. |

Related Commands

* [Get-VBRSureBackupJob](get-vbrsurebackupjob.md)
* [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1)


