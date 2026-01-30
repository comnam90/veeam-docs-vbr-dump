---
title: "Get-VBRLocalhost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrlocalhost.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---

# Get-VBRLocalhost


Short Description

Returns the local server on which the backup infrastructure is installed.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRLocalhost  [<CommonParameters>] |

Detailed Description

This cmdlet returns the local server on which the backup infrastructure is installed.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Example

This command looks for the local backup infrastructure server.

|  |
| --- |
| Get-VBRLocalhost |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Remove-VBRServer](remove-vbrserver.md)


