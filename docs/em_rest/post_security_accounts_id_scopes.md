---
title: "POST /security/accounts/{ID}/scopes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_security_accounts_id_scopes.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# POST /security/accounts/{ID}/scopes


Assigns a restore scope to the account having the specified ID. The account is added to Veeam Backup Enterprise Manager and has a specific security role.

Request

To assign a restore scope to the account having the specified ID, send the POST HTTP request to the /security/accounts/{ID}/scopes resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/security/accounts/{ID}/scopes |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters of the restore scope. The restore scope is specified as a branch in the virtual infrastructure hierarchy. The client defines the upper node in the branch, and all child nodes of the defined node become accessible by the user.

For example, if you want to allow the user to restore data from all VMs in the VMs resource pool, send the parameters of the VMs resource pool node in the request body. As a result, Veeam Backup Enterprise Manager will allow the user to restore data from all VMs residing in the VMs resource pool.

The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| HierarchyObjRef | HierarchyObjRefType | Reference to the object in the virtual infrastructure hierarchy. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference.  To get a file share reference, use the [GET /nas/fileServers/{ID}](get_nas_fileservers_id.md) request. | Yes | 0/1 |
| ObjectName | String | Name of the object in the virtual infrastructure hierarchy, for example: VM01. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "HierarchyScopeItems": [     {       "HierarchyObjRef": "urn:VMware:Vm:a2b0c55d-829a-4efe-bd95-125ee77ba9dd.vm-7870",       "ObjectName": "VM01"     },     {       "HierarchyObjRef": "urn:NasBackup:FileServer:541178f4-5335-46cb-b7bc-8fbb4a944307.541178f4-5335-46cb-b7bc-8fbb4a944307",       "ObjectName": "\\\\enterprise05.tech.local\\SMB Share"     }   ]  } |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 202 Accepted.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

None.

Example

The example below assigns the restore scope to the account having ID fd4befd6-70c6-4b2f-a068-d1d9a61905a3. The restore scope includes only one VM: SQLSRV having MoRef vm-15309.

|  |
| --- |
| Request:  POST https://localhost:9398/api/security/accounts/fd4befd6-70c6-4b2f-a068-d1d9a61905a3/scopes    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <HierarchyScopeCreateSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <HierarchyScopeItem>     <HierarchyObjRef>urn:VMware:Vm:a2b0c55d-829a-4efe-bd95-125ee77ba9dd.vm-15309</HierarchyObjRef>     <ObjectName>SQLSRV</ObjectName>   </HierarchyScopeItem>   <HierarchyScopeItem>     <HierarchyObjRef>urn:NasBackup:FileServer:541178f4-5335-46cb-b7bc-8fbb4a944307.541178f4-5335-46cb-b7bc-8fbb4a944307</HierarchyObjRef>     <ObjectName>\\enterprise05.tech.local\SMB Share</ObjectName>    </HierarchyScopeItem> </HierarchyScopeCreateSpec>    Response:  201 Created    Response Body:  None |


