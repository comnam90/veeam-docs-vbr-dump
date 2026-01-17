---
title: "POST /security/accounts/{ID}/roles"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_security_accounts_id_roles.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# POST /security/accounts/{ID}/roles


Assigns a Veeam Backup Enterprise Manager security role to the specified account.For details on security roles, see [Security Roles](security_roles_concept.md).

Request

To assign a security role to an account having the specified ID, send the POST HTTP request to the /security/accounts/{ID}/roles resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/security/accounts/{ID}/roles |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send the parameters for the role that should be assigned to the account. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| EnterpriseRoleUid | UidType | UID of the role that must be assigned to the account. To get a list of IDs for available roles, send the [GET HTTP request to the /security/roles resource](get_security_roles.md). | No | 1/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "EnterpriseRoleUid": "urn:veeam:EnterpriseRole:c11c0c38-ba8b-49c7-bf70-fc2058fff1e2"  } |

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

The example below assigns the VM Restore Operator role to the account having ID f7d81d38-a457-4ee7-9294-a9123f8e4e99:

|  |
| --- |
| Request:  POST https://localhost:9398/api/security/accounts/f7d81d38-a457-4ee7-9294-a9123f8e4e99/roles    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <EnterpriseAccountInRoleCreateSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <EnterpriseRoleUid>urn:veeam:EnterpriseRole:c11c0c38-ba8b-49c7-bf70-fc2058fff1e2</EnterpriseRoleUid> </EnterpriseAccountInRoleCreateSpec>    Response:  201 Created    Response Body:  None |


