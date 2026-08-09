---
title: "/security/accounts/{ID}/scopes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/security_accounts_id_scopes.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /security/accounts/{ID}/scopes


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
| <EnterpriseAccountHierarchyScopes xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">     <EnterpriseAccountHierarchyScope Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/db0fd3c6-5f71-44f9-9bb1-1c61fc8b9fe2">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/db0fd3c6-5f71-44f9-9bb1-1c61fc8b9fe2" Rel="Delete" />         </Links>         <Name>172.24.145.152</Name>         <HierarchyRootName>24a14898-77d0-4881-bbf8-c8ba71ce4d55</HierarchyRootName>         <Platform>vCloud</Platform>         <HierarchyObjectType>VcdSystem</HierarchyObjectType>         <State>Processed</State>     </EnterpriseAccountHierarchyScope>     <EnterpriseAccountHierarchyScope Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf" Rel="Delete" />         </Links>         <Name>Enterprise</Name>         <HierarchyRootName>d68c782f-ec0a-4bf3-b3c1-04c552b64fdf</HierarchyRootName>         <Platform>VMware</Platform>         <HierarchyObjectType>ResourcePool</HierarchyObjectType>         <State>Processed</State>     </EnterpriseAccountHierarchyScope>     <EnterpriseAccountHierarchyScope Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf" Rel="Delete" />         </Links>         <Name>Enterprise</Name>         <HierarchyRootName>83963a7e-d43f-4fea-9036-466898c9c9e7</HierarchyRootName>         <Platform>VMware</Platform>         <HierarchyObjectType>ResourcePool</HierarchyObjectType>         <State>Processed</State>     </EnterpriseAccountHierarchyScope>     <EnterpriseAccountHierarchyScope Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf">         <Links>             <Link Href="https://enterprise04.tech.local:9398/api/security/accounts/d6701c3d-15f4-421d-b376-c0e2634bc1f4/scopes/4a203df3-ccc0-489f-9ff9-b80884977caf" Rel="Delete" />         </Links>         <Name>Enterprise</Name>         <HierarchyRootName>a26349ce-8c8a-47a2-af10-58afdd9fcece</HierarchyRootName>         <Platform>VMware</Platform>         <HierarchyObjectType>ResourcePool</HierarchyObjectType>         <State>Processed</State>     </EnterpriseAccountHierarchyScope> </EnterpriseAccountHierarchyScopes> |

Page updated 2026-07-29

