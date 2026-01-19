---
title: "Disable-VEPSQLExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/disable-vepsqlextendedlogging.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Disable-VEPSQLExtendedLogging


Short Description

Disables the extended logging mode for Veeam Explorer for PostgreSQL.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VEPSQLExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet disables the extended logging mode for Veeam Explorer for PostgreSQL if it is enabled. If it is disabled, nothing will happen and it will not cause any errors.

Run the [Get-VEPSQLExtendedLogging](get-vepsqlextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for PostgreSQL.

Run the [Enable-VEPSQLExtendedLogging](enable-vepsqlextendedlogging.md) cmdlet to enable the extended logging mode for Veeam Explorer for PostgreSQL.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Disabling Extended Logging

This command disables the extended logging mode for Veeam Explorer for PostgreSQL.

|  |
| --- |
| Disable-VEPSQLExtendedLogging |

Related Commands

* [Get-VEPSQLExtendedLogging](get-vepsqlextendedlogging.md)
* [Enable-VEPSQLExtendedLogging](enable-vepsqlextendedlogging.md)


