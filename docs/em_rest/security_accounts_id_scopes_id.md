---
title: "/security/accounts/{ID}/scopes/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security_accounts_id_scopes_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /security/accounts/{ID}/scopes/{ID}


Represents a specific restore scope defined for the specified account. The account is added to Veeam Backup Enterprise Manager and is assigned a specific security role.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/security/accounts/{ID}/scopes/{ID} |

Related Resources

[/security/accounts/{ID}/scopes](security_accounts_id_scopes.md)

Methods

The following methods are supported for the /security/accounts/{ID}/scopes/{ID} resource:

* [GET /security/accounts/{ID}/scopes/{ID}](get_security_accounts_id_scopes_id.md)
* [DELETE /security/accounts /{ID}/scopes/{ID}](delete_security_accounts_id_scopes_id.md)

Resource Representation

The /security/accounts/{ID}/scopes/{ID} resource has a resource representation of the following types.

|  |
| --- |
| <EnterpriseAccountHierarchyScope xmlns="http://www.veeam.com/ent/v1.0" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7/scopes/bceb75f9-5c10-4f39-9eb5-c000a2fabaee"> |


