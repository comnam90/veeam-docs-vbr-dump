---
title: "new_updated_cmdlets_12.3"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/new_updated_cmdlets_12.3.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---


In this article

This section contains information on new and updated Veeam Explorers PowerShell cmdlets in Veeam Backup & Replication 12.3.

Veeam Explorer for Microsoft Active Directory

In Veeam Backup & Replication 12.3, new cmdlets were added to the Veeam Explorer for Microsoft Active Directory PowerShell module, which allow you to get, enable and disable the extended logging mode.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VEADExtendedLogging](get-veadextendedlogging.md) | Returns the state of the extended logging mode for Veeam Explorer for Microsoft Active Directory. | | [Enable-VEADExtendedLogging](enable-veadextendedlogging.md) | Enables the extended logging mode for Veeam Explorer for Microsoft Active Directory. | | [Disable-VEADExtendedLogging](disable-veadextendedlogging.md) | Disables the extended logging mode for Veeam Explorer for Microsoft Active Directory. | |

Veeam Explorer for Oracle

In this version, the SysUserPassword parameter was added to the [Restore-VEORRMANDatabase](restore-veorrmandatabase.md) cmdlet. Use this parameter to restore your data when OS authentication to Oracle databases is disabled on the target server.

Page updated 9/26/2025

Page content applies to build 13.0.1.1071
