---
title: "Disconnect-VBRServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disconnect-vbrserver.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Disconnect-VBRServer


Short Description

Ends current session with a Veeam backup server.

Syntax

|  |
| --- |
| Disconnect-VBRServer  [<CommonParameters>] |

Detailed Description

This cmdlet ends the current local or remote session with a Veeam backup server.

Run the [Connect-VBRServer](connect-vbrserver.md) cmdlet to start the session again.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

This command terminates the current connection to a Veeam backup server.

|  |
| --- |
| Disconnect-VBRServer |


