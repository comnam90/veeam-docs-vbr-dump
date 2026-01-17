---
title: "GET /query?type=FileServer"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_fileserver.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of file shares added on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/nas/fileServers](nas_fileservers.md).

Request

To get a list of file shares, send the GET HTTP request to the query with the type parameter set to FileServer.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=FileServer |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

| Parameter | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the file share, for example: urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c. |
| Name | String | Name of the file share, for example: \\srv12\share. |
| BackupServerUid | UidType | UID of the backup server parent to the file share resource. |
| BackupServerName | String | Name of the backup server parent to the file share resource. |

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

In the response body, the REST API returns a representation of the /nas/fileServers resource collection.

Example

The example below returns an entity resource representation of a collection of file shares added on the backup server with name enterprise06.tech.local. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=FileServer&format=Entities&sortAsc=name&filter=BackupServerName=="enterprise06.tech.local"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
