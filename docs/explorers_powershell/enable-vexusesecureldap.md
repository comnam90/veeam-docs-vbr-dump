---
title: "enable-vexusesecureldap"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/enable-vexusesecureldap.html"
last_updated: "7/23/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Enables the secure LDAP mode for Veeam Explorer for Microsoft Exchange.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VEXUseSecureLdap [<CommonParameters>] |

Detailed Description

This cmdlet enables the secure LDAP mode for Veeam Explorer for Microsoft Exchange if it is disabled. If it is enabled, nothing will happen and it will not cause any errors. Veeam Explorer for Microsoft Exchange will use the more secure LDAPS (LDAP over SSL/TLS) protocol and will not failover to the LDAP protocol if LDAPS is not available.

Run the [Get-VEXUseSecureLdap](get-vexusesecureldap.md) cmdlet to get the state of the secure LDAP mode for Veeam Explorer for Microsoft Exchange.

Run the [Disable-VEXUseSecureLdap](disable-vexusesecureldap.md) cmdlet to disable the secure LDAP mode for Veeam Explorer for Microsoft Exchange.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Enabling Secure LDAP Mode

This command enables the secure LDAP mode for Veeam Explorer for Microsoft Exchange.

|  |
| --- |
| Enable-VEXUseSecureLdap |

Related Commands

* [Get-VEXUseSecureLdap](get-vexusesecureldap.md)
* [Disable-VEXUseSecureLdap](disable-vexusesecureldap.md)

Page updated 7/23/2025

Page content applies to build 13.0.1.1071
