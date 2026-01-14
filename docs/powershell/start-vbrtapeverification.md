---
title: "Start-VBRTapeVerification"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrtapeverification.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Start-VBRTapeVerification

In this article

Short Description

Starts tape verification jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRTapeVerification -Medium <VBRTapeMedium[]>  [<CommonParameters>] |

Detailed Description

This cmdlet starts tape verification jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Medium | Specifies an array of tapes. The cmdlet will add this array of tapes to the tape verification job. | Accepts the [VBRTapeMedium[]](vbrtapemedium.md) object. To get this object, run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupSession object that defines the started tape verification jobs with the following details: Progress, RunManually flag, Log path, CreationTime, EndTime, JobId, Result, State, and the tape session Id.

Examples

Starting Tape Verification Job

This example shows how to start a tape verification job that will check data that is stored on the 0021000C tape.

|  |
| --- |
| $tape = Get-VBRTapeMedium -Name "0021000C"  Start-VBRTapeVerification -Medium $tape |

Perform the following steps:

1. Run the [Get-VBRTapeMedium](get-vbrtapemedium.md) cmdlet. Specify the Name parameter value. Save the result to the $tape variable.
2. Run the Start-VBRTapeVerification cmdlet. Set the $tape variable as the Medium parameter value.

Related Commands

[Get-VBRTapeMedium](get-vbrtapemedium.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
