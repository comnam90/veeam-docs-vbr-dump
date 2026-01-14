---
title: "security_accounts_id_scopes"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security_accounts_id_scopes.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of restore scopes defined for the specified account that is added to Veeam Backup Enterprise Manager and is assigned a specific security role.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/security/accounts/{ID}/scopes |

Related Resources

[/security/accounts/{ID}](security_accounts_id.md)

Methods

The following methods are supported for the /security/accounts/{ID}/scopes resource:

* [GET /security/accounts/{ID}/scopes](get_security_accounts_id_scopes.md)
* [POST /security/accounts /{ID}/scopes](post_security_accounts_id_scopes.md)

Resource Representation

The /security/accounts/{ID}/scopes resource has a resource representation of the following type:

|  |
| --- |
| <EnterpriseAccountHierarchyScopes xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
