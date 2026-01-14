---
title: "enable-vemdbextendedlogging"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/enable-vemdbextendedlogging.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Enables the extended logging mode for Veeam Explorer for MongoDB.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VEMDBExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet enables the extended logging mode for Veeam Explorer for MongoDB if it is disabled. If it is enabled, nothing will happen and it will not cause any errors.

Run the [Get-VEMDBExtendedLogging](get-vemdbextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for MongoDB.

Run the [Disable-VEMDBExtendedLogging](disable-vemdbextendedlogging.md) cmdlet to disable the extended logging mode for Veeam Explorer for MongoDB.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Enabling Extended Logging

This command enables the extended logging mode for Veeam Explorer for MongoDB.

|  |
| --- |
| Enable-VEMDBExtendedLogging |

Related Commands

* [Get-VEMDBExtendedLogging](get-vemdbextendedlogging.md)
* [Disable-VEMDBExtendedLogging](disable-vemdbextendedlogging.md)

Page updated 6/12/2024

Page content applies to build 13.0.1.1071
