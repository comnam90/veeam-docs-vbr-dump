---
title: "get-vehanaextendedlogging"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vehanaextendedlogging.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns the state of the extended logging mode for Veeam Explorer for SAP HANA.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEHANAExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet returns the state of the extended logging mode for Veeam Explorer for SAP HANA. The cmdlet will return the following types of state:

* True — indicates that the extended logging mode is enabled.
* False — indicates that the extended logging mode is disabled.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Getting State of Extended Logging

This command returns the state of the extended logging mode for Veeam Explorer for SAP HANA.

|  |
| --- |
| Get-VEHANAExtendedLogging |

Related Commands

* [Enable-VEHANAExtendedLogging](enable-vehanaextendedlogging.md)
* [Disable-VEHANAExtendedLogging](disable-vehanaextendedlogging.md)

Page updated 4/19/2024

Page content applies to build 13.0.1.1071
