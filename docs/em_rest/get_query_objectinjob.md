---
title: "GET /query?type=ObjectInJob"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_objectinjob.html"
last_updated: "9/1/2023"
product_version: "13.0.1.1071"
---

# GET /query?type=ObjectInJob


Returns a list of VMs and VM containers processed by jobs. For details, see [/jobs/{ID}/includes](jobs_id_includes.md).

Request

To get a list of all VMs and VM containers processed by jobs, send the GET HTTP request to the query with the type parameter set to ObjectInJob.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=ObjectInJob |

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
| UID | String | ID of the VM or VM container processed by the job, for example: e310aa12-eff2-41f4-97c8-631b677fc17f. |
| Name | String | Name of the VM or VM container processed by the job, for example: DC-SRV. |
| JobUid | UidType | UID of the backup or replication job parent to the VM or VM container resource, for example: urn:veeam:Job:da736815-4fea-4c8e-b0e1-5ecdbca1c512. |
| JobName | String | Name of the backup or replication job parent to the VM or VM container resource, for example: DC Backup. |
| BackupServerUid | UidType | UID of the backup server to which the hierarchy root parent for the VM or VM container resource has been added, for example: urn:veeam:BackupServer:15942270-fb56-4dcc-96e9-5f80e4725a15. |
| BackupServerName | String | Name of the backup server to which the hierarchy root parent for the VM or VM container resource has been added, for example: BACKUPSERVER. |

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

In the response body, the REST API returns a representation of the /jobs/{ID}/includes resource collection.

Example

The example below returns an entity resource representation of a collection of objects that have the ubuntu88 name and that are processed by jobs created on the enterprise06.tech.local backup server. The results are ordered in the acceding order by the JobName parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=ObjectInJob&format=Entities&sortAsc=JobName&filter=BackupServerName=="enterprise06.tech.local";Name==ubuntu88    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


