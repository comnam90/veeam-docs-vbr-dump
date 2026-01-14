---
title: "Get-VBRLinuxTrustedHostPolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrlinuxtrustedhostpolicy.html"
last_updated: "1/17/2025"
product_version: "13.0.1.1071"
---

# Get-VBRLinuxTrustedHostPolicy

In this article

Short Description

Returns the trust policy for Linux hosts.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRLinuxTrustedHostPolicy  [<CommonParameters>] |

Detailed Description

This cmdlet returns the trust policy that is set for Linux hosts.

The trust policy determines which protected computers running Linux OS are allowed to connect to the backup server:

* All: with this policy, the connection is allowed for all newly discovered Linux hosts.
* KnownHosts: with this policy, the connection is allowed only for trusted Linux hosts.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRLinuxTrustedHostPolicy](vbrlinuxtrustedhostpolicy.md)

Examples

Getting Trust Policy for Linux Hosts

This command returns the trust policy that is set for Linux hosts.

|  |
| --- |
| Get-VBRLinuxTrustedHostPolicy |

Page updated 1/17/2025

Page content applies to build 13.0.1.1071
