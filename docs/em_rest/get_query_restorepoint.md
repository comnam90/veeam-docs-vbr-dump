---
title: "get_query_restorepoint"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_restorepoint.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a restore points collection for backups and replicas created on or imported to backup servers connected to Veeam Backup Enterprise Manager. For details, see [/restorePoints](restorepoints.md).

Request

To get a list of restore points, send the GET HTTP request to the query with the type parameter set to RestorePoint.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=RestorePoint |

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
| UID | UidType | UID of the restore point resource, for example: urn:veeam:RestorePoint:bf0542a7-baea-41fa-baec-12e76043d0e1 |
| Name | String | Name of the restore point, for example: Aug 26 2013 7:57AM. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| BackupUid | UidType | UID of the VM backup parent to the restore point resource. |
| BackupName | String | Name of the backup parent to the restore point resource. |
| BackupServerUid | UidType | UID of the backup server on which the restore point has been created. |
| BackupServerName | String | Name of the backup server on which the restore point has been created. |

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

In the response body, the REST API returns a representation of the /restorePoints resource collection.

Example

The example below returns an entity resource representation of a collection of restore points for the backup with name Backup Job 5. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=RestorePoint&format=Entities&sortAsc=name&filter=BackupName=="Backup Job 5"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
