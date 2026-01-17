---
title: "GET /query?type=AgentBackupJob"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_agentbackupjob.html"
last_updated: "9/1/2023"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of Veeam Agent backup jobs configured in Veeam Backup & Replication on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/agents/jobs](agents_jobs.md).

Request

To get a list of Veeam Agent backup jobs, send the GET HTTP request to the query with the type parameter set to AgentBackupJob.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=AgentBackupJob |

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
| UID | UidType | UID of the Veeam Agent backup job, for example: urn:veeam:Job:da736815-4fea-4c8e-b0e1-5ecdbca1c512. |
| Name | String | Name of the Veeam Agent backup job, for example: Linux job. |
| Description | String | Description of the Veeam Agent backup job. |
| JobType | String | Defines Veeam Agent backup job type. Possible value: AgentBackup. |
| Platform | String | Platform for which the job is created. Possible values:   * AgentForLinux * AgentForWindows |
| ScheduleConfigured | Boolean | Defines whether scheduling options are specified for the job. Possible values:   * True * False |
| ScheduleEnabled | Boolean | Defines whether schedule is enabled for the job. Possible values:   * True * False |
| BackupServerUid | UidType | UID of the backup server parent to the Veeam Agent backup job resource, for example: urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563. |
| BackupServerName | String | Name of the backup server parent to the Veeam Agent backup job resource. |

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

In the response body, the REST API returns a representation of the /agents/jobs resource collection.

Example

The example below returns an entity resource representation of a collection of Agent backup jobs that process Windows VMs.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=AgentBackupJob&format=Entities&filter=Platform==AgentForWindows    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 9/1/2023

Page content applies to build 13.0.1.1071
