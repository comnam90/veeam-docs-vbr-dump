---
title: "Disable-VEXExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/disable-vexextendedlogging.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Disables the extended logging mode for Veeam Explorer for Microsoft Exchange.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VEXExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet disables the extended logging mode for Veeam Explorer for Microsoft Exchange if it is enabled. If it is disabled, nothing will happen and it will not cause any errors.

Run the [Get-VEXExtendedLogging](get-vexextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for Microsoft Exchange.

Run the [Enable-VEXExtendedLogging](enable-vexextendedlogging.md) cmdlet to enable the extended logging mode for Veeam Explorer for Microsoft Exchange.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Disabling Extended Logging

This command disables the extended logging mode for Veeam Explorer for Microsoft Exchange.

|  |
| --- |
| Disable-VEXExtendedLogging |

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
