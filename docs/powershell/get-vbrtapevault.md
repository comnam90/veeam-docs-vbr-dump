---
title: "Get-VBRTapeVault"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapevault.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBRTapeVault


Short Description

Returns tape vaults.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all tape vaults.

|  |
| --- |
| Get-VBRTapeVault  [<CommonParameters>] |

* Get a tape vault by ID.

|  |
| --- |
| Get-VBRTapeVault [-Id <guid[]>]  [<CommonParameters>] |

* Get a tape vault by name.

|  |
| --- |
| Get-VBRTapeVault [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing tape vaults.

You can get the list of all tape vaults or search for instances directly by name or ID.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of vault names. The cmdlet will return vaults with these names. | String | False | Named | True (ByValue, ByProperty Name) |
| Id | Specifies the array of vault IDs. The cmdlet will return vaults with these IDs. | Accepts GUID or string. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeVault[]](vbrtapevault.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Tape Vaults

|  |  |
| --- | --- |
| This command looks for a list of all existing vaults.  |  | | --- | | Get-VBRTapeVault | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Tape Vault by Name

|  |  |
| --- | --- |
| This command looks for a vault named Sydney Remote Storage.  |  | | --- | | Get-VBRTapeVault -Name "Sydney Remote Storage" | |


