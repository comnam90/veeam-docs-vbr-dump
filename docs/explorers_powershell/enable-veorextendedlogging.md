---
title: "Enable-VEORExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/enable-veorextendedlogging.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Enable-VEORExtendedLogging


Short Description

Enables the extended logging mode for Veeam Explorer for Oracle.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VEORExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet enables the extended logging mode for Veeam Explorer for Oracle if it is disabled. If it is enabled, nothing will happen and it will not cause any errors.

Run the [Get-VEORExtendedLogging](get-veorextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for Oracle.

Run the [Disable-VEORExtendedLogging](disable-veorextendedlogging.md) cmdlet to disable the extended logging mode for Veeam Explorer for Oracle.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Enabling Extended Logging

This command enables the extended logging mode for Veeam Explorer for Oracle.

|  |
| --- |
| Enable-VEORExtendedLogging |

Related Commands

* [Get-VEORExtendedLogging](get-veorextendedlogging.md)
* [Disable-VEORExtendedLogging](disable-veorextendedlogging.md)


