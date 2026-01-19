---
title: "DELETE /backupServers/{ID}/credentials/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/delete_backupservers_id_creds_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# DELETE /backupServers/{ID}/credentials/{ID}


Deletes a credentials record having the specified ID from the backup server with the specified ID.

|  |
| --- |
| Note |
| You cannot delete credentials that are currently being used by any backup infrastructure component. |

Request

To remove a credentials record from the backup server, send the DELETE HTTP request to the /backupServers/{ID}/credentials/{ID} resource.

HTTP Request

|  |
| --- |
| DELETE https://<Enterprise-Manager>:9398/api/backupServers/{ID}/credentials/{ID} |

Request Headers

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

The example below removes a credentials record having ID c473b8df-4499-41b8-ba6b-7f76def6fea1 on the backup server with ID f62624c1-8462-4747-8bd4-d686f99b0540.

|  |
| --- |
| Request:  DELETE https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540/credentials/c473b8df-4499-41b8-ba6b-7f76def6fea1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  204 No Content |


