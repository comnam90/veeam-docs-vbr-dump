---
title: "GET /replicaSessions/{ID}/replicaTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_replicasessions_id_replicatasksessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /replicaSessions/{ID}/replicaTaskSessions


Returns a collection of replication task sessions of the replication session that has the specified ID. Note, the request only returns the sessions that has been created for the last 30 days.

Request

To get a collection of replication task sessions of the replication session, send the GET HTTP request to the /replicaSessions/{ID}/replicaTaskSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/replicaSessions/{ID}/replicaTaskSessions |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
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

Response Headers

| Header | Description |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /replicaSessions/{ID}/replicaTaskSessions resource collection.

Example

The example below returns a collection of replication task sessions of the replication session that has ID f5bf1a4b-c229-452e-a4e8-0354e1752b4e.

|  |
| --- |
| Request:  GET https://localhost:9398/api/replicaSessions/f5bf1a4b-c229-452e-a4e8-0354e1752b4e/replicaTaskSessions?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <ReplicaTaskSessions xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">     <ReplicaTaskSession Href="https://enterprise06.tech.local:9398/api/replicaTaskSessions/c20dae03-4f75-4191-ae81-862f4b7988ca?format=Entity" Type="ReplicaTaskSession" Name="ubuntu88@2025-11-03 21:00:26" UID="urn:veeam:ReplicaTaskSession:c20dae03-4f75-4191-ae81-862f4b7988ca" VmDisplayName="ubuntu88">         <Links>             <Link Href="https://enterprise06.tech.local:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" Type="BackupServerReference" Rel="Up" />             <Link Href="https://enterprise06.tech.local:9398/api/replicaSessions/f5bf1a4b-c229-452e-a4e8-0354e1752b4e" Name="Replication Job 1@2025-11-03 21:00:11" Type="ReplicaJobSessionReference" Rel="Up" />             <Link Href="https://enterprise06.tech.local:9398/api/replicaTaskSessions/c20dae03-4f75-4191-ae81-862f4b7988ca" Name="ubuntu88@2025-11-03 21:00:26" Type="ReplicaTaskSessionReference" Rel="Alternate" />         </Links>         <JobSessionUid>urn:veeam:ReplicaJobSession:f5bf1a4b-c229-452e-a4e8-0354e1752b4e</JobSessionUid>         <CreationTimeUTC>2025-11-03T21:00:26.19Z</CreationTimeUTC>         <EndTimeUTC>2025-11-03T21:03:16.73Z</EndTimeUTC>         <State>Completed</State>         <Result>Success</Result>         <Reason />         <TotalSize>17179869184</TotalSize>     </ReplicaTaskSession> </ReplicaTaskSessions> |

Page updated 2026-07-28

