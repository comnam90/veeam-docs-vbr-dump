---
title: "Enable-VEADExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/enable-veadextendedlogging.html"
last_updated: "9/23/2024"
product_version: "13.0.1.1071"
---

# Enable-VEADExtendedLogging


Short Description

Enables the extended logging mode for Veeam Explorer for Microsoft Active Directory.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VEADExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet enables the extended logging mode for Veeam Explorer for Microsoft Active Directory if it is disabled. If it is enabled, nothing will happen and it will not cause any errors.

Run the [Get-VEADExtendedLogging](get-veadextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for Microsoft Active Directory.

Run the [Disable-VEADExtendedLogging](disable-veadextendedlogging.md) cmdlet to disable the extended logging mode for Veeam Explorer for Microsoft Active Directory.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Enabling Extended Logging

This command enables the extended logging mode for Veeam Explorer for Microsoft Active Directory.

|  |
| --- |
| Enable-VEADExtendedLogging |

Related Commands

* [Get-VEADExtendedLogging](get-veadextendedlogging.md)
* [Disable-VEADExtendedLogging](disable-veadextendedlogging.md)


