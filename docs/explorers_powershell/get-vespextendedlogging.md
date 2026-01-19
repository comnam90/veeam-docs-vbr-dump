---
title: "Get-VESPExtendedLogging"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vespextendedlogging.html"
last_updated: "1/23/2025"
product_version: "13.0.1.1071"
---

# Get-VESPExtendedLogging


Short Description

Returns a state of the extended logging mode for Veeam Explorer for Microsoft SharePoint.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESPExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet returns a state of the extended logging mode for Veeam Explorer for Microsoft SharePoint. The cmdlet will return the following types of the state:

* True — indicates that the extended logging mode is enabled.
* False — indicates that the extended logging mode is disabled.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Getting State of Extended Logging

This command returns an indication of the enabled or disabled state of the extended logging mode for Veeam Explorer for Microsoft SharePoint.

|  |
| --- |
| Get-VESPExtendedLogging |


