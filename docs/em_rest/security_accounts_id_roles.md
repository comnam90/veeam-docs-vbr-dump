---
title: "security_accounts_id_roles"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security_accounts_id_roles.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of security roles assigned to the specified Veeam Backup Enterprise Manager account. For details on security roles, see [Security Roles](security_roles_concept.md).

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/security/accounts/{ID}/roles |

Related Resources

* [/security/accounts/{ID}](security_accounts_id.md)

Methods

The following methods are supported for the /security/accounts/{ID}/roles resource:

* [GET /security/accounts/{ID}/roles](get_security_accounts_id_roles.md)
* [POST /security/accounts/{ID}/roles](post_security_accounts_id_roles.md)

Resource Representation

The /security/accounts/{ID}/roles resource has a resource representation of the following type:

|  |
| --- |
| <EnterpriseAccountInRoleList xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
