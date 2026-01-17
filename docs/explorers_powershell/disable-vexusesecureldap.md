---
title: "Disable-VEXUseSecureLdap"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/disable-vexusesecureldap.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Disables the secure LDAP mode for Veeam Explorer for Microsoft Exchange.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VEXUseSecureLdap [<CommonParameters>] |

Detailed Description

This cmdlet disables the secure LDAP mode for Veeam Explorer for Microsoft Exchange if it is enabled. If it is disabled, nothing will happen and it will not cause any errors. Veeam Explorer for Microsoft Exchange will use the less secure LDAP protocol.

Run the [Enable-VEXUseSecureLdap](enable-vexusesecureldap.md) cmdlet to get the state of the secure LDAP mode for Veeam Explorer for Microsoft Exchange.

Run the [Disable-VEXUseSecureLdap](disable-vexusesecureldap.md) cmdlet to disable the secure LDAP mode for Veeam Explorer for Microsoft Exchange.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Disabling Secure LDAP Mode

This command disables the secure LDAP mode for Veeam Explorer for Microsoft Exchange.

|  |
| --- |
| Disable-VEXUseSecureLdap |

Related Commands

* [Get-VEXUseSecureLdap](get-vexusesecureldap.md)
* [Enable-VEXUseSecureLdap](enable-vexusesecureldap.md)

Page updated 8/21/2025

Page content applies to build 13.0.1.1071
