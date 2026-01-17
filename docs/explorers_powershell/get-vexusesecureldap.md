---
title: "Get-VEXUseSecureLdap"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vexusesecureldap.html"
last_updated: "7/23/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns the state of the secure LDAP mode for Veeam Explorer for Microsoft Exchange.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEXUseSecureLdap [<CommonParameters>] |

Detailed Description

This cmdlet returns the state of secure LDAP mode for Veeam Explorer for Microsoft Exchange. The cmdlet will return the following types of state:

* True — indicates that the secure LDAP mode is enabled. Veeam Explorer for Microsoft Exchange uses the LDAPS (LDAP over SSL/TLS) protocol and prevents failover to the LDAP protocol if LDAPS is not available.
* False — indicates that the secure LDAP mode is disabled. Veeam Explorer for Microsoft Exchange uses the less secure LDAP protocol.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Getting State of Secure LDAP Mode

This command returns the state of the secure LDAP mode for Veeam Explorer for Microsoft Exchange.

|  |
| --- |
| Get-VEXUseSecureLdap |

Related Commands

* [Enable-VEXUseSecureLdap](enable-vexusesecureldap.md)
* [Disable-VEXUseSecureLdap](disable-vexusesecureldap.md)

Page updated 7/23/2025

Page content applies to build 13.0.1.1071
