---
title: "Sync-VBRObjectToTapeJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrobjecttotapejob.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# Sync-VBRObjectToTapeJob

In this article

Short Description

Starts an active full for a selected GFS object to tape job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create active full for weekly media set.

|  |
| --- |
| Sync-VBRObjectToTapeJob -Job <VBRObjectToTapeJob> [-Weekly] [-Wait]  [<CommonParameters>] |

* Create active full for monthly media set.

|  |
| --- |
| Sync-VBRObjectToTapeJob -Job <VBRObjectToTapeJob> [-Monthly] [-Wait]  [<CommonParameters>] |

* Create active full for quarterly media set.

|  |
| --- |
| Sync-VBRObjectToTapeJob -Job <VBRObjectToTapeJob> [-Quarterly] [-Wait]  [<CommonParameters>] |

* Create active full for yearly media set.

|  |
| --- |
| Sync-VBRObjectToTapeJob -Job <VBRObjectToTapeJob> [-Yearly] [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet starts an active full for a selected backup period of a GFS object to tape job. The job must be targeted to a GFS media pool.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the GFS object to tape job for which you want to create an active full. | Accepts the [VBRObjectToTapeJob](vbrobjecttotapejob.md) object. To create this object, run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | Named | True (ByValue) |
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

Starting Weekly Active Full Backup for GFS Object to Tape Job

This example shows how to start an active weekly full backup for the Sydney Container to Tape GFS object to tape job.

|  |
| --- |
| $job = Get-VBRTapeJob -Name "Sydney Container to Tape"  Sync-VBRObjectToTapeJob -Job $job -Weekly |

Perform the following steps:

1. Run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Sync-VBRObjectToTapeJob cmdlet. Set the $job variable as the Job parameter value. Provide the Weekly parameter.

Related Commands

[Get-VBRTapeJob](get-vbrtapejob.md)

Page updated 9/3/2025

Page content applies to build 13.0.1.1071
