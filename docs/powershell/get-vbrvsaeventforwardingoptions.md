---
title: "Get-VBRVSAEventForwardingOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvsaeventforwardingoptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRVSAEventForwardingOptions


Short Description

Returns Veeam Software Appliance syslog event forwarding settings.

Applies to

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRVSAEventForwardingOptions  [<CommonParameters>] |

Detailed Description

This cmdlet returns the current Veeam Software Appliance syslog event forwarding settings. The settings include the target syslog server, transport protocol, severity rules, and per-application filtering rules.

Parameters

This cmdlet does not take parameters.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRVSAEventForwardingOptions](vbrvsaeventforwardingoptions.md)

Examples

Getting Veeam Software Appliance Event Forwarding Settings

This command returns the current Veeam Software Appliance syslog event forwarding settings.

|  |
| --- |
| Get-VBRVSAEventForwardingOptions |

Related Commands

* [Set-VBRVSAEventForwardingOptions](set-vbrvsaeventforwardingoptions.md)

Page updated 2026-05-27

