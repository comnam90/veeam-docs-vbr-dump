---
title: "enable-vepsqlextendedlogging"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/enable-vepsqlextendedlogging.html"
last_updated: "1/21/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Enables the extended logging mode for Veeam Explorer for PostgreSQL.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VEPSQLExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet enables the extended logging mode for Veeam Explorer for PostgreSQL if it is disabled. If it is enabled, nothing will happen and it will not cause any errors.

Run the [Get-VEPSQLExtendedLogging](get-vepsqlextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for PostgreSQL.

Run the [Disable-VEPSQLExtendedLogging](disable-vepsqlextendedlogging.md) cmdlet to disable the extended logging mode for Veeam Explorer for PostgreSQL.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Enabling Extended Logging

This command enables the extended logging mode for Veeam Explorer for PostgreSQL.

|  |
| --- |
| Enable-VEPSQLExtendedLogging |

Related Commands

* [Get-VEPSQLExtendedLogging](get-vepsqlextendedlogging.md)
* [Disable-VEPSQLExtendedLogging](disable-vepsqlextendedlogging.md)

Page updated 1/21/2025

Page content applies to build 13.0.1.1071
