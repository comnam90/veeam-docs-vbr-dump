---
title: "disable-veorextendedlogging"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/disable-veorextendedlogging.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Disables the extended logging mode for Veeam Explorer for Oracle.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VEORExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet disables the extended logging mode for Veeam Explorer for Oracle if it is enabled. If it is disabled, nothing will happen and it will not cause any errors.

Run the [Get-VEORExtendedLogging](get-veorextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for Oracle.

Run the [Enable-VEORExtendedLogging](enable-veorextendedlogging.md) cmdlet to enable the extended logging mode for Veeam Explorer for Oracle.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Disabling Extended Logging

This command disables the extended logging mode for Veeam Explorer for Oracle.

|  |
| --- |
| Disable-VEORExtendedLogging |

Related Commands

* [Get-VEORExtendedLogging](get-veorextendedlogging.md)
* [Enable-VEORExtendedLogging](enable-veorextendedlogging.md)

Page updated 3/8/2024

Page content applies to build 13.0.1.1071
