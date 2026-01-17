---
title: "DELETE /security/accounts /{ID}/scopes/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/delete_security_accounts_id_scopes_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# DELETE /security/accounts /{ID}/scopes/{ID}


Removes a restore scope having the specified ID from the account having the specified ID. The account is added to Veeam Backup Enterprise Manager and is assigned a specific security role.

Request

To remove a restore scope from the account having the specified ID, send the DELETE HTTP request to the /security/accounts/{ID}/scopes/{ID} resource.

HTTP Request

|  |
| --- |
| DELETE https://<Enterprise-Manager>:9398/api/security/accounts/{ID}/scopes/{ID} |

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

The example below removes a restore scope having ID 75316e14-c742-4e7e-b594-ee532ae50fe9 for the account having ID 448744d7-d5fd-4f8a-83d2-c06e4ab796b6:

|  |
| --- |
| Request:  DELETE https://localhost:9398/api/security/accounts/448744d7-d5fd-4f8a-83d2-c06e4ab796b6/scopes/75316e14-c742-4e7e-b594-ee532ae50fe9    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  204 No Content    Response Body:  None |


