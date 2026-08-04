---
title: "GET /nas/jobs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_nas_jobs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /nas/jobs


Returns a resource representation of a collection of file share backup jobs created on all backup servers that are connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of file share backup jobs, send the [GET /query?type=NasJob](get_query_nasjob.md) request. |

Request

To get a list of file share backup jobs created on all backup servers connected to Veeam Backup Enterprise Manager, send the GET HTTP request to the /nas/jobs resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/nas/jobs |

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

In the response body, the REST API returns a representation of the /nas/jobs resource collection.

Example

The example below returns a list of all file share backup jobs created on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/nas/jobs  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <Ref UID="urn:veeam:NasJob:d6b01759-40f0-43ee-940e-496bdd13973c" Name="NFS Share Backup" Href="https://srv12.tech.local:9398/api/nas/jobs/d6b01759-40f0-43ee-940e-496bdd13973c" Type="NasJobReference">     <Links>       <Link Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://srv12.tech.local:9398/api/nas/jobs/d6b01759-40f0-43ee-940e-496bdd13973c?format=Entity" Name="NFS Share Backup" Type="Job" Rel="Alternate"/>       <Link Href="https://srv12.tech.local:9398/api/nas/jobs/d6b01759-40f0-43ee-940e-496bdd13973c/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:NasJob:93dfbb3e-f420-45cf-addc-4ee9297113f2" Name="Shared Files Backup" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2" Type="NasJobReference">     <Links>       <Link Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2?format=Entity" Name="Shared Files Backup" Type="Job" Rel="Alternate"/>       <Link Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

