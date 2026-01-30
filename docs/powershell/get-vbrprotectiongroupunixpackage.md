---
title: "Get-VBRProtectionGroupUnixPackage"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrprotectiongroupunixpackage.html"
last_updated: "4/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRProtectionGroupUnixPackage


Short Description

Returns Veeam Agents for Unix packages.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRProtectionGroupUnixPackage [-Name <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Veeam Agents for Unix packages.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of the Veeam Agents for Unix package. The cmdlet will return Unix packages with this name. | String | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRProtectionGroupUnixPackage](vbrprotectiongroupunixpackage.md) object that contains Veeam Agents for Unix packages.

Examples

Getting all Veeam Agents for Unix Packages

This command returns an array of all Veeam Agents for Unix packages.

|  |
| --- |
| Get-VBRProtectionGroupUnixPackage |


