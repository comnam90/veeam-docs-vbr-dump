---
title: "Stop-VBRVMRestoreToAmazon"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrvmrestoretoamazon.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRVMRestoreToAmazon

In this article

Short Description

Stops running restore to Amazon EC2 sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRVMRestoreToAmazon -Session <VBRAmazonRestoreSession> [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet stops specified restore to Amazon EC2 sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the active restore to Amazon EC2 session that you want to stop. | Accepts the VBRAmazonRestoreSession object. To get this object, run the [Get-VBRAmazonRestoreSession](get-vbramazonrestoresession.md) cmdlet. | True | Named | True (ByValue) |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Active Restore Session to Amazon EC2

This example shows how to stop active restore session to Amazon EC2.

|  |
| --- |
| $session = Get-VBRAmazonRestoreSession -Session "New session"  Stop-VBRVMRestoreToAmazon -Session $session |

Perform the following steps:

1. Run the [Get-VBRAmazonRestoreSession](get-vbramazonrestoresession.md) cmdlet. Specify the Session parameter value. Save the result to the $session variable.
2. Run the Stop-VBRVMRestoreToAmazon cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VBRAmazonRestoreSession](get-vbramazonrestoresession.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
