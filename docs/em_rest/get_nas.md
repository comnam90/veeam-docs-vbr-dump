---
title: "GET /nas"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_nas.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /nas


Returns a set of links to NAS backup resources.

Request

To get a list of NAS backup resources, send the GET HTTP request to the /nas resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/nas |

Request Header

The request contains the following headers:

Request Header

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

In the response body, the REST API returns a representation of the /nas resource.

Example

The example below returns a resource representation of the /nas resource.

|  |
| --- |
| Request:  GET https://localhost:9398/api/nas  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <NASService xmlns="http://www.veeam.com/ent/v1.0">   <Links>     <Link Rel="Down" Type="JobReferenceList" Href="https://srv12.tech.local:9398/api/nas/jobs" />     <Link Rel="Down" Type="FileServerReferenceList" Href="https://srv12.tech.local:9398/api/nas/fileServers" />     <Link Rel="Down" Type="BackupJobSessionReferenceList" Href="https://srv12.tech.local:9398/api/nas/backupSessions" />     <Link Rel="Down" Type="JobList" Href="https://srv12.tech.local:9398/api/nas/jobs?format=Entity" />     <Link Rel="Down" Type="FileServerList" Href="https://srv12.tech.local:9398/api/nas/fileServers?format=Entity" />     <Link Rel="Down" Type="BackupJobSessionList" Href="https://srv12.tech.local:9398/api/nas/backupSessions?format=Entity" />   </Links> </NASService> |

Page updated 2026-07-29

