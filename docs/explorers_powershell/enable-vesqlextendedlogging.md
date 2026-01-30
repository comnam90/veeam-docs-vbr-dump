---
title: "Enable-VESQLExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/enable-vesqlextendedlogging.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Enable-VESQLExtendedLogging


Short Description

Enables the extended logging mode for Veeam Explorer for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VESQLExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet enables the extended logging mode for Veeam Explorer for Microsoft SQL Server if it is disabled. If it is enabled, nothing will happen and it will not cause any errors.

Run the [Get-VESQLExtendedLogging](get-vesqlextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for Microsoft SQL Server.

Run the [Disable-VESQLExtendedLogging](disable-vesqlextendedlogging.md) cmdlet to disable the extended logging mode for Veeam Explorer for Microsoft SQL Server.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Enabling Extended Logging

This command enables the extended logging mode for Veeam Explorer for Microsoft SQL Server.

|  |
| --- |
| Enable-VESQLExtendedLogging |

Related Commands

* [Get-VESQLExtendedLogging](get-vesqlextendedlogging.md)
* [Disable-VESQLExtendedLogging](disable-vesqlextendedlogging.md)


