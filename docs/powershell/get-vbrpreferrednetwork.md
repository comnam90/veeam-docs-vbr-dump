---
title: "Get-VBRPreferredNetwork"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrpreferrednetwork.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRPreferredNetwork

In this article

Short Description

Returns preferred networks.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRPreferredNetwork  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of preferred networks created for the backup infrastructure.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRPreferredNetwork](vbrpreferrednetwork.md)

Examples

Getting Preferred Networks

This command returns preferred networks created for the backup infrastructure.

|  |
| --- |
| Get-VBRPreferredNetwork  IpAddress                               SubnetMask                              CIDRNotation  192.168.0.1                             255.255.255.255                         192.168.0.1/32  123.0.0.0                               255.0.0.0                               123.0.0.0/8 |

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
