---
title: "/security/roles/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security_roles_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /security/roles/{ID}


Represents a Veeam Backup Enterprise Manager security role having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/security/roles/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/security/roles/{ID}?format=Entity |

Related Resources

* [/security](security.md)
* [/security/roles](security_roles.md)
* [/security/accounts](security_accounts.md)

Methods

The following methods are supported for the /security/roles/{ID} resource:

[GET /security/roles/{ID}](get_security_roles_id.md)

Resource Representation

The /security/roles/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="EnterpriseRoleReference" Href="https://localhost:9398/api/security/roles/f83e4c81-0815-452f-9377-9d573dd9d481" Name="Exchange Restore Operator" UID="urn:veeam:EnterpriseRole:f83e4c81-0815-452f-9377-9d573dd9d481">   <Links>     <Link Rel="Alternate" Type="EnterpriseRole" Href="https://localhost:9398/api/security/roles/f83e4c81-0815-452f-9377-9d573dd9d481?format=Entity" />   </Links> </EntityRef> |

Entity resource representation:

|  |
| --- |
| <EnterpriseRole xmlns="http://www.veeam.com/ent/v1.0" Type="EnterpriseRole" Href="https://localhost:9398/api/security/roles/f83e4c81-0815-452f-9377-9d573dd9d481?format=Entity" Name="Exchange Restore Operator" UID="urn:veeam:EnterpriseRole:f83e4c81-0815-452f-9377-9d573dd9d481">   <Links>     <Link Rel="Alternate" Type="EnterpriseRoleReference" Href="https://localhost:9398/api/security/roles/f83e4c81-0815-452f-9377-9d573dd9d481" />   </Links> </EnterpriseRole> |

Page updated 2026-07-29

