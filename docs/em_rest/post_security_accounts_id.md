---
title: "POST /security/accounts/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_security_accounts_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Enables or disables the Restore scope: All virtual machines option specified for the account.

The account added to Veeam Backup Enterprise Manager can be assigned a permission to restore all VMs in the virtual infrastructure or only those VMs that belong to a specific level: for example, VMs that reside in a specific resource pool. By sending the POST HTTP request to the /security/accounts/{ID} URL, the client can toggle this setting to enabled or disabled.

Request

To enable or disable the Restore scope: All virtual machines option for the account, send the POST HTTP request to the /security/accounts/{ID} URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/security/accounts/{ID} |

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

The example below disables the Restore scope: All virtual machines option for the account having ID b1f22c43-645a-4a38-8d8e-560188b03f95:

|  |
| --- |
| Request:  POST https://localhost:9398/api/security/accounts/fd4befd6-70c6-4b2f-a068-d1d9a61905a3    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  204 No Content    Response Body:  None |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
