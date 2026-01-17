---
title: "Enable-VEHANAExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/enable-vehanaextendedlogging.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Enable-VEHANAExtendedLogging


Short Description

Enables the extended logging mode for Veeam Explorer for SAP HANA.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VEHANAExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet enables the extended logging mode for Veeam Explorer for SAP HANA if it is disabled. If it is enabled, nothing will happen and it will not cause any errors.

Run the [Get-VEHANAExtendedLogging](get-vehanaextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for SAP HANA.

Run the [Disable-VEHANAExtendedLogging](disable-vehanaextendedlogging.md) cmdlet to disable the extended logging mode for Veeam Explorer for SAP HANA.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Enabling Extended Logging

This command enables the extended logging mode for Veeam Explorer for SAP HANA.

|  |
| --- |
| Enable-VEHANAExtendedLogging |

Related Commands

* [Get-VEHANAExtendedLogging](get-vehanaextendedlogging.md)
* [Disable-VEHANAExtendedLogging](disable-vehanaextendedlogging.md)


