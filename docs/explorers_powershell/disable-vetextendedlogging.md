---
title: "Disable-VETExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/disable-vetextendedlogging.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---

# Disable-VETExtendedLogging


Short Description

Disables the extended logging mode for Veeam Explorer for Microsoft Teams.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

|  |
| --- |
| Disable-VETExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet disables the extended logging mode for Veeam Explorer for Microsoft Teams if it is enabled. If it is disabled, nothing will happen and it will not cause any errors.

Run the [Get-VETExtendedLogging](get-vetextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for Microsoft Teams.

Run the [Enable-VETExtendedLogging](enable-vetextendedlogging.md) cmdlet to enable the extended logging mode for Veeam Explorer for Microsoft Teams.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Disabling Extended Logging

This command disables the extended logging mode for Veeam Explorer for Microsoft Teams.

|  |
| --- |
| Disable-VETExtendedLogging |


