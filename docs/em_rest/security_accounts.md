---
title: "/security/accounts"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security_accounts.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /security/accounts


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
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="EnterpriseAccountReference" Href="https://localhost:9398/api/security/accounts/d1b025b4-af19-4a8d-9eeb-2db43e4710f4" Name="BUILTIN\Administrators" UID="urn:veeam:EnterpriseAccount:d1b025b4-af19-4a8d-9eeb-2db43e4710f4">     <Links>       <Link Rel="Alternate" Type="EnterpriseAccount" Href="https://localhost:9398/api/security/accounts/d1b025b4-af19-4a8d-9eeb-2db43e4710f4?format=Entity" />     </Links>   </Ref>   <Ref Type="EnterpriseAccountReference" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7" Name="BUILTIN\Users" UID="urn:veeam:EnterpriseAccount:de19303b-bcf3-428b-b113-ac0b2cf46bd7">     <Links>       <Link Rel="Alternate" Type="EnterpriseAccount" Href="https://localhost:9398/api/security/accounts/de19303b-bcf3-428b-b113-ac0b2cf46bd7?format=Entity" />     </Links>   </Ref>   <Ref Type="EnterpriseAccountReference" Href="https://localhost:9398/api/security/accounts/2cd80a69-077c-400f-a714-cafe97bc8f60" Name="SRV02\Administrator" UID="urn:veeam:EnterpriseAccount:2cd80a69-077c-400f-a714-cafe97bc8f60">     <Links>       <Link Rel="Alternate" Type="EnterpriseAccount" Href="https://localhost:9398/api/security/accounts/2cd80a69-077c-400f-a714-cafe97bc8f60?format=Entity" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

