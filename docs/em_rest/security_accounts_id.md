---
title: "security_accounts_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security_accounts_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents an account having the specified ID. The account is added to Veeam Backup Enterprise Manager and is assigned a specific security role.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/security/accounts/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/security/accounts/{ID}?format=Entity |

Related Resources

* [/security](security.md)
* [/security/accounts](security_accounts.md)
* [/security/roles](security_roles.md)
* [/security/accounts/{ID}/scopes](security_accounts_id_scopes.md)

Methods

The following methods are supported for the /security/accounts/{ID} resource:

* [GET /security/accounts/{ID}](get_security_accounts_id.md)
* [POST /security/accounts/{ID}](post_security_accounts_id.md)
* [DELETE /security/accounts/{ID}](delete_security_accounts_id.md)

Resource Representation

The /security/accounts/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="EnterpriseAccountReference" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7" Name="BUILTIN\Users" UID="urn:veeam:EnterpriseAccount:de19303b-bcf3-428b-b113-ac0b2cf46bd7"> |

Entity resource representation:

|  |
| --- |
| <EnterpriseAccount xmlns="http://www.veeam.com/ent/v1.0" Type="EnterpriseAccount" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7?format=Entity" Name="BUILTIN\Users" UID="urn:veeam:EnterpriseAccount:de19303b-bcf3-428b-b113-ac0b2cf46bd7">   <Links>     <Link Rel="Alternate" Type="EnterpriseAccountReference" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7" />     <Link Rel="Down" Type="EnterpriseAccountInRoleList" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7/roles" />     <Link Rel="Create" Type="EnterpriseAccountInRole" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7/roles" />     <Link Rel="Down" Type="EnterpriseAccountHierarchyScopeList" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7/scopes" />     <Link Rel="Create" Type="EnterpriseAccountHierarchyScope" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7/scopes" />     <Link Rel="Delete" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7" />     <Link Rel="ToggleRestoreScopesEnabled" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7" />   </Links>   <AccountType>Group</AccountType>   <AllowRestoreAllVms>false</AllowRestoreAllVms> </EnterpriseAccount> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
