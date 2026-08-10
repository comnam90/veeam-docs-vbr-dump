---
title: "GET /cdpReplicaSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdpreplicasessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cdpReplicaSessions


Returns a collection of all CDP replication sessions performed on all backup servers connected to Veeam Backup Enterprise Manager. Note, the request only returns the sessions that has been created for the last 30 days.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of CDP replication sessions, send the [GET /query?type=CdpReplicaSession](get_query_cdpreplicasession.md) request. |

Request

To get a collection of all CDP replication sessions, send the GET HTTP request to the /cdpReplicaSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpReplicaSessions |

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

In the response body, the REST API returns a representation of the /cdpReplicaSessions resource collection.

Example

The example below returns a collection of all CDP replication sessions performed on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpReplicaSessions  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" UID="urn:veeam:CdpReplicaSession:6b872a71-51e8-437a-8d45-5c6494b92f3f">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/145f3365-6ec0-44e9-9538-8c8c34ebdcce" Name="CDP Policy 1" />       <Link Rel="Alternate" Type="CdpReplicaSession" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f?format=Entity" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Down" Type="CdpReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f/cdpReplicaTaskSessions" />     </Links>   </Ref>   <Ref Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/40fa1841-227c-4b07-aeca-5d84e6816c8b" Name="CDP Policy 1@2025-02-11 17:12:45" UID="urn:veeam:CdpReplicaSession:40fa1841-227c-4b07-aeca-5d84e6816c8b">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/145f3365-6ec0-44e9-9538-8c8c34ebdcce" Name="CDP Policy 1" />       <Link Rel="Alternate" Type="CdpReplicaSession" Href="https://localhost:9398/api/cdpReplicaSessions/40fa1841-227c-4b07-aeca-5d84e6816c8b?format=Entity" Name="CDP Policy 1@2025-02-11 17:12:45" />       <Link Rel="Down" Type="CdpReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/cdpReplicaSessions/40fa1841-227c-4b07-aeca-5d84e6816c8b/cdpReplicaTaskSessions" />     </Links>   </Ref>   <Ref Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8" Name="CDP Policy 2@2025-02-11 17:13:47" UID="urn:veeam:CdpReplicaSession:f351a7b1-33d5-4bc7-9095-8892edc9e9c8">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/a3f2bc1b-b9d2-4c07-b15e-eefad1ba8701" Name="CDP Policy 2" />       <Link Rel="Alternate" Type="CdpReplicaSession" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8?format=Entity" Name="CDP Policy 2@2025-02-11 17:13:47" />       <Link Rel="Down" Type="CdpReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/cdpReplicaSessions/f351a7b1-33d5-4bc7-9095-8892edc9e9c8/cdpReplicaTaskSessions" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-28

