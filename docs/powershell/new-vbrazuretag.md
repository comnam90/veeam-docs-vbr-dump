---
title: "New-VBRAzureTag"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrazuretag.html"
last_updated: "1/22/2024"
product_version: "13.0.1.1071"
---

# New-VBRAzureTag

In this article

Short Description

Defines Azure metadata tags.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAzureTag -Key <string> -Value <string>  [<CommonParameters>] |

Detailed Description

This cmdlet defines the [VBRAzureTag](vbrazuretag.md) object. This object contains Azure metadata tags.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Key | Specifies a key for the Azure metadata tag. The cmdlet will create the cmdlet with the specified key. | String | True | Named | False |
| Value | Specifies a value for the the Azure metadata tag. The cmdlet will create the cmdlet with the specified value. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureTag](vbrazuretag.md)

Examples

Defining Azure MetadataTags

This command defines Azure metadata tags.

|  |
| --- |
| New-VBRAzureTag -Key Critically -Value High |

Page updated 1/22/2024

Page content applies to build 13.0.1.1071
