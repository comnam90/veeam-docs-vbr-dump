---
title: "security_accounts_id_roles_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security_accounts_id_roles_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a specific security role assigned to the specified account that is added to Veeam Backup Enterprise Manager. For details on security roles, see [Security Roles](security_roles_concept.md).

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/security/accounts/{ID}/roles/{ID} |

Related Resources

* [/security/accounts/{ID}/roles](security_accounts_id_roles.md)

Methods

The following methods are supported for the /security/accounts/{ID}/roles/{ID} resource:

* [GET /security/accounts/{ID}/roles/{ID}](get_security_accounts_id_roles_id.md)
* [DELETE /security/accounts/{ID}/roles/{ID}](delete_security_accounts_id_roles_id.md)

Resource Representation

The /security/accounts/{ID}/roles/{ID} resource has a resource representation of the following type:

|  |
| --- |
| <EnterpriseAccountInRole xmlns="http://www.veeam.com/ent/v1.0" Href="https://localhost:9398/api/security/accounts/f7d81d38-a457-4ee7-9294-a9123f8e4e99/roles/f84a8b62-49b8-4d0c-b25b-92321b52bab6"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
