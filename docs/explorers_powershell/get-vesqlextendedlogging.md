---
title: "Get-VESQLExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlextendedlogging.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Get-VESQLExtendedLogging


Short Description

Returns the state of the extended logging mode for Veeam Explorer for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet returns the state of the extended logging mode for Veeam Explorer for Microsoft SQL Server. The cmdlet will return the following types of state:

* True — in case the extended logging mode is enabled.
* False — in case the extended logging mode is disabled.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Getting State of Extended Logging

This command returns the state of the extended logging mode for Veeam Explorer for Microsoft SQL Server.

|  |
| --- |
| Get-VESQLExtendedLogging |

Related Commands

* [Enable-VESQLExtendedLogging](enable-vesqlextendedlogging.md)
* [Disable-VESQLExtendedLogging](disable-vesqlextendedlogging.md)


