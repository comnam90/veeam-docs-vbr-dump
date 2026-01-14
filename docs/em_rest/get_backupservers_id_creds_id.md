---
title: "get_backupservers_id_creds_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupservers_id_creds_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a credentials record with the specified ID created on the backup server with the specified ID.

Request

To get a resource representation of the credentials record created on a specific backup server, send the GET HTTP request to the /backupServers/{ID}/credentials/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupServers/{ID}/credentials/{ID} |

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

A successfully completed operation returns response code 200 OK.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /backupServers/{ID}/credentials/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| Id | String | ID of the credentials record, for example: 3ff61155-ed3d-47c5-a07b-29c7ca0d36b9. |
| Username | String | User name of the credentials record, for example: BACKUPSERVER\Administrator. |
| Description | String | Description of the credentials record, for example: Administrator credentials. |
| Password | String | Password of the credentials record. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=Credentials](get_query_credentials.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the credentials have been created. |
| /backupServers/{ID}/credentials/{ID} | Edit | Alternate URL of the [PUT /backupServers/{ID}/credentials/{ID}](put_backupservers_id_creds_id.md) resource. |
| /backupServers/{ID}/credentials/{ID} | Delete | URL for the [DELETE /backupServers/{ID}/credentials/{ID}](delete_backupservers_id_creds_id.md) request. |

Example

The example below returns a credentials record having ID a45eb049-6f8d-49d4-9dba-4f1499f9d8d1 created on the backup server having ID 50a1b2fb-b90a-4e05-816f-e298eb2f995c.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/credentials/a45eb049-6f8d-49d4-9dba-4f1499f9d8d1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CredentialsInfo xmlns="http://www.veeam.com/ent/v1.0" Type="Credentials" Href="https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/credentials/a45eb049-6f8d-49d4-9dba-4f1499f9d8d1"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
