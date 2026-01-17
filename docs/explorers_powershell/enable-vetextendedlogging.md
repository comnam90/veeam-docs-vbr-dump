---
title: "Enable-VETExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/enable-vetextendedlogging.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Enables the extended logging mode for Veeam Explorer for Microsoft Teams.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

|  |
| --- |
| Enable-VETExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet enables the extended logging mode for Veeam Explorer for Microsoft Teams if it is disabled. If it is enabled, nothing will happen and it will not cause any errors.

Run the [Get-VETExtendedLogging](get-vetextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for Microsoft Teams.

Run the [Disable-VETExtendedLogging](disable-vetextendedlogging.md) cmdlet to the disable the extended logging mode for Veeam Explorer for Microsoft Teams.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Enabling Extended Logging

This command enables the extended logging mode for Veeam Explorer for Microsoft Teams.

|  |
| --- |
| Enable-VETExtendedLogging |

Page updated 6/18/2024

Page content applies to build 13.0.1.1071
