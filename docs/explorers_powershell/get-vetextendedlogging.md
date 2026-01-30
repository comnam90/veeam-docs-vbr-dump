---
title: "Get-VETExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vetextendedlogging.html"
last_updated: "1/27/2025"
product_version: "13.0.1.1071"
---

# Get-VETExtendedLogging


Short Description

Returns a state of the extended logging mode for Veeam Explorer for Microsoft Teams.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

|  |
| --- |
| Get-VETExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet returns a state of the extended logging mode for Veeam Explorer for Microsoft Teams. The cmdlet returns the following types of the state:

* True — indicates that the extended logging mode is enabled.
* False — indicates that the extended logging mode is disabled.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Getting State of Extended Logging

This command returns a state of the extended logging mode for Veeam Explorer for Microsoft Teams.

|  |
| --- |
| Get-VETExtendedLogging |


