---
title: "GET /systemSessions/{ID}/events"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_systemsessions_id_events.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /systemSessions/{ID}/events


Returns a resource representation of a collection of all log events of a system session having the specified ID.

Request

To get a list of all log events of a system session, send the GET HTTP request to the /systemSessions/{ID}/events resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/systemSessions/{ID}/events |

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

In the response body, the REST API returns a representation of the /systemSessions/{ID}/events resource.

Example

The example below returns a list of log events of a system session with an ID 00057ade-8f1a-4b54-a265-391441981e25.

|  |
| --- |
| Request:  GET https://localhost:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25/events  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <SystemSessionEvents xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0" Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25/events" Type="SystemSessionEvents">   <Links>     <Link Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25?format=Entity" Name="Collect Job @2025-01-27 17:05:52.069837" Type="BackupJobSession" Rel="Up"/>   </Links>   <Events>     <CreationTimeUTC>2025-01-27T17:05:52.069837</CreationTimeUTC>     <Message>Starting data collection job...</Message>     <Order>1</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:05:52.101105</CreationTimeUTC>     <Message>Job successfully started.</Message>     <Order>2</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:05:52.101105</CreationTimeUTC>     <Message>Checking deleted backup servers removal</Message>     <Order>3</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:05:52.116682</CreationTimeUTC>     <Message>Preparing to collect data from enterprise05.tech.local</Message>     <Order>4</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:05:52.116682</CreationTimeUTC>     <Message>Retrieving data from enterprise05.tech.local...</Message>     <Order>5</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:06:10.30038</CreationTimeUTC>     <Message>Data collection from enterprise05.tech.local completed successfully.</Message>     <Order>6</Order>   </Events>   <Events>     <CreationTimeUTC>2025-01-27T17:06:10.488816</CreationTimeUTC>     <Message>Data collection job finished.</Message>     <Order>7</Order>   </Events> </SystemSessionEvents> |

Page updated 2026-07-29

