---
title: "Get-VEPSQLExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vepsqlextendedlogging.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns the state of the extended logging mode for Veeam Explorer for PostgreSQL.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEPSQLExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet returns the state of the extended logging mode for Veeam Explorer for PostgreSQL. The cmdlet will return the following types of state:

* True — in case the extended logging mode is enabled.
* False — in case the extended logging mode is disabled.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Getting State of Extended Logging

This command returns the state of the extended logging mode for Veeam Explorer for PostgreSQL.

|  |
| --- |
| Get-VEPSQLExtendedLogging |

Related Commands

* [Enable-VEPSQLExtendedLogging](enable-vepsqlextendedlogging.md)
* [Disable-VEPSQLExtendedLogging](disable-vepsqlextendedlogging.md)

Page updated 4/19/2024

Page content applies to build 13.0.1.1071
