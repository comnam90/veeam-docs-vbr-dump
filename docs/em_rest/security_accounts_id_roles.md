---
title: "/security/accounts/{ID}/roles"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security_accounts_id_roles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /security/accounts/{ID}/roles


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
| <EnterpriseAccountInRoleList xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">     <EnterpriseAccountInRole Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f84a8b62-49b8-4d0c-b25b-92321b52bab6">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f84a8b62-49b8-4d0c-b25b-92321b52bab6" Rel="Delete" />         </Links>         <RoleName>File Restore Operator</RoleName>     </EnterpriseAccountInRole>     <EnterpriseAccountInRole Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/c11c0c38-ba8b-49c7-bf70-fc2058fff1e2">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/c11c0c38-ba8b-49c7-bf70-fc2058fff1e2" Rel="Delete" />         </Links>         <RoleName>VM Restore Operator</RoleName>     </EnterpriseAccountInRole>     <EnterpriseAccountInRole Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f83e4c81-0815-452f-9377-9d573dd9d481">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f83e4c81-0815-452f-9377-9d573dd9d481" Rel="Delete" />         </Links>         <RoleName>Exchange Restore Operator</RoleName>     </EnterpriseAccountInRole>     <EnterpriseAccountInRole Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f78a92b8-9f06-4f1e-b522-4f0927cabd0f">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/f78a92b8-9f06-4f1e-b522-4f0927cabd0f" Rel="Delete" />         </Links>         <RoleName>SQL Restore Operator</RoleName>     </EnterpriseAccountInRole>     <EnterpriseAccountInRole Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/d19a3d33-cb77-4ffe-94e6-001432483a4e">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/roles/d19a3d33-cb77-4ffe-94e6-001432483a4e" Rel="Delete" />         </Links>         <RoleName>Portal User</RoleName>     </EnterpriseAccountInRole> </EnterpriseAccountInRoleList> |

Page updated 2026-07-29

