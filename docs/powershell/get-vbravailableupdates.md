---
title: "Get-VBRAvailableUpdates"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbravailableupdates.html"
last_updated: "8/4/2025"
product_version: "13.0.1.1071"
---

# Get-VBRAvailableUpdates


Short Description

Returns available software updates.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAvailableUpdates [-ServerName <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns all available software updates for a server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ServerName | Specifies the server you want to view available updates for. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRAvailableUpdates

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Available Updates For All Servers

|  |  |
| --- | --- |
| This command returns available software updates for all servers.  |  | | --- | | Get-VBRAvailableUpdates | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Available Updates For Specific Server

|  |  |
| --- | --- |
| This command returns available software updates for the server example.server.local.  |  | | --- | | Get-VBRAvailableUpdates -ServerName "example.server.local" | |

Related Commands

[Install-VBRAvailableUpdates](install-vbravailableupdates.md)


