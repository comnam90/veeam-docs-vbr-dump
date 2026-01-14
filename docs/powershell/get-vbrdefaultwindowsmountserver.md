---
title: "Get-VBRDefaultWindowsMountServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdefaultwindowsmountserver.html"
last_updated: "7/22/2025"
product_version: "13.0.1.1071"
---

# Get-VBRDefaultWindowsMountServer

In this article

Short Description

Returns the default Windows mount server.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRDefaultWindowsMountServer  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRDefaultWindowsMountServer object which contains the default Windows mount server and its settings.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDefaultWindowsMountServer](vbrdefaultwindowsmountserver.md)

Examples

Getting Default Windows Mount Server

This command returns the default Windows mount server.

|  |
| --- |
| Get-VBRDefaultWindowsMountServer |

Page updated 7/22/2025

Page content applies to build 13.0.1.1071
