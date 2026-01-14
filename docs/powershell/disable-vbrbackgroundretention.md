---
title: "Disable-VBRBackgroundRetention"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrbackgroundretention.html"
last_updated: "7/25/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRBackgroundRetention

In this article

Short Description

Disables background retention for backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRBackgroundRetention  [<CommonParameters>] |

Detailed Description

This cmdlet disables background retention for backups that starts automatically every 24 hours at 00:30.

Run the [Enable-VBRBackgroundRetention](enable-vbrbackgroundretention.md) cmdlet to enable background retention policy.

The Disable-VBRIndependentRetention cmdlet is an alias for the Disable-VBRBackgroundRetention cmdlet.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Background Retention for Backups

This command disables background retention for backups.

|  |
| --- |
| Disable-VBRBackgroundRetention |

Page updated 7/25/2025

Page content applies to build 13.0.1.1071
