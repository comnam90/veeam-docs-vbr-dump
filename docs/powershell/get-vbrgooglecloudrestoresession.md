---
title: "Get-VBRGoogleCloudRestoreSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudrestoresession.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudRestoreSession

In this article

Short Description

Returns restore to Google Cloud sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGoogleCloudRestoreSession [-Session <VBRGoogleCloudRestoreSession>] [-Id <guid>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore to Google Cloud sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies restore session name. | Accepts the [VBRGoogleCloudRestoreSession](vbrgooglecloudrestoresession.md) object. To create this object, run the [Start-VBRVMRestoreToGoogleCloud](start-vbrvmrestoretogooglecloud.md) cmdlet. | False | Named | False |
| Id | Specifies restore session ID. | Guid | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudRestoreSession](vbrgooglecloudrestoresession.md)

Examples

Getting Session of Machine Restore to Google Compute Engine

This command gets the New session restore session.

|  |
| --- |
| Get-VBRGoogleCloudRestoreSession -Session "New session" |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
