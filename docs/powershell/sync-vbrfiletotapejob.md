---
title: "Sync-VBRFileToTapeJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrfiletotapejob.html"
last_updated: "7/16/2025"
product_version: "13.0.1.1071"
---

# Sync-VBRFileToTapeJob


Short Description

Starts an active full for a selected GFS file to tape job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create active full for weekly media set.

|  |
| --- |
| Sync-VBRFileToTapeJob -Job <VBRFileToTapeJob> -Weekly [-Wait]  [<CommonParameters>] |

* Create active full for monthly media set.

|  |
| --- |
| Sync-VBRFileToTapeJob -Job <VBRFileToTapeJob> -Monthly [-Wait]  [<CommonParameters>] |

* Create active full for quarterly media set.

|  |
| --- |
| Sync-VBRFileToTapeJob -Job <VBRFileToTapeJob> -Quarterly [-Wait]  [<CommonParameters>] |

* Create active full for yearly media set.

|  |
| --- |
| Sync-VBRFileToTapeJob -Job <VBRFileToTapeJob> -Yearly [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet starts an active full for a selected backup period of a GFS file to tape job. The job must be targeted to a GFS media pool.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the GFS file to tape job for which you want to create an active full. | Accepts the [VBRFileToTapeJob](vbrfiletotapejob.md) object. To get this object, run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | Named | True (ByValue) |
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

Starting Weekly Active Full Backup for GFS File to Tape Job

This example shows how to start an active weekly full backup for the File Share Backup GFS file to tape job.

|  |
| --- |
| $job = Get-VBRTapeJob -Name "File Share Backup"  Sync-VBRFileToTapeJob -Job $job -Weekly |

Perform the following steps:

1. Run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Sync-VBRFileToTapeJob cmdlet. Set the $job variable as the Job parameter value. Provide the Weekly parameter.

Related Commands

[Get-VBRTapeJob](get-vbrtapejob.md)


