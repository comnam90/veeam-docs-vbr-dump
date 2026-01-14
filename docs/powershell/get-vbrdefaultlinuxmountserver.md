---
title: "Get-VBRDefaultLinuxMountServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdefaultlinuxmountserver.html"
last_updated: "7/22/2025"
product_version: "13.0.1.1071"
---

# Get-VBRDefaultLinuxMountServer

In this article

Short Description

Returns the default Linux mount server.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRDefaultLinuxMountServer  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRDefaultLinuxMountServer object which contains the default Linux mount server and its settings.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDefaultLinuxMountServer](vbrdefaultlinuxmountserver.md)

Examples

Getting Default Linux Mount Server

This command returns the default Linux mount server.

|  |
| --- |
| Get-VBRDefaultLinuxMountServer |

Page updated 7/22/2025

Page content applies to build 13.0.1.1071
