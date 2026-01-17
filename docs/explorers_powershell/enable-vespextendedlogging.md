---
title: "Enable-VESPExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/enable-vespextendedlogging.html"
last_updated: "6/21/2024"
product_version: "13.0.1.1071"
---

# Enable-VESPExtendedLogging


Short Description

Enables the extended logging mode for Veeam Explorer for Microsoft SharePoint.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VESPExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet enables the extended logging mode for Veeam Explorer for Microsoft SharePoint if it is disabled. If it is enabled, nothing will happen and it will not cause any errors.

Run the [Disable-VESPExtendedLogging](disable-vespextendedlogging.md) cmdlet to disable the extended logging mode.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Enabling Extended Logging

This command enables the extended logging mode for Veeam Explorer for Microsoft SharePoint.

|  |
| --- |
| Enable-VESPExtendedLogging |


