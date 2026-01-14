---
title: "Get-VBRPluginRestoreSession"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrpluginrestoresession_standalone.html"
last_updated: "5/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRPluginRestoreSession

In this article

Short Description

Returns active restore sessions for standalone and managed Veeam Plug-ins.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all active restore sessions for standalone and managed Veeam Plug-ins.

|  |
| --- |
| Get-VBRPluginRestoreSession  [<CommonParameters>] |

* Get active restore sessions by the session ID.

|  |
| --- |
| Get-VBRPluginRestoreSession [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns active restore sessions for standalone and managed Veeam Plug-ins.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies the array of restore sessions for standalone and managed Veeam Plug-ins. The cmdlet will return the sessions with these IDs. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRPluginRestoreSession](vbrpluginrestoresession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Active Restore Sessions

|  |  |
| --- | --- |
| This command returns all active restore sessions for standalone and managed Veeam Plug-ins.  |  | | --- | | Get-VBRPluginRestoreSession | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Active Restore Sessions by ID

|  |  |
| --- | --- |
| This command returns the ebea2113-dacb-4f5f-ac2a-18794fb6d4aa session.  |  | | --- | | Get-VBRPluginRestoreSession -Id ebea2113-dacb-4f5f-ac2a-18794fb6d4aa | |

Page updated 5/29/2024

Page content applies to build 13.0.1.1071
