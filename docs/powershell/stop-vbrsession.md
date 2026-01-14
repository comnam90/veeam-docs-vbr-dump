---
title: "Stop-VBRSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrsession.html"
last_updated: "3/13/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRSession

In this article

Short Description

Stops tape jobs sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRSession -Session <VBRSession> [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet stops running tape jobs sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a running tape job session. The cmdlet will stop this session. | Accepts the VBRSession object. To get this object, run the [Get-VBRSession](get-vbrsession.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Stopping Session for Tape Job

This example shows how to stop the session for the specified tape job.

|  |
| --- |
| $job = Get-VBRTapeJob -Name "Backup Copy Job"  $session = Get-VBRSession -Job $job  Stop-VBRSession -Session $session |

Perform the following steps:

1. Run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [Get-VBRSession](get-vbrsession.md) cmdlet. Set the $job variable as the Job parameter value. Save the result to the $session variable.
3. Run the Stop-VBRSession cmdlet. Set the $session variable as the Session parameter value.

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRSession](get-vbrsession.md)

Page updated 3/13/2024

Page content applies to build 13.0.1.1071
