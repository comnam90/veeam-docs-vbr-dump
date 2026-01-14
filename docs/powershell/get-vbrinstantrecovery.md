---
title: "Get-VBRInstantRecovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrinstantrecovery.html"
last_updated: "1/23/2024"
product_version: "13.0.1.1071"
---

# Get-VBRInstantRecovery

In this article

Short Description

Returns running Instant Recovery sessions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRInstantRecovery [-Id <guid[]>] [-Full]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Instant Recovery (including Instant Recovery for first class disks, file shares and so on) sessions running at the moment. If you do not specify cmdlet parameters, the cmdlet will return all running Instant Recovery sessions.

You can get the information about the Instant Recovery sessions in short or detailed view.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies IDs of Instant Recovery sessions that you want to return.  Tip: You can find the session ID in an object returned by the cmdlet that launched the Instant Recovery session. | Guid[] | False | Named | True (ByPropertyName) |
| Full | Specifies the information on sessions and history returned in detailed view. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the InstantRecovery[] object that defines settings of Instant Recovery sessions.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Instant Recovery Sessions in Short View

|  |  |
| --- | --- |
| This command gets the list of the instant recovery sessions in short view.  |  | | --- | | Get-VBRInstantRecovery | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Instant Recovery Sessions in Detailed View

|  |  |
| --- | --- |
| This command gets the list of the instant recovery sessions in detailed view.  |  | | --- | | Get-VBRInstantRecovery -Full | |

Page updated 1/23/2024

Page content applies to build 13.0.1.1071
