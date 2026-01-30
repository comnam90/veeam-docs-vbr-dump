---
title: "VBRADEntity"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbradentity.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRADEntity


Contains an Active Directory object.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | The Active Directory object ID. |
| Name | string | The Active Directory object name. |
| Type | VBRADEntityType | The Active Directory object type:   * Domain * Cluster * OrganizationUnit * Group * Folder * Computer |
| DistinguishedName | string | The Active Directory object LDAP distinguished name. |

Related Commands

[Find-VBRADEntity](find-vbradentity.md)


