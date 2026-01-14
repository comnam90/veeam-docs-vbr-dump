---
title: "post_security_accounts"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_security_accounts.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Adds a user or group account having a specific security role to Veeam Backup Enterprise Manager.

Request

To add an account with a specific security role to Veeam Backup Enterprise Manager, send the POST HTTP request to the /security/accounts resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/security/accounts |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send the parameters for the account that should be added to Veeam Backup Enterprise Manager and the ID of the role that should be assigned to the account. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| AccountType | AccountTypeEnumeration | Type of account added to Veeam Backup Enterprise Manager. Possible values:   * User * Group * ExternalUser * ExternalGroup   Accounts of the ExternalUser and ExternalGroup type are created for users that will access Veeam Backup Enterprise Manager using a single sign-on service. For details, see the [SAML Authentication Support](https://helpcenter.veeam.com/docs/backup/em/em_saml.html?ver=120) section in the Veeam Backup Enterprise Manager Guide. | No | 1/1 |
| AccountName | String | Name of the account added to Veeam Backup Enterprise Manager:   * For the User or Group account, the name must be specified in the Domain\Name format, for example: TECH\william.fox. * For the ExternalUser account, the name must be specified in the Username@Suffix format, for example: william.fox@tech.com. * For the ExternalGroup account, the name can be a free-form string. | Yes | 1/1 |
| Roles | EnterpriseAccountInRoleCreateSpecListType | UID of the role assigned to the added account. To get a list of UIDs for available roles, send the GET HTTP request to the /security/roles resource. For details, see [GET /security/roles](get_security_roles.md). | No | 1/1 |
| AllowRestoreAllVms | Boolean | Defines whether the account must have permissions to restore all VMs or not. If this parameter is set to False, the client must provide the restore scope in the HierarchyScopeObjects element. | No | 1/1 |
| HierarchyScopeObjects | HierarchyScopeCreateSpecType | Restore scope assigned to the added account. For details, see [Hierarchy Scope Settings](post_security_accounts.md#hierarchy). | No | 0/1 |
| FlrSettings | FileRestoreSettingsInfoType | File-level restore restrictions assigned to the added account. For details, see [File-Level Restore Settings](post_security_accounts.md#flr). | No | 0/1 |
| SqlSettings | SqlRestoreSettingsSpecsType | SQL restore restrictions assigned to the added account. For details, see [SQL restore settings](#sql). | No | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "AccountType": "User",   "AccountName": "TECH\\william.fox",   "Roles": {     "EnterpriseRoles": [       {         "EnterpriseRoleUid": "urn:veeam:EnterpriseRole:f84a8b62-49b8-4d0c-b25b-92321b52bab6"       }     ]   },   "AllowRestoreAllVms": false,   "HierarchyScopeObjects": {     "HierarchyScopeItems": [       {         "HierarchyObjRef": "",         "ObjectName": ""       }     ]   }  } |

Hierarchy Scope Settings

You can define the following hierarchy scope settings for the added account:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| HierarchyObjRef | HierarchyObjRefType | Reference to the object in the virtual infrastructure hierarchy. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference.  To get a file share reference, use the [GET /nas/fileServers/{ID}](get_nas_fileservers_id.md) request. | Yes | 0/1 |
| ObjectName | String | Name of the object in the virtual infrastructure hierarchy, for example: VM01. | Yes | 0/1 |

Hierarchy scope settings are provided in the following format:

XML Representation

|  |
| --- |
| <HierarchyScopeObjects>   <HierarchyScopeItem>     <HierarchyObjRef>urn:VMware:Vm:a2b0c55d-829a-4efe-bd95-125ee77ba9dd.vm-7870</HierarchyObjRef>     <ObjectName>VM01</ObjectName>   </HierarchyScopeItem> </HierarchyScopeObjects> |

JSON Representation

|  |
| --- |
| "HierarchyScopeObjects": {   "HierarchyScopeItem": {     "HierarchyObjRef": "urn:VMware:Vm:a2b0c55d-829a-4efe-bd95-125ee77ba9dd.vm-7870",     "ObjectName": "VM01"   }  } |

File-Level Restore Settings

You can define the following file-level restore settings for the added account:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| FlrInplaceOnly | Boolean | Defines whether the account must have permissions to restore only files with specific filename extensions or not. If this parameter is set to True, the client must provide filename extensions for files that are permitted for restore in the FlrExtentionRestrictions element. | Yes | 1/1 |
| FlrExtentionRestrictions | String | Filename extensions for files that are permitted for restore separated by comma, for example: doc,pptx,pdf. | Yes | 0/1 |

|  |
| --- |
| Note |
| You cannot edit file-level restore settings for the created account. To change file-level restore settings for the account, remove the account and create the account with necessary file-level restore settings. |

File-level restore settings are provided in the following format:

XML Representation

|  |
| --- |
| <FlrSettings>     <FlrInplaceOnly>true</FlrInplaceOnly>     <FlrExtentionRestrictions>doc,pptx</FlrExtentionRestrictions> </FlrSettings> |

JSON Representation

|  |
| --- |
| "FlrSettings": {   "FlrInplaceOnly": "true",    "FlrExtentionRestrictions": "doc,pptx"  } |

SQL Restore Settings

You can define the following SQL restore settings for the added account:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| DenyInPlaceRestore | Boolean | Defines whether you want to prevent user account from overriding production databases at restore. | Yes | 1/1 |

|  |
| --- |
| Note |
| You cannot edit SQL restore settings for the created account. To change SQL restore settings for the account, remove the account and create the account with necessary SQL restore settings. |

SQL restore settings are provided in the following format:

XML Representation

|  |
| --- |
| <SqlSettings>     <DenyInPlaceRestore>True</DenyInPlaceRestore> </SqlSettings> |

JSON Representation

|  |
| --- |
| "SqlSettings": {"DenyInPlaceRestore": "True"} |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 201 Created.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

None.

Example

Example 1

The example below adds a Restore Operator user account:

|  |
| --- |
| Request:  POST https://localhost:9398/api/security/accounts    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <EnterpriseAccountCreateSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <AccountType>User</AccountType>   <AccountName>VEEAM\User</AccountName>   <Roles>     <EnterpriseRole>       <EnterpriseRoleUid>urn:veeam:EnterpriseRole:f84a8b62-49b8-4d0c-b25b-92321b52bab6</EnterpriseRoleUid>     </EnterpriseRole>    </Roles>   <AllowRestoreAllVms>true</AllowRestoreAllVms> </EnterpriseAccountCreateSpec>    Response:  201 Created    Response Body:  None |

Example 2

The example below adds a Restore Operator user account that can restore a file share.

|  |
| --- |
| Request:  POST https://localhost:9398/api/security/accounts    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <EnterpriseAccountCreateSpec xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <AccountType>User</AccountType>   <AccountName>TECH\mary.smith</AccountName>   <Roles>     <EnterpriseRole>       <EnterpriseRoleUid>urn:veeam:EnterpriseRole:f84a8b62-49b8-4d0c-b25b-92321b52bab6</EnterpriseRoleUid>     </EnterpriseRole>   </Roles>   <AllowRestoreAllVms>false</AllowRestoreAllVms>   <HierarchyScopeObjects>      <HierarchyScopeItem>       <HierarchyObjRef>urn:NasBackup:FileServer:541178f4-5335-46cb-b7bc-8fbb4a944307.541178f4-5335-46cb-b7bc-8fbb4a944307</HierarchyObjRef>       <ObjectName>\\enterprise05.tech.local\SMB Share</ObjectName>      </HierarchyScopeItem>   </HierarchyScopeObjects> </EnterpriseAccountCreateSpec>      Response:  201 Created    Response Body:  None |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
