---
title: "Stop-VBRVMRestoreToGoogleCloud"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrvmrestoretogooglecloud.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRVMRestoreToGoogleCloud


Short Description

Stops running restore to Google Compute Engine sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRVMRestoreToGoogleCloud -Session <VBRGoogleCloudRestoreSession> [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet stops specified restore to Google Compute Engine sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore to Google Compute Engine session. | Accepts the VBRGoogleCloudRestoreSession object. To get this object, run the [Get-VBRGoogleCloudRestoreSession](get-vbrgooglecloudrestoresession.md) cmdlet. | True | Named | True (ByValue) |
| Wait | Defines that the command will wait for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudRestoreSession](vbrgooglecloudrestoresession.md)

Examples

Stopping Session of Machine Restore to Google Compute Engine

This example shows how to stop the New session restore session.

|  |
| --- |
| $session = Get-VBRGoogleCloudRestoreSession -Session "New session"  Stop-VBRVMRestoreToGoogleCloud -Session $session |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudRestoreSession](get-vbrgooglecloudrestoresession.md) cmdlet. Specify the Session parameter value. Save the result to the $session variable.
2. Run the Stop-VBRVMRestoreToGoogleCloud cmdlet. Set the $session variable as the Session parameter value.

Related Commands

[Get-VBRGoogleCloudRestoreSession](get-vbrgooglecloudrestoresession.md)


