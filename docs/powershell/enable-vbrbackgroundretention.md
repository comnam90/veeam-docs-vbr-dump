---
title: "Enable-VBRBackgroundRetention"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrbackgroundretention.html"
last_updated: "7/25/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRBackgroundRetention


Short Description

Enables previously disabled background retention for backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRBackgroundRetention  [<CommonParameters>] |

Detailed Description

This cmdlet enables the disabled background retention for backups. Enabled background retention is launched every 24 hours at 00:30.

Run the [Disable-VBRBackgroundRetention](disable-vbrbackgroundretention.md) cmdlet to disable background retention policy.

The Enable-VBRIndependentRetention cmdlet is an alias for the Enable-VBRBackgroundRetention cmdlet.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Enabling Background Retention for Backups

This command enables background retention for backups.

|  |
| --- |
| Enable-VBRBackgroundRetention |


