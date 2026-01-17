---
title: "DELETE /security/accounts/{ID}/roles/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/delete_security_accounts_id_roles_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Removes the Veeam Backup Enterprise Manager security role from the account having the specified ID.

|  |
| --- |
| Note |
| The DELETE method is used to remove a specific security role from the list of roles assigned to the specific account. You cannot remove the last role from the account. |

Request

To remove a security role from the account having the specified ID, send the DELETE HTTP request to the /security/accounts/{ID}/roles/{ID} resource.

HTTP Request

|  |
| --- |
| DELETE https://<Enterprise-Manager>:9398/api/security/accounts/{ID}/roles/{ID} |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 204 No Content.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

None.

Example

The example below removes the File Restore Operator role from the account having ID f7d81d38-a457-4ee7-9294-a9123f8e4e99:

|  |
| --- |
| Request:  DELETE https://localhost:9398/api/security/accounts/f7d81d38-a457-4ee7-9294-a9123f8e4e99/roles/f84a8b62-49b8-4d0c-b25b-92321b52bab6    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  204 No Content    Response Body:  None |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
