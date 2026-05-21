---
title: "VBRADEntity"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbradentity.html"
last_updated: "5/20/2026"
product_version: "13.0.1.2067"
---

# VBRADEntity


Contains an Active Directory object.

Properties

Properties

| Property | Type | Description |
| Id | GUID | The Active Directory object ID. |
| Name | string | The Active Directory object name.  For Computer objects, returns the dNSHostName attribute. |
| FullName | string | The Active Directory object full name. |
| Type | VBRADEntityType | The Active Directory object type:   * Domain * Cluster * OrganizationUnit * Group * Folder * Computer |
| DistinguishedName | string | The Active Directory object LDAP distinguished name. |

Related Commands

[Find-VBRADEntity](find-vbradentity.md)


