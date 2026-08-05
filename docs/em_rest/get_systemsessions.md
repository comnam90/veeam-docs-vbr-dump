---
title: "GET /systemSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_systemsessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /systemSessions


Returns a resource representation of a collection of all system sessions of Veeam Backup Enterprise Manager. Note, the request only returns the sessions that has been created for the last 30 days.

Request

To get a list of all system sessions, send the GET HTTP request to the /systemSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/systemSessions |

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

In the response body, the REST API returns a representation of the /systemSessions resource collection.

Example

The example below returns a list of sessions for backup jobs on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/systemSessions  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <SystemSessions xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <Sessions Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25?format=Entity" Type="SystemSession" Name="Collect Job @2025-01-27 17:05:52.069837" UID="urn:veeam:SystemSession:00057ade-8f1a-4b54-a265-391441981e25">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25" Name="Collect Job @2025-01-27 17:05:52.069837" Type="BackupJobSessionReference" Rel="Alternate"/>       <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25/events" Name="Events" Type="SystemSessionEvents" Rel="Down"/>     </Links>     <SessionType>CollectJob</SessionType>     <CreationTimeUTC>2025-01-27T17:05:52.069837Z</CreationTimeUTC>     <EndTimeUTC>2025-01-27T17:06:10.491337Z</EndTimeUTC>     <State>CompletedSuccessfully</State>     <Result>       <Result>CompletedSuccessfully</Result>       <Message/>       <IsCanceled>false</IsCanceled>     </Result>   </Sessions>   <Sessions Href="https://enterprise04.tech.local:9398/api/systemSessions/00463c10-8196-4389-bd6b-8681c662e499?format=Entity" Type="SystemSession" Name="Catalog Replication Job @2025-01-30 16:38:54.377016" UID="urn:veeam:SystemSession:00463c10-8196-4389-bd6b-8681c662e499">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00463c10-8196-4389-bd6b-8681c662e499" Name="Catalog Replication Job @2025-01-30 16:38:54.377016" Type="BackupJobSessionReference" Rel="Alternate"/>       <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00463c10-8196-4389-bd6b-8681c662e499/events" Name="Events" Type="SystemSessionEvents" Rel="Down"/>     </Links>     <SessionType>CatalogReplicationJob</SessionType>     <CreationTimeUTC>2025-01-30T16:38:54.377016Z</CreationTimeUTC>     <EndTimeUTC>2025-01-30T16:39:08.988371Z</EndTimeUTC>     <State>CompletedSuccessfully</State>     <Result>       <Result>CompletedSuccessfully</Result>       <Message/>       <IsCanceled>false</IsCanceled>     </Result>   </Sessions> </SystemSessions> |

Page updated 2026-07-28

