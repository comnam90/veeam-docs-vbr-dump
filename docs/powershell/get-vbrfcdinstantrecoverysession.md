---
title: "Get-VBRFCDInstantRecoverySession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrfcdinstantrecoverysession.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Get-VBRFCDInstantRecoverySession

In this article

Short Description

Returns an array of FCD recovery sessions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRFCDInstantRecoverySession [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlets returns an array of sessions that are running to perform FCD recovery.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of session IDs that are running to perform FCD recovery. The cmdlet will return recovery sessions with these IDs. | Guid[] | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRFCDInstantRecoverySession[] object that contains an array of sessions that are running to perform FCD recovery.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Sessions Running to Perform FCD Recovery

|  |  |
| --- | --- |
| This command returns all sessions that are running to perform FCD recovery.  |  | | --- | | Get-VBRFCDInstantRecoverySession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Sessions Running to Perform FCD Recovery

|  |  |
| --- | --- |
| This command returns the sessions that are running to perform FCD recovery with the following IDs: 49664A5F-9C55-4A1F-8E6A-1CD5705A684B and 42696B53-6FEC-4148-9354-AA9E4B52DED9.  |  | | --- | | Get-VBRFCDInstantRecoverySession -Id "49664A5F-9C55-4A1F-8E6A-1CD5705A684B", "42696B53-6FEC-4148-9354-AA9E4B52DED9" | |

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
