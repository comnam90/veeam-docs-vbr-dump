---
title: "Add-VBRTapeVault"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrtapevault.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Add-VBRTapeVault


Short Description

Creates a tape vault.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRTapeVault -Name <String> [-Description <String>] [-Protect]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new tape vault.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the vault. | String | True | Named | False |
| Description | Specifies the description of the vault. | String | False | Named | False |
| Protect | Defines that all tapes moved to this media vault automatically get lifelong overwrite protection. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeVault](vbrtapevault.md)

Examples

Creating Tape Vault

This command creates a vault named Sydney Remote Storage.

|  |
| --- |
| Add-VBRTapeVault -Name "Sydney Remote Storage" -Description "Veeam backups offsite" |


