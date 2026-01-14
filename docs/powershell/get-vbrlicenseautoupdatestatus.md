---
title: "Get-VBRLicenseAutoUpdateStatus"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrlicenseautoupdatestatus.html"
last_updated: "2/5/2024"
product_version: "13.0.1.1071"
---

# Get-VBRLicenseAutoUpdateStatus

In this article

Short Description

Returns a state of the automatic license update option.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRLicenseAutoUpdateStatus  [<CommonParameters>] |

Detailed Description

This cmdlet returns a state of the automatic license update option.

* False - indicates that the automatic license update option is disabled.
* True - indicates that the automatic license update option is enabled.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Getting State of Automatic License Update Option

This command returns a state of the automatic license update option.

|  |
| --- |
| Get-VBRLicenseAutoUpdateStatus  True |

Page updated 2/5/2024

Page content applies to build 13.0.1.1071
