---
title: "/security/roles"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security_roles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /security/roles


Represents a collection of security roles used for access management in Veeam Backup Enterprise Manager REST API. For details on security roles, see [Security Roles](security_roles_concept.md).

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/security/roles |

Related Resources

* [/security](security.md)
* [/security/roles/{ID}](security_roles_id.md)
* [/security/accounts](security_accounts.md)

Methods

The following methods are supported for the /security/roles resource:

[GET /security/roles](get_security_roles.md)

Resource Representation

The /security/roles resource has a resource representation of the following type:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <EntityReferences xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">     <Ref UID="urn:veeam:EnterpriseRole:d19a3d33-cb77-4ffe-94e6-001432483a4e" Name="Portal User" Href="https://enterprise04.tech.local:9398/api/security/roles/d19a3d33-cb77-4ffe-94e6-001432483a4e" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/d19a3d33-cb77-4ffe-94e6-001432483a4e?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:f78a92b8-9f06-4f1e-b522-4f0927cabd0f" Name="SQL Restore Operator" Href="https://enterprise04.tech.local:9398/api/security/roles/f78a92b8-9f06-4f1e-b522-4f0927cabd0f" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/f78a92b8-9f06-4f1e-b522-4f0927cabd0f?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:e9d90e66-b6d4-49dc-8986-73cf33489623" Name="Oracle Restore Operator" Href="https://enterprise04.tech.local:9398/api/security/roles/e9d90e66-b6d4-49dc-8986-73cf33489623" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/e9d90e66-b6d4-49dc-8986-73cf33489623?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:f84a8b62-49b8-4d0c-b25b-92321b52bab6" Name="File Restore Operator" Href="https://enterprise04.tech.local:9398/api/security/roles/f84a8b62-49b8-4d0c-b25b-92321b52bab6" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/f84a8b62-49b8-4d0c-b25b-92321b52bab6?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:f83e4c81-0815-452f-9377-9d573dd9d481" Name="Exchange Restore Operator" Href="https://enterprise04.tech.local:9398/api/security/roles/f83e4c81-0815-452f-9377-9d573dd9d481" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/f83e4c81-0815-452f-9377-9d573dd9d481?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:5f37a46b-9ce2-40f4-8a62-b45b079257fc" Name="Portal Administrator" Href="https://enterprise04.tech.local:9398/api/security/roles/5f37a46b-9ce2-40f4-8a62-b45b079257fc" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/5f37a46b-9ce2-40f4-8a62-b45b079257fc?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref>     <Ref UID="urn:veeam:EnterpriseRole:c11c0c38-ba8b-49c7-bf70-fc2058fff1e2" Name="VM Restore Operator" Href="https://enterprise04.tech.local:9398/api/security/roles/c11c0c38-ba8b-49c7-bf70-fc2058fff1e2" Type="EnterpriseRoleReference">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/roles/c11c0c38-ba8b-49c7-bf70-fc2058fff1e2?format=Entity" Type="EnterpriseRole" Rel="Alternate" />         </Links>     </Ref> </EntityReferences> |

Page updated 2026-07-29

