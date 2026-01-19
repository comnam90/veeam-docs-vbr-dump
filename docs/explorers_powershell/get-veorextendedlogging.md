---
title: "Get-VEORExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veorextendedlogging.html"
last_updated: "9/7/2023"
product_version: "13.0.1.1071"
---

# Get-VEORExtendedLogging


Short Description

Returns the state of the extended logging mode for Veeam Explorer for Oracle.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEORExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet returns the state of the extended logging mode for Veeam Explorer for Oracle. The cmdlet will return the following types of state:

* True — in case the extended logging mode is enabled.
* False — in case the extended logging mode is disabled.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Getting State of Extended Logging

This command returns the state of the extended logging mode for Veeam Explorer for Oracle.

|  |
| --- |
| Get-VEORExtendedLogging |

Related Commands

* [Enable-VEORExtendedLogging](enable-veorextendedlogging.md)
* [Disable-VEORExtendedLogging](disable-veorextendedlogging.md)


