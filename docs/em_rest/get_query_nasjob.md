---
title: "GET /query?type=NasJob"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_nasjob.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# GET /query?type=NasJob


Returns a resource representation of a collection of file share backup jobs created on backup servers that are connected to Veeam Backup Enterprise Manager. For details, see [/nas/jobs](nas_jobs.md).

Request

To get a list of file share backup jobs, send the GET HTTP request to the query with the type parameter set to NasJob.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=NasJob |

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
| UID | UidType | UID of the file share backup job, for example: urn:veeam:NasJob:93dfbb3e-f420-45cf-addc-4ee9297113f2. |
| Name | String | Name of the file share backup job, for example: Shared Files Backup. |
| Description | String | Description of the file share backup job. |
| NextRun | DateTime | Date and time of the next job run. The parameter accepts only UTC-formatted DateTime values.  Note that this parameter can be used for scheduled jobs only. |
| ScheduleConfigured | Boolean | Defines whether scheduling options are specified for the job. Possible values:   * True * False |
| ScheduleEnabled | Boolean | Defines whether schedule is enabled for the job. Possible values:   * True * False |
| BackupServerUid | UidType | UID of the backup server parent to the file share backup job resource. |
| BackupServerName | String | Name of the backup server parent to the file share backup job resource. |

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

In the response body, the REST API returns a representation of the /nas/jobs resource collection.

Example

The example below returns an entity resource representation of a collection of file share backup jobs created on the backup server enterprise06.tech.local.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=NasJob&format=Entities&filter=BackupServerName=="enterprise06.tech.local"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


