---
title: "scenario_restore_scope"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/scenario_restore_scope.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Using Veeam Backup Enterprise Manager REST API, you assign a restore scope to an account having the Restore Operators role in Veeam Backup Enterprise Manager.

A restore scope can be assigned to a user account that belongs to the Portal Operators group in Veeam Backup Enterprise Manager. The restore scope is specified as a branch in the virtual infrastructure hierarchy. The client defines the upper node in the branch and all child nodes of the defined node become available to the user for restore.

For example, if you want to allow the user to restore data from all VMs in the VMs resource pool, send the parameters of the resource pool node when assigning a restore scope. As a result, Veeam Backup Enterprise Manager will allow the user to restore data from all VMs residing in the VMs resource pool.

Prerequisites

Make sure you are logged on to Veeam Backup Enterprise Manager under the user account to which the Portal Administrator role is assigned. Otherwise you will not be able to change configuration settings in Veeam Backup Enterprise Manager.

Procedure

1. After you [access](accessing_em_web_api.md) Veeam Backup Enterprise Manager [REST API](accessing_em_web_api.md) and [create a new logon session](logging_on.md), examine the representation of the logon session that the server has returned:

|  |
| --- |
| Request:  POST https://localhost:9398/api/sessionMngr/?v=v1\_7    Request Header:  Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=    Response:  201 Created    Response Header:  X-RestSvcSessionId: NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response Body:  <LogonSession xmlns="http://www.veeam.com/ent/v1.0" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/3b68b200-0a74-4543-b7b2-301fae3ea507"> |

1. Find the link for the /security resource:

|  |
| --- |
| <Link Rel="Down" Type="EnterpriseSecuritySettings" Href="https://localhost:9398/api/security" /> |

1. From the link, retrieve the URL for the /security resource. The URL is specified in the Href element. Send the GET HTTP request to the retrieved URL. The server will return a representation of the security resource that provides access to Veeam Backup Enterprise Manager security settings and allows you to manage roles used in Veeam Backup Enterprise Manager:

|  |
| --- |
| Request:  GET https://localhost:9398/api/security    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EnterpriseSecuritySettings xmlns="http://www.veeam.com/ent/v1.0" Href="https://localhost:9398/api/security">   <Links>     <Link Rel="Down" Type="EnterpriseAccountReferenceList" Href="https://localhost:9398/api/security/accounts" />     <Link Rel="Down" Type="EnterpriseRoleReferenceList" Href="https://localhost:9398/api/security/roles" />     <Link Rel="Create" Href="https://localhost:9398/api/security/accounts" />     <Link Rel="Start" Href="https://localhost:9398/api/security/accounts?action=rebuildScope" />   </Links> </EnterpriseSecuritySettings> |

1. Examine the received resource representation and find a link to the /accounts resource.

|  |
| --- |
| <Link Rel="Down" Type="EnterpriseAccountReferenceList" Href="https://localhost:9398/api/security/accounts" /> |

1. Retrieve the URL for the /accounts resource and send the GET HTTP request to the retrieved URL. The server will return a list of all accounts that have a specific role in Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/security/accounts    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="EnterpriseAccountReference" Href="https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5" Name="localhost\Administrator" UID="urn:veeam:EnterpriseAccount:129ccafb-d740-4a5a-b602-b02acfec1ec5">     <Links>       <Link Rel="Alternate" Type="EnterpriseAccount" Href="https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5?format=Entity" />     </Links>   </Ref>   <Ref Type="EnterpriseAccountReference" Href="https://localhost:9398/api/security/accounts/d537f7a1-9143-4c90-8326-d4225c4a8f30" Name="BUILTIN\Administrators" UID="urn:veeam:EnterpriseAccount:d537f7a1-9143-4c90-8326-d4225c4a8f30">     <Links>       <Link Rel="Alternate" Type="EnterpriseAccount" Href="https://localhost:9398/api/security/accounts/d537f7a1-9143-4c90-8326-d4225c4a8f30?format=Entity" />     </Links>   </Ref> </EntityReferences> |

1. Find a link to the entity representation of the necessary account resource and send the GET HTTP request to it.

|  |
| --- |
| Request:  GET https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5?format=Entity    Request Header:  X-RestSvcSessionId:  NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EnterpriseAccount xmlns="http://www.veeam.com/ent/v1.0" Type="EnterpriseAccount" Href="https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5?format=Entity" Name="localhost\Administrator" UID="urn:veeam:EnterpriseAccount:129ccafb-d740-4a5a-b602-b02acfec1ec5">   <Links>     <Link Rel="Alternate" Type="EnterpriseAccountReference" Href="https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5" />     <Link Rel="Down" Type="EnterpriseAccountInRoleList" Href="https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5/roles" />     <Link Rel="Create" Type="EnterpriseAccountInRole" Href="https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5/roles" />     <Link Rel="Down" Type="EnterpriseAccountHierarchyScopeList" Href="https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5/scopes" />     <Link Rel="Create" Type="EnterpriseAccountHierarchyScope" Href="https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5/scopes" />     <Link Rel="Delete" Href="https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5" />     <Link Rel="ToggleRestoreScopesEnabled" Href="https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5" />   </Links>   <AccountType>User</AccountType>   <AllowRestoreAllVms>true</AllowRestoreAllVms> </EnterpriseAccount> |

1. Examine the received resource representation and find a link to the scope creation action. Send the POST HTTP request to the URL in the link.

The request requires a body. In the body of the request, you must provide a reference to the hierarchy object, or node in the virtual infrastructure, and the object name. For example, if you want to assign a resource pool as a restore scope, you must provide a reference to the resource pool object in the request body.

The reference to the hierarchy object can be [constructed manually](constructing_hierarchyobjreftype.md) or obtained using the [lookup service](lookupsvc.md).

|  |
| --- |
| Request:  POST https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5/scopes    Request Headers:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <HierarchyScopeCreateSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <HierarchyScopeItem>     <HierarchyObjRef>urn:VMware:ResourcePool:3e7fea0c-e92d-4459-9842-0304df34c644.resgroup-10734</HierarchyObjRef>     <ObjectName>Production</ObjectName>   </HierarchyScopeItem> </HierarchyScopeCreateSpec>    Response:  201 Created    Response Body:  None |

1. To check if the restore scope has been successfully assigned or not, send the GET HTTP request to the /security/accounts/{ID}/scopes resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/security/accounts/129ccafb-d740-4a5a-b602-b02acfec1ec5/scopes    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EnterpriseAccountHierarchyScopes xmlns="http://www.veeam.com/ent/v1.0">   <EnterpriseAccountHierarchyScope Href="https://localhost:9398/api/security/accounts/9570aed1-7eff-4684-b77a-7735bdbe820d/scopes/2afe748f-bdc3-49d0-8837-20d2037a1176">     <Links>       <Link Rel="Delete" Type="EnterpriseAccountHierarchyScope" Href="https://localhost:9398/api/security/accounts/9570aed1-7eff-4684-b77a-7735bdbe820d/scopes/2afe748f-bdc3-49d0-8837-20d2037a1176" />     </Links>     <Name>Production</Name>     <HierarchyRootName>vcprod.tech.local</HierarchyRootName>     <Platform>VMware</Platform>     <HierarchyObjectType>ResourcePool</HierarchyObjectType>     <State>Unprocessed</State>   </EnterpriseAccountHierarchyScope>   ... </EnterpriseAccountHierarchyScopes> |

Result

The restore scope is assigned to the selected account having the Restore Operators role.

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
