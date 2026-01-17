---
title: "Disable-VEHANAExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/disable-vehanaextendedlogging.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Disables the extended logging mode for Veeam Explorer for SAP HANA.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VEHANAExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet disables the extended logging mode for Veeam Explorer for SAP HANA if it is enabled. If it is disabled, nothing will happen and it will not cause any errors.

Run the [Get-VEHANAExtendedLogging](get-vehanaextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for SAP HANA.

Run the [Enable-VEHANAExtendedLogging](enable-vehanaextendedlogging.md) cmdlet to enable the extended logging mode for Veeam Explorer for SAP HANA.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Disabling Extended Logging

This command disables the extended logging mode for Veeam Explorer for SAP HANA.

|  |
| --- |
| Disable-VEHANAExtendedLogging |

Related Commands

* [Get-VEHANAExtendedLogging](get-vehanaextendedlogging.md)
* [Enable-VEHANAExtendedLogging](enable-vehanaextendedlogging.md)

Page updated 4/19/2024

Page content applies to build 13.0.1.1071
