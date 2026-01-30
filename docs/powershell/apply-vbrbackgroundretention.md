---
title: "Apply-VBRBackgroundRetention"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/apply-vbrbackgroundretention.html"
last_updated: "7/25/2025"
product_version: "13.0.1.1071"
---

# Apply-VBRBackgroundRetention


Short Description

Performs background retention for backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Apply-VBRBackgroundRetention  [<CommonParameters>] |

Detailed Description

This cmdlet performs background retention for backups.

The Apply-VBRIndependentRetention cmdlet is an alias for the Apply-VBRBackgroundRetention cmdlet.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Performing Background Retention for Backups

This command performs background retention for backups.

|  |
| --- |
| Apply-VBRBackgroundRetention |


