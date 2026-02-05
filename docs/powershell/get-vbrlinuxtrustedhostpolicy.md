---
title: "Get-VBRLinuxTrustedHostPolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrlinuxtrustedhostpolicy.html"
last_updated: "2/4/2026"
product_version: "13.0.1.1071"
---

# Get-VBRLinuxTrustedHostPolicy


Short Description

Returns the trust policy for protected Linux and Microsoft Windows machines.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRLinuxTrustedHostPolicy  [<CommonParameters>] |

Detailed Description

This cmdlet returns the trust policy for protected machines.

The trust policy determines which protected computers are allowed to connect to the backup server:

* All: with this policy, Veeam Backup & Replication allows all servers added to the protection group and all VMs to connect to the backup server. SSH and deployer certificate fingerprints are added to the Veeam Backup & Replication database and checked every time a machine establishes a connection with the backup server. If the SSH or certificate fingerprints do not match, the connection fails.
* KnownHosts: with this policy, only trusted servers and VMs can connect to the backup server.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRLinuxTrustedHostPolicy](vbrlinuxtrustedhostpolicy.md)

Examples

Getting Trust Policy

This command returns the trust policy that is set for protected machines.

|  |
| --- |
| Get-VBRLinuxTrustedHostPolicy |


