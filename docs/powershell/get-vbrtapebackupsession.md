---
title: "Get-VBRTapeBackupSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapebackupsession.html"
last_updated: "3/21/2024"
product_version: "13.0.1.1071"
---

# Get-VBRTapeBackupSession


Short Description

Returns tape backup job sessions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get tape backup sessions with certain IDs.

|  |
| --- |
| Get-VBRTapeBackupSession [-Id <Guid[]>]  [<CommonParameters>] |

* Get tape backup sessions run for a certain tape backup job.

|  |
| --- |
| Get-VBRTapeBackupSession [-Job <VBRTapeJob>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns tape backup job sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of tape backup session IDs. The cmdlet will return tape backup sessions with these IDs. | Guid[] | False | Named | False |
| Job | Specifies a tape backup job. The cmdlet will return tape backup sessions run for this tape backup job. | Accepts the VBRTapeJob object. To create this object, run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRTapeBackupSession object that defines the tape backup job session with the following attributes: Progress, RunManually, Log, Initiator, CreationTime, EndTime, JobId, Result, State, Id.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Tape Backup Sessions with Certain IDs

|  |  |
| --- | --- |
| This example shows how to get tape backup sessions with certain IDs.  |  | | --- | | Get-VBRTapeBackupSession -Id ("49664A5F-9C55-4A1F-8E6A-1CD5705A684B", "42696B53-6FEC-4148-9354-AA9E4B52DED9") | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Tape Backup Sessions for Certain Tape Backup Job

|  |  |
| --- | --- |
| This example shows how to get tape backup sessions run for a certain tape backup job.  |  | | --- | | $tapejob = Get-VBRTapeJob -Name "Payroll Reports to Tape (Q1-Q2)"  Get-VBRTapeBackupSession -Job $tapejob |  Perform the following steps:   1. Run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. Specify the Name parameter value. Save the result to the $tapejob variable. 2. Run the Get-VBRTapeBackupSession cmdlet. Set the $tapejob variable as the Job parameter value. |

Related Commands

[Get-VBRTapeJob](get-vbrtapejob.md)


