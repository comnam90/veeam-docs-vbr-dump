---
title: "/security/accounts"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security_accounts.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of accounts having specific security roles in Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/security/accounts |

Related Resources

* [/security](security.md)
* [/security/accounts/{ID}](security_accounts_id.md)
* [/security/roles/{ID}](security_roles_id.md)

Methods

The following methods are supported for the /security/accounts resource:

* [GET /security/accounts](get_security_accounts.md)
* [POST /security/accounts](post_security_accounts.md)
* [POST /security/accounts?action=rebuildScope](post_security_accounts_actionrebuildscope.md)

Resource Representation

The /security/accounts resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
