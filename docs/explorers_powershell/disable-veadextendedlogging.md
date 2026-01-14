---
title: "disable-veadextendedlogging"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/disable-veadextendedlogging.html"
last_updated: "9/23/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Disables the extended logging mode for Veeam Explorer for Microsoft Active Directory.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VEADExtendedLogging [<CommonParameters>] |

Detailed Description

This cmdlet disables the extended logging mode for Veeam Explorer for Microsoft Active Directory if it is enabled. If it is disabled, nothing will happen and it will not cause any errors.

Run the [Get-VEADExtendedLogging](get-veadextendedlogging.md) cmdlet to get the state of the extended logging mode for Veeam Explorer for Microsoft Active Directory.

Run the [Enable-VEADExtendedLogging](enable-veadextendedlogging.md) cmdlet to enable the extended logging mode for Veeam Explorer for Microsoft Active Directory.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Disabling Extended Logging

This command disables the extended logging mode for Veeam Explorer for Microsoft Active Directory.

|  |
| --- |
| Disable-VEADExtendedLogging |

Related Commands

* [Get-VEADExtendedLogging](get-veadextendedlogging.md)
* [Enable-VEADExtendedLogging](enable-veadextendedlogging.md)

Page updated 9/23/2024

Page content applies to build 13.0.1.1071
