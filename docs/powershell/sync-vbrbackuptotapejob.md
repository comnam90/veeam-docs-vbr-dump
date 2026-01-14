---
title: "Sync-VBRBackupToTapeJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrbackuptotapejob.html"
last_updated: "7/16/2025"
product_version: "13.0.1.1071"
---

# Sync-VBRBackupToTapeJob

In this article

Short Description

Starts an active full for a selected GFS backup to tape job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create active full for weekly media set.

|  |
| --- |
| Sync-VBRBackupToTapeJob -Job <VBRBackupToTapeJob> -Weekly [-Wait]  [<CommonParameters>] |

* Create active full for monthly media set.

|  |
| --- |
| Sync-VBRBackupToTapeJob -Job <VBRBackupToTapeJob> -Monthly [-Wait]  [<CommonParameters>] |

* Create active full for quarterly media set.

|  |
| --- |
| Sync-VBRBackupToTapeJob -Job <VBRBackupToTapeJob> -Quarterly [-Wait]  [<CommonParameters>] |

* Create active full for yearly media set.

|  |
| --- |
| Sync-VBRBackupToTapeJob -Job <VBRBackupToTapeJob> -Yearly [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet starts an active full for a selected backup period of a GFS backup to tape job. The job must be targeted to a GFS media pool.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the backup to tape job for which you want to create an active full. | Accepts the [VBRBackupToTapeJob](vbrbackuptotapejob.md) object. To get this object, run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | Named | True (ByValue) |
| Weekly | Defines that the job will create a weekly full. | SwitchParameter | True | Named | False |
| Monthly | Defines that the job will create a monthly full. | SwitchParameter | True | Named | False |
| Quarterly | Defines that the job will create a quarterly full. | SwitchParameter | True | Named | False |
| Yearly | Defines that the job will create a yearly full. | SwitchParameter | True | Named | False |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting Weekly Active Full Backup for GFS Backup to Tape Job

This example shows how to start an active weekly full backup for the WebApp Backup GFS job.

|  |
| --- |
| $job = Get-VBRTapeJob -Name "WebApp Backup"  Sync-VBRBackupToTapeJob -Job $job -Weekly |

Perform the following steps:

1. Run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Sync-VBRBackupToTapeJob cmdlet. Set the $job variable as the Job parameter value. Provide the Weekly parameter.

Related Commands

[Get-VBRTapeJob](get-vbrtapejob.md)

Page updated 7/16/2025

Page content applies to build 13.0.1.1071
